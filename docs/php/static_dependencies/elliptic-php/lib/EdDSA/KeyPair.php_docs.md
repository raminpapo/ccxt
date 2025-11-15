# Documentation: php/static_dependencies/elliptic-php/lib/EdDSA/KeyPair.php

## File Metadata

- **Path**: `php/static_dependencies/elliptic-php/lib/EdDSA/KeyPair.php`
- **Size**: 3,641 bytes
- **Lines**: 127
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace Elliptic\EdDSA;

use Elliptic\Utils;

class KeyPair {
    public $eddsa;
    public $_pubBytes;
/**
* @param {\Elliptic\EdDSA} eddsa - instance
* @param {Object} params - public/private key parameters
*
* @param {Array<Byte>} [params.secret] - secret seed bytes
* @param {Point} [params.pub] - public key point (aka `A` in eddsa terms)
* @param {Array<Byte>} [params.pub] - public key point encoded as bytes
*
*/
    function __construct($eddsa, $params) {
        $this->eddsa = $eddsa;
        $this->_secret = isset($params["secret"]) ? Utils::parseBytes($params["secret"]) : null;
        if (!isset($params["pub"])) {
            $this->_pub = null;
            $this->_pubBytes = null;
            return;
        }
        if ($eddsa->isPoint($params["pub"]))
            $this->_pub = $params["pub"];
        else
            $this->_pubBytes = Utils::parseBytes($params["pub"]);
    }

    public static function fromPublic($eddsa, $pub) {
        if ($pub instanceof KeyPair)
            return $pub;
        return new KeyPair($eddsa, [ "pub" => $pub ]);
    }

    public static function fromSecret($eddsa, $secret) {
        if ($secret instanceof KeyPair)
            return $secret;
        return new KeyPair($eddsa, [ "secret" => $secret ]);
    }

    private $_secret;
    public function secret() {
        return $this->_secret;
    }

    public function pubBytes() {
        if (!$this->_pubBytes) 
            $this->_pubBytes = $this->eddsa->encodePoint($this->pub());
        return $this->_pubBytes;
    }

    private $_pub;
    public function pub() {
        if (!$this->_pub) {
            if ($this->_pubBytes)
                $this->_pub = $this->eddsa->decodePoint($this->_pubBytes);
            else
                $this->_pub = $this->eddsa->g->mul($this->priv());
        }
        return $this->_pub;
    }

    private $_privBytes;
    public function privBytes() {
        if (!$this->_privBytes) {
            $eddsa = $this->eddsa;
            $hash = $this->hash();
            $lastIx = $eddsa->encodingLength - 1;

            $a = array_slice($hash, 0, $eddsa->encodingLength);
            $a[0] &= 248;
            $a[$lastIx] &= 127;
            $a[$lastIx] |= 64;
            $this->_privBytes = $a;
        }
        return $this->_privBytes;
    }

    private $_priv;
    public function priv() {
        if (!$this->_priv) {
            $this->_priv = $this->eddsa->decodeInt($this->privBytes());
        }
        return $this->_priv;
    }

    private $_hash;
    public function hash() {
        if (!$this->_hash) {
            // TODO: !!!
            $hash = hash_init('sha512');
            hash_update($hash, Utils::toBin($this->secret()));
            $this->_hash = Utils::toArray( hash_final($hash), 'hex' );
        }
        return $this->_hash;
    }

    private $_messagePrefix;
    public function messagePrefix() {
        if (!$this->_messagePrefix) {
            $this->_messagePrefix = array_slice($this->hash(), $this->eddsa->encodingLength);
        }
        return $this->_messagePrefix;
    }

    public function sign($message) {
        assert($this->_secret); //, 'KeyPair can only verify');
        return $this->eddsa->sign($message, $this);
    }

    public function verify($message, $sig) {
        return $this->eddsa->verify($message, $sig, $this);
    }

    public function getSecret($enc = false) {
        assert($this->_secret); //, 'KeyPair is public only');
        return Utils::encode($this->secret(), $enc);
    }

    public function getPublic($enc = false) {
        return Utils::encode($this->pubBytes(), $enc);
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/elliptic-php/lib/EdDSA/KeyPair.php`.

**Classes defined**: KeyPair

**Functions defined**: hash, privBytes, fromPublic, priv, __construct, pubBytes, secret, fromSecret, messagePrefix, pub

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 127
- Code lines: 109
- Comment lines: 10
- Blank lines: 8

### Main Components

**Classes** (1):
- `KeyPair`

**Functions** (14):
- `__construct()`
- `fromPublic()`
- `fromSecret()`
- `getPublic()`
- `getSecret()`
- `hash()`
- `messagePrefix()`
- `priv()`
- `privBytes()`
- `pub()`
- `pubBytes()`
- `secret()`
- `sign()`
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
php php/static_dependencies/elliptic-php/lib/EdDSA/KeyPair.php
```

