# Christmas Lights

A lightweight web component and WordPress plugin that adds a festive string of Christmas lights at the top of your website. Default palette is `classic`.

## Web Component (CDN)

Include the script and add the element:

```html
<script type="module" src="https://cdn.example.com/christmas-lights@0.1.0/christmas-lights.js"></script>
<christmas-lights count="24" colors="classic" twinkle="true" speed="0.6" size="1" offset="0"></christmas-lights>
```

- `count`: number of bulbs (default 24)
- `colors`: either a preset (`classic`, `warm`) or comma-separated colors. Default: `classic` (red, green, blue, orange, white).
- `twinkle`: `true` | `false`
- `speed`: animation speed multiplier (default 0.6, lower = slower)
- `size`: scale multiplier (default 1)
- `offset`: top offset in px (default 0)

## WordPress Plugin

1. Copy this plugin folder to `wp-content/plugins/christmas-lights`.
2. Activate the plugin.
3. Lights appear at the top of your site.

### Filters

- `christmas_lights_component_src`: override script source, e.g. to point to your CDN.
- `christmas_lights_component_attrs`: provide attributes array to customize behavior.

Example (in theme’s `functions.php`):

```php
add_filter( 'christmas_lights_component_src', function( $src ) {
    return 'https://cdn.example.com/christmas-lights@0.1.0/christmas-lights.js';
});

add_filter( 'christmas_lights_component_attrs', function( $attrs ) {
    return array_merge( $attrs, array(
        'count' => 30,
        'colors' => 'classic',
        'twinkle' => 'true',
        'speed' => '1',
        'size' => '1',
        'offset' => '0',
    ) );
});
```

## Notes

- Pure web-component with Shadow DOM; no dependencies.
- Minimal animations for performance; pointer-events are disabled.
- Uses `wp_body_open` with footer fallback to ensure rendering.
