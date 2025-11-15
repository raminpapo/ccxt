# Documentation: php/static_dependencies/elliptic-php/lib/EdDSA/Signature.php

## File Metadata

- **Path**: `php/static_dependencies/elliptic-php/lib/EdDSA/Signature.php`
- **Size**: 2,301 bytes
- **Lines**: 83
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php
namespace Elliptic\EdDSA;

use Elliptic\Utils;
use BN\BN;

class Signature {
    
    public $eddsa;
    
    /**
     * @param {EdDSA} eddsa - eddsa instance
     * @param {Array<Bytes>|Object} sig -
     * @param {Array<Bytes>|Point} [sig.R] - R point as Point or bytes
     * @param {Array<Bytes>|bn} [sig.S] - S scalar as bn or bytes
     * @param {Array<Bytes>} [sig.Rencoded] - R point encoded
     * @param {Array<Bytes>} [sig.Sencoded] - S scalar encoded
     */
    function __construct($eddsa, $sig) {
        $this->eddsa = $eddsa;

        if (is_string($sig))
            $sig = Utils::parseBytes($sig);

        if (is_array($sig) && !isset($sig["R"])) {
            $sig = [
                "R" => array_slice($sig, 0, $eddsa->encodingLength),
                "S" => array_slice($sig, $eddsa->encodingLength)
            ];
        }

        assert($sig["R"] && $sig["S"]); //, 'Signature without R or S');

        if ($eddsa->isPoint($sig["R"]))
            $this->_R = $sig["R"];
        if ($sig["S"] instanceof BN)
            $this->_S = $sig["S"];

        $this->_Rencoded = is_array($sig["R"]) ? $sig["R"] : (isset($sig["Rencoded"]) ?$sig["Rencoded"] : null);
        $this->_Sencoded = is_array($sig["S"]) ? $sig["S"] : (isset($sig["Sencoded"]) ?$sig["Sencoded"] : null);
    }

    private $_S;
    public function S() {
        if (!$this->_S) {
            $this->_S = $this->eddsa->decodeInt($this->Sencoded());
        }
        return $this->_S;
    }

    private $_R;
    public function R() {
        if (!$this->_R) {
            $this->_R = $this->eddsa->decodePoint($this->Rencoded());
        }
        return $this->_R;
    }

    private $_Rencoded;
    public function Rencoded() {
        if (!$this->_Rencoded) {
            $this->_Rencoded = $this->eddsa->encodePoint($this->R());
        }
        return $this->_Rencoded;
    }

    private $_Sencoded;
    public function Sencoded() {
        if (!$this->_Sencoded) {
            $this->_Sencoded = $this->eddsa->encodeInt($this->S());
        }
        return $this->_Sencoded;
    }

    public function toBytes() {
        return array_merge($this->Rencoded(), $this->Sencoded());
    }

    public function toHex() {
        return strtoupper(Utils::encode($this->toBytes(), 'hex'));
    }
}

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/elliptic-php/lib/EdDSA/Signature.php`.

**Classes defined**: Signature

**Functions defined**: Sencoded, R, Rencoded, toBytes, __construct, toHex, S

**Documentation**: Contains inline documentation/comments.



## Detailed Walkthrough

### Code Structure

- Total lines: 83
- Code lines: 67
- Comment lines: 8
- Blank lines: 8

### Main Components

**Classes** (1):
- `Signature`

**Functions** (7):
- `R()`
- `Rencoded()`
- `S()`
- `Sencoded()`
- `__construct()`
- `toBytes()`
- `toHex()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/elliptic-php/lib/EdDSA/Signature.php
```

