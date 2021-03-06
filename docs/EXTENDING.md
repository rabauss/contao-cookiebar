# Create own Cookie-Types
All cookie types are prepared by the PHP class `CookieHandler`. This class allows you to prepare the scripts to be processed by the JS plugin. See [Hooks](EXTENDING.md#hooks) for integration.

## Functions

### `addScript(string $strScript, bool $confirmed, int $pos)`
Adds a script at the desired position (e.g. `<script>console.log(1);</script>`)

Parameter | Description
---------- | -----------
`string $strScript` | Enables the integration of your own cookie types. (see Create own Cookie-Types)
`bool $confirmed` | Defines whether the script should be output when the cookie is accepted or not
`int $pos` | Defines the position in HTML (see "Constants": Position-Constants)

### `addResource(string $strSrc, array $flags, int $mode)`
Adds an external resource in the header area (e.g. `<script src="www.vendor.com/script.js" async></script>`)

Parameter | Description
---------- | -----------
`string $strSrc` | The external URL
`array $flags` | Defines further tag attributes (e.g. `['async', 'defer']`)
`int $mode` | Defines the loading mode (see "Constants": Loading-Constants)

## Constants
Position-Constants | Description
---------- | -----------
`POS_BELOW` | Below the content within the body tag
`POS_ABOVE` | Above the content within the body tag
`POS_HEAD` | Within the head tag

Loading-Constants | Description
---------- | -----------
`LOAD_CONFIRMED` | Load only after confirmation
`LOAD_UNCONFIRMED` | Load only if not confirmed
`LOAD_ALWAYS` | Load always

<br/>

# Create own iFrame-Types
By expanding the `config/config.yml` file, you can add as many iFrame types as you want to respond to different vendors. Types for blocking Youtube, Vimeo and Google Maps iFrames are already delivered by default. 

## Example of new types
Add a new module and the template to which you have to react:
```yaml
contao_cookiebar:
  iframe_types:
    vendortype: 
      - ce_html_vendortype
```
Now another option "vendortype" appears in the cookie type "iFrame" for the select field "iFrame types". Select this to block all iFrames with the template `ce_html_vendortype` until the cookie is accepted.

## Example of additional templates
If you want to supplement your own templates with an already existing iFrame type, these can also be considered.
```yaml
contao_cookiebar:
  iframe_types:
    googlemaps: 
      - ce_my_google_template
```

<br/>

# Hooks
Hook | Parameter | Description
---------- | ----------- | -----------
`compileCookieType` | `string $type`, `CookieHandler $objCookieHandler` | Enables the integration of your own cookie types. (see Create own Cookie-Types)
`parseCookiebarTemplate` | `FrontendTemplate $objTemplate`, `$objConfig` | Is called before parsing the cookiebar template.

<br/>

# Further links
- [Install & Configuration](CONFIGURATION.md)
- [Styling & Customization](CUSTOMIZATION.md)
- [Extended usage](EXTENDED_USAGE.md)
