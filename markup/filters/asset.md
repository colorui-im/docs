---
title: "Filters: asset"
description: "Documentation on the 'asset' Twig filter."
---
# asset

## Usage

The `| asset` filter generates a URL for an asset using the current scheme of the request (HTTP or HTTPS):

```twig
{{ 'img/photo.jpg' | asset }}

{# or #}

{{ asset('img/photo.jpg') }}
```

See the [Asset helper method](/v1.2/docs/services/helpers#method-asset) for more information.
