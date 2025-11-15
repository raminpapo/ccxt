# Documentation: php/static_dependencies/elliptic-php/lib/Curve/PresetCurve.php

## File Metadata

- **Path**: `php/static_dependencies/elliptic-php/lib/Curve/PresetCurve.php`
- **Size**: 588 bytes
- **Lines**: 28
- **Type**: PHP
- **Extension**: .php


## Original Source Code

```php
<?php

namespace Elliptic\Curve;

class PresetCurve
{
    public $curve;
    public $g;
    public $n;
    public $hash;

    function __construct($options)
    {
        if ( $options["type"] === "short" )
            $this->curve = new ShortCurve($options);
        elseif ( $options["type"] === "edwards" )
            $this->curve = new EdwardsCurve($options);
        else
            $this->curve = new MontCurve($options);

        $this->g = $this->curve->g;
        $this->n = $this->curve->n;
        $this->hash = isset($options["hash"]) ? $options["hash"] : null;
    }
}

?>

```

## High-Level Overview

This is a PHP file located at `php/static_dependencies/elliptic-php/lib/Curve/PresetCurve.php`.

**Classes defined**: PresetCurve

**Functions defined**: __construct



## Detailed Walkthrough

### Code Structure

- Total lines: 28
- Code lines: 22
- Comment lines: 0
- Blank lines: 6

### Main Components

**Classes** (1):
- `PresetCurve`

**Functions** (1):
- `__construct()`



## Usage Examples

No explicit usage examples found in the file. Refer to related test files or documentation.



## Performance & Security Notes

No specific performance or security issues detected.



## Related Files

No explicit file references found.



## Testing & Execution

**To execute this PHP file:**

```bash
php php/static_dependencies/elliptic-php/lib/Curve/PresetCurve.php
```

