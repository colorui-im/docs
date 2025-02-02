# Templating

Winter extends the [Twig template language](https://twig.symfony.com/doc/2.x/) with a number of functions, tags, filters and variables. These extensions allow you to use the CMS features and access the page environment information inside your templates.

## Variables

Template variables are printed on the page using *double curly brackets*.

```twig
{{ variable }}
```

Variables can also represent *expressions*.

```twig
{{ isAjax ? 'Yes' : 'No' }}
```

Variables can be concatenated with the `~` character.

```twig
{{ 'Your name: ' ~ name }}
```

Winter provides global variables under the `this` variable, as listed under the **Variables** section.

## Tags

Tags are a unique feature to Twig and are wrapped with `{% %}` characters.

```twig
{% tag %}
```

Tags provide a more fluent way to describe template logic.

```twig
{% if stormCloudComing %}
    Stay inside
{% else %}
    Go outside and play
{% endif %}
```

The `{% set %}` tag can be used to set variables inside the template.

```twig
{% set activePage = 'blog' %}
```

Tags can take on many different syntaxes and are listed under the **Tags** section.

## Filters

Filters act as modifiers to variables for a single instance and are applied using a *pipe symbol* followed by the filter name.

```twig
{{ 'string' | filter }}
```

Filters can take arguments like a function.

```twig
{{ price | currency('USD') }}
```

Filters can be applied in succession.

```twig
{{ 'Winter Glory' | upper | replace({'Winter': 'Morning'}) }}
```

Filters are listed under the **Filters** section.

## Functions

Functions allow logic to be executed and the return result acts as a variable.

```twig
{{ function() }}
```

Functions can take arguments.

```twig
{{ dump(variable) }}
```

Functions are listed under the **Functions** section.

## Access logic

The most important thing to learn about Twig is how it accesses the PHP layer. For convenience sake `{{ foo.bar }}` does the following checks on a PHP object:

1. Check if `foo` is an array and `bar` a valid element.
1. If not, and if `foo` is an object, check that `bar` is a valid property.
1. If not, and if `foo` is an object, check that `bar` is a valid method (even if bar is the constructor - use `__construct()` instead).
1. If not, and if `foo` is an object, check that `getBar` is a valid method.
1. If not, and if `foo` is an object, check that `isBar` is a valid method.
1. If not, return a `null` value.

## Unsupported features

There are some features offered by Twig that are not supported by Winter. They are listed below next to the equivalent feature.

Tag | Equivalent
------------- | -------------
`{% extend %}` | Use [Layouts](../cms/layouts) or `{% placeholder %}`
`{% include %}` | Use `{% partial %}` or `{% content %}`
