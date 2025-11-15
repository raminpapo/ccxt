# Documentation: php/static_dependencies/elliptic-php/lib/Curve/BaseCurve/Point.php

## File Metadata

- **Path**: `php/static_dependencies/elliptic-php/lib/Curve/BaseCurve/Point.php`
- **Size**: 2,869 bytes
- **Lines**: 121
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Elliptic\Curve\BaseCurve;

use Elliptic\Utils;

abstract class Point
{
    public $curve;
    public $type;
    public $precomputed;

    function __construct($curve, $type)
    {
        $this->curve = $curve;
        $this->type = $type;
        $this->precomputed = null;
    }

    abstract public function eq($other);

    public function validate() {
        return $this->curve->validate($this);
    }

    public function encodeCompressed($enc) {
        return $this->encode($enc, true);
    }

    public function encode($enc, $compact = false) {
        return Utils::encode($this->_encode($compact), $enc);
    }

    protected function _encode($compact)
    {
        $len = $this->curve->p->byteLength();
        $x = $this->getX()->toArray("be", $len);

        if( $compact )
        {
            array_unshift($x, ($this->getY()->isEven() ? 0x02 : 0x03));
            return $x;
        }

        return array_merge(array(0x04), $x, $this->getY()->toArray("be", $len));
    }

    public function precompute($power = null)
    {
        if( isset($this->precomputed) )
            return $this;

        $this->precomputed = array(
            "naf" => $this->_getNAFPoints(8),
            "doubles" => $this->_getDoubles(4, $power),
            "beta" => $this->_getBeta()
        );

        return $this;
    }

    protected function _hasDoubles($k)
    {
        if( !isset($this->precomputed) || !isset($this->precomputed["doubles"]) )
            return false;

        return count($this->precomputed["doubles"]["points"]) >= ceil(($k->bitLength() + 1) / $this->precomputed["doubles"]["step"]);
    }

    public function _getDoubles($step = null, $power = null)
    {
        if( isset($this->precomputed) && isset($this->precomputed["doubles"]) )
            return $this->precomputed["doubles"];

        $doubles = array( $this );
        $acc = $this;
        for($i = 0; $i < $power; $i += $step)
        {
            for($j = 0; $j < $step; $j++)
                $acc = $acc->dbl();
            array_push($doubles, $acc);
        }

        return array(
            "step" => $step,
            "points" => $doubles
        );
    }

    public function _getNAFPoints($wnd)
    {
        if( isset($this->precomputed) && isset($this->precomputed["naf"]) )
            return $this->precomputed["naf"];

        $res = array( $this );
        $max = (1  << $wnd) - 1;
        $dbl = $max === 1 ? null : $this->dbl();
        for($i = 1; $i < $max; $i++)
            array_push($res, $res[$i - 1]->add($dbl));

        return array(
            "wnd" => $wnd,
            "points" => $res
        );
    }

    public function _getBeta() {
        return null;
    }

    public function dblp($k)
    {
        $r = $this;
        for($i = 0; $i < $k; $i++)
            $r = $r->dbl();
        return $r;
    }
}

?>

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/elliptic-php/lib/Curve/BaseCurve/Point.php`.

**Classes defined**: Point

**Functions defined**: _getNAFPoints, encode, _hasDoubles, precompute, eq, __construct, validate, encodeCompressed, _encode, _getDoubles



## Detailed Walkthrough

### Code Structure

- Total lines: 121
- Code lines: 95
- Comment lines: 0
- Blank lines: 26

### Main Components

**Classes** (1):
- `Point`

**Functions** (12):
- `__construct()`
- `_encode()`
- `_getBeta()`
- `_getDoubles()`
- `_getNAFPoints()`
- `_hasDoubles()`
- `dblp()`
- `encode()`
- `encodeCompressed()`
- `eq()`
- `precompute()`
- `validate()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/elliptic-php/lib/Curve/BaseCurve/Point.php
```

