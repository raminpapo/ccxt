# Documentation: php/static_dependencies/elliptic-php/lib/Curve/MontCurve.php

## File Metadata

- **Path**: `php/static_dependencies/elliptic-php/lib/Curve/MontCurve.php`
- **Size**: 1,126 bytes
- **Lines**: 50
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Elliptic\Curve;

use Elliptic\Curve\MontCurve\Point;
use Elliptic\Utils;
use BN\BN;

class MontCurve extends BaseCurve
{
    public $a;
    public $b;
    public $i4;
    public $a24;

    function __construct($conf)
    {
        parent::__construct("mont", $conf);

        $this->a = (new BN($conf["a"], 16))->toRed($this->red);
        $this->b = (new BN($conf["b"], 16))->toRed($this->red);
        $this->i4 = (new BN(4))->toRed($this->red)->redInvm();
        $this->a24 = $this->i4->redMul($this->a->redAdd($this->two));
    }

    public function validate($point)
    {
        $x = $point->normalize()->x;
        $x2 = $x->redSqr();
        $rhs = $x2->redMul($x)->redAdd($x2->redMul($this->a))->redAdd($x);
        $y = $rhs->redSqr();

        return $y->redSqr()->cmp($rhs) ===0;
    }

    public function decodePoint($bytes, $enc = false) {
        return $this->point(Utils::toArray($bytes, $enc), 1);
    }

    public function point($x, $z) {
        return new Point($this, $x, $z);
    }

    public function pointFromJSON($obj) {
        return Point::fromJSON($this, $obj);
    }
}

?>

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/elliptic-php/lib/Curve/MontCurve.php`.

**Classes defined**: MontCurve

**Functions defined**: pointFromJSON, point, __construct, validate, decodePoint



## Detailed Walkthrough

### Code Structure

- Total lines: 50
- Code lines: 38
- Comment lines: 0
- Blank lines: 12

### Main Components

**Functions** (5):
- `__construct()`
- `decodePoint()`
- `point()`
- `pointFromJSON()`
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
php php/static_dependencies/elliptic-php/lib/Curve/MontCurve.php
```

