---
extends: _layouts.documentation
title: "Font Families"
description: "Utilities for controlling the font family of an element."
features:
  responsive: true
  customizable: true
  hover: false
  focus: false
---

@include('_partials.class-table', [
  'rows' => $page->config['theme']['fontFamily']->map(function ($fonts, $variant) {
    $class = ".font-{$variant}";
    $code = 'font-family: '.$fonts->implode(', ').';';
    $description = "Set the font family to the {$variant} font stack.";
    return [
      $class,
      $code,
      $description,
    ];
  })
])

### Sans-serif

Use `.font-sans` to apply a web safe sans-serif font family:

@component('_partials.code-sample')
<p class="font-sans text-lg text-gray-800 text-center">
  I'm a sans-serif paragraph.
</p>
@endcomponent

### Serif

Use `.font-serif` to apply a web safe serif font family:

@component('_partials.code-sample')
<p class="font-serif text-lg text-gray-800 text-center">
  I'm a serif paragraph.
</p>
@endcomponent

### Monospaced

Use `.font-mono` to apply a web safe monospaced font family:

@component('_partials.code-sample')
<p class="font-mono text-lg text-gray-800 text-center">
  I'm a monospaced paragraph.
</p>
@endcomponent

## Customizing

### Font Families

By default Tailwind provides three font family utilities: a cross-browser sans-serif stack, a cross-browser serif stack, and a cross-browser monospaced stack. You can change, add, or remove these by editing the `fonts` section of your Tailwind config.

@component('_partials.customized-config', ['key' => 'fonts'])
- 'sans': ['-apple-system', 'BlinkMacSystemFont', ...],
- 'serif': ['Georgia', 'Cambria', ...],
- 'mono': ['SFMono-Regular', 'Menlo', ...],
+ 'display': ['Oswald', ...],
+ 'body': ['Open Sans', ...],
@endcomponent

Font families can be specified as an array or as a simple comma-delimited string:

```js
{
  // Array format:
  'sans': ['Helvetica', 'Arial', 'sans-serif'],

  // Comma-delimited format:
  'sans': 'Helvetica, Arial, sans-serif',
}
```

Note that **Tailwind does not automatically escape font names** for you. If you're using a font that contains an invalid identifier, wrap it in quotes or escape the invalid characters.

```js
{
  // Won't work:
  'sans': ['Exo 2', ...],

  // Add quotes:
  'sans': ['"Exo 2"', ...],

  // ...or escape the space:
  'sans': ['Exo\\ 2', ...],
}

```

@include('_partials.variants-and-disabling', [
    'utility' => [
        'name' => 'font',
        'property' => 'fonts',
    ],
    'variants' => [
        'responsive',
    ],
])