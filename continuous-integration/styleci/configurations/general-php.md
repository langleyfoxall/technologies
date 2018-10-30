# StyleCI - General PHP

The following is a recommended configuration for general PHP projects which may or may not use a framework. If you are
using Laravel please use the alternative configuration [here](laravel.md). This configuration uses the `psr2` 
preset with risky heuristics enabled. It is also tailored to suit our internal PHP & JavaScript guidelines.

```yaml
php:
  preset: psr2
  
  risky: true

  enabled:
    - concat_with_spaces

  disabled:
    - short_array_syntax
    - phpdoc_summary
    - length_ordered_imports
    - phpdoc_no_package
    - concat_without_spaces

  finder:
    exclude:
    - "tests"
js:
  tab-width: 4
  use-tabs: false
  print-width: 120
  double-quotes: false
  trailing-commas: es5
  semicolons: true
  arrow-parens: avoid
  bracket-spacing: true
  finder:
    exclude:
      - node_modules
      - storage
      - vendor
      - public
    name:
      - "*.js"
      - "*.jsx"
    not-name:
      - "*.min.js"
ts: false
css: false
py: false
```
