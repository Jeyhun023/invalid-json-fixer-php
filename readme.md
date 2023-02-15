## jeyhun023/invalid-json-fixer-php

## Usage
```php
use Jeyhun\Json\Fixer;

$json = (new Fixer)->fix('{"a":1,"b":2');
// {"a":1,"b":2}

$json = (new Fixer)->fix('{"a":1,"b":true,');
// {"a":1,"b":true}

$json = (new Fixer)->fix('{"b":[1,[{"b":1,"c"');
// {"b":[1,[{"b":1,"c":null}]]}

// For batch fixing, you can just reuse same fixer instance:
$fixer = new Fixer;

$fixer->fix('...');
$fixer->fix('...');
// ...
```

## Error

If there's error and fixer cant fix the JSON for some reason, it will throw a `RuntimeException`.
You can disable this behavior by passing silent flag (2nd param) to `fix()` in which case original input is returned:

```php
(new Fixer)->silent()->fix('invalid');
// 'invalid'

(new Fixer)->silent(true)->fix('invalid');
// 'invalid'

(new Fixer)->silent(false)->fix('invalid');
// RuntimeException
```

