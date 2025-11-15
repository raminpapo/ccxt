# Documentation: php/static_dependencies/elliptic-php/lib/EC/KeyPair.php

## File Metadata

- **Path**: `php/static_dependencies/elliptic-php/lib/EC/KeyPair.php`
- **Size**: 3,550 bytes
- **Lines**: 142
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Elliptic\EC;

use BN\BN;

class KeyPair
{
    public $ec;
    public $pub;
    public $priv;

    function __construct($ec, $options)
    {
        $this->ec = $ec;

        $this->priv = null;
        $this->pub = null;

        if( isset($options["priv"]) )
            $this->_importPrivate($options["priv"], $options["privEnc"]);

        if( isset($options["pub"]) )
            $this->_importPublic($options["pub"], $options["pubEnc"]);
    }

    public static function fromPublic($ec, $pub, $enc)
    {
        if( $pub instanceof KeyPair )
            return $pub;

        return new KeyPair($ec, array(
            "pub" => $pub,
            "pubEnc" => $enc
        ));
    }

    public static function fromPrivate($ec, $priv, $enc)
    {
        if( $priv instanceof KeyPair )
            return $priv;

        return new KeyPair($ec, array(
            "priv" => $priv,
            "privEnc" => $enc
        ));
    }

    public function validate()
    {
        $pub = $this->getPublic();

        if( $pub->isInfinity() )
            return array( "result" => false, "reason" => "Invalid public key" );

        if( !$pub->validate() )
            return array( "result" => false, "reason" => "Public key is not a point" );

        if( !$pub->mul($this->ec->curve->n)->isInfinity() )
            return array( "result" => false, "reason" => "Public key * N != O" );

        return array( "result" => true, "reason" => null );
    }

    public function getPublic($compact = false, $enc = "")
    {
        //compact is optional argument
        if( is_string($compact) )
        {
            $enc = $compact;
            $compact = false;
        }

        if( $this->pub === null )
            $this->pub = $this->ec->g->mul($this->priv);

        if( !$enc )
            return $this->pub;

        return $this->pub->encode($enc, $compact);
    }

    public function getPrivate($enc = false)
    {
        if( $enc === "hex" )
            return $this->priv->toString(16, 2);

        return $this->priv;
    }

    private function _importPrivate($key, $enc)
    {
        $this->priv = new BN($key, (isset($enc) && $enc) ? $enc : 16);

        // Ensure that the priv won't be bigger than n, otherwise we may fail
        // in fixed multiplication method
        $this->priv = $this->priv->umod($this->ec->curve->n);
    }

    private function _importPublic($key, $enc)
    {
        $x = $y = null;
        if ( is_object($key) ) {
            $x = $key->x;
            $y = $key->y;
        } elseif ( is_array($key) ) {
            $x = isset($key["x"]) ? $key["x"] : null;
            $y = isset($key["y"]) ? $key["y"] : null;
        }

        if( $x != null || $y != null )
            $this->pub = $this->ec->curve->point($x, $y);
        else
            $this->pub = $this->ec->curve->decodePoint($key, $enc);
    }

    //ECDH
    public function derive($pub) {
        return $pub->mul($this->priv)->getX();
    }

    //ECDSA
    public function sign($msg, $enc = false, $options = false) {
        return $this->ec->sign($msg, $this, $enc, $options);
    }

    public function verify($msg, $signature) {
        return $this->ec->verify($msg, $signature, $this);
    }

    public function inspect() {
        return "<Key priv: " . (isset($this->priv) ? $this->priv->toString(16, 2) : "") .
            " pub: " . (isset($this->pub) ? $this->pub->inspect() : "") . ">";
    }

    public function __debugInfo() {
        return ["priv" => $this->priv, "pub" => $this->pub];
    }
}

?>

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/elliptic-php/lib/EC/KeyPair.php`.

**Classes defined**: KeyPair

**Functions defined**: fromPrivate, fromPublic, derive, sign, _importPublic, __construct, validate, getPrivate, _importPrivate, getPublic



## Detailed Walkthrough

### Code Structure

- Total lines: 142
- Code lines: 104
- Comment lines: 5
- Blank lines: 33

### Main Components

**Classes** (1):
- `KeyPair`

**Functions** (13):
- `__construct()`
- `__debugInfo()`
- `_importPrivate()`
- `_importPublic()`
- `derive()`
- `fromPrivate()`
- `fromPublic()`
- `getPrivate()`
- `getPublic()`
- `inspect()`
- `sign()`
- `validate()`
- `verify()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/elliptic-php/lib/EC/KeyPair.php
```

