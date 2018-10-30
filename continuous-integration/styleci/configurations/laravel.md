# StyleCI - Laravel

The following is a recommended configuration for Laravel that uses the `laravel` StyleCI preset along with risky 
heuristics enabled. It also follows PSR-2 and is tailored to suit our internal PHP & JavaScript guidelines.

```yaml
php:
  preset: laravel

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
    - "node_modules"
    - "storage"
    - "vendor"
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
