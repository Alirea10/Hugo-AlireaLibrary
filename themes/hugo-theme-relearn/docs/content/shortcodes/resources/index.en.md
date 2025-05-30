+++
categories = ['howto', 'reference']
description = 'List resources contained in a page bundle'
title = 'Resources'

[[resources]]
  name = 'MaybeTreasure.txt'
  src = 'MaybeTreasure.en.txt'
+++

The `resources` shortcode displays links to resources contained in a [page bundle](https://gohugo.io/content-management/page-bundles/).

{{% resources sort="asc" /%}}

## Usage

{{< tabs groupid="shortcode-parameter">}}
{{% tab title="shortcode" %}}

````go
{{%/* resources sort="asc" /*/%}}
````

{{% /tab %}}
{{% tab title="partial" %}}

````go
{{ partial "shortcodes/resources.html" (dict
  "page" .
  "sort" "asc"
)}}
````

{{% /tab %}}
{{< /tabs >}}

Multilanguage features are not supported directly by the shortcode but rely on Hugo's handling for resource translations applied when the theme iterates over all available resources.

### Parameter

| Name                  | Default         | Notes       |
|-----------------------|-----------------|-------------|
| **style**             | `transparent`   | The style scheme used for the box.<br><br>- by severity: `caution`, `important`, `info`, `note`, `tip`, `warning`<br>- by brand color: `primary`, `secondary`, `accent`<br>- by color: `blue`, `cyan`, `green`, `grey`, `magenta`, `orange`, `red`<br>- by special color: `default`, `transparent`, `code`<br><br>You can also [define your own styles](shortcodes/notice#defining-own-styles). |
| **color**             | see notes       | The [CSS color value](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value) to be used. If not set, the chosen color depends on the **style**. Any given value will overwrite the default.<br><br>- for severity styles: a nice matching color for the severity<br>- for all other styles: the corresponding color |
| **title**             | see notes       | Arbitrary text for the box title. Depending on the **style** there may be a default title. Any given value will overwrite the default.<br><br>- for severity styles: the matching title for the severity<br>- for all other styles: `Resources`<br><br>If you want no title for a severity style, you have to set this parameter to `" "` (a non empty string filled with spaces) |
| **icon**              | see notes       | [Font Awesome icon name](shortcodes/icon#finding-an-icon) set to the left of the title. Depending on the **style** there may be a default icon. Any given value will overwrite the default.<br><br>- for severity styles: a nice matching icon for the severity<br>- for all other styles: `paperclip`<br><br>If you want no icon, you have to set this parameter to `" "` (a non empty string filled with spaces) |
| **expanded**          | _&lt;empty&gt;_ | Whether to draw an expander and how the resource list is displayed.<br><br>- _&lt;empty&gt;_: no expander is drawn and the resource list is permanently shown<br>- `true`: the expander is drawn and the resource list is initially shown<br>- `false`: the expander is drawn and the resource list is initially hidden |
| **sort**              | `asc`           | Sorting the output in `asc`ending or `desc`ending order. |
| **pattern**           | `.*`            | A [regular expressions](https://en.wikipedia.org/wiki/Regular_expression), used to filter the resources [by name](https://gohugo.io/methods/resource/name/). For example:<br><br>- to match a file suffix of 'jpg', use `.*\.jpg` (not `*.\.jpg`)<br>- to match file names ending in `jpg` or `png`, use `.*\.(jpg\|png)` |

## Examples

### Custom Title, List of Resources Ending in png, jpg or gif

````go
{{%/* resources title="Related **files**" pattern=".*\.(png|jpg|gif)" /*/%}}
````

{{% resources title="Related **files**" pattern=".*\.(png|jpg|gif)" /%}}

### Info Styled Box, Descending Sort Order

````go
{{%/* resources style="info" sort="desc" /*/%}}
````

{{% resources style="info" sort="desc" /%}}

### With User-Defined Color and Font Awesome Brand Icon

````go
{{%/* resources color="fuchsia" icon="fa-fw fab fa-hackerrank" /*/%}}
````

{{% resources color="fuchsia" icon="fa-fw fab fa-hackerrank" /%}}

### Expander with Initially Hidden Resource List

````go
{{%/* resources style="primary" expanded="false" /*/%}}
````

{{% resources style="primary" expanded="false" /%}}

### Style, Color, Title and Icons

For further examples for **style**, **color**, **title** and **icon**, see the [`notice` shortcode](shortcodes/notice) documentation. The parameter are working the same way for both shortcodes, besides having different defaults.
