+++
categories = ['howto', 'reference']
description = 'Clickable buttons'
title = 'Button'
+++

The `button` shortcode displays a clickable button with adjustable color, title and icon.

{{% button href="https://gohugo.io/" %}}Go Hugo{{% /button %}}
{{% button href="images/magic.gif?download" style="tip" icon="wand-magic-sparkles" %}}Download Magic{{% /button %}}

## Usage

{{< tabs groupid="shortcode-parameter">}}
{{% tab title="shortcode" %}}

````go
{{%/* button href="https://gohugo.io/" %}}Go Hugo{{% /button */%}}
{{%/* button href="images/magic.gif?download" style="tip" icon="wand-magic-sparkles" %}}Download Magic{{% /button */%}}
````

{{% /tab %}}
{{% tab title="partial" %}}

````go
{{ partial "shortcodes/button.html" (dict
    "page" .
    "href" "https://gohugo.io/"
    "content" "Go Hugo"
)}}
{{ partial "shortcodes/button.html" (dict
  "page" .
  "href" "https://gohugo.io/"
  "style" "tip"
  "icon" "wand-magic-sparkles"
  "content" "Download Magic"
)}}
````

{{% /tab %}}
{{< /tabs >}}

### Parameter

| Name                  | Default         | Notes       |
|-----------------------|-----------------|-------------|
| **href**              | _&lt;empty&gt;_ | Either the destination URL for the button or JavaScript code to be executed on click. If this parameter is not set, the button will do nothing but is still displayed as clickable.<br><br>- if starting with `javascript:` all following text will be executed in your browser<br>- every other string will be interpreted as URL, you can use [link effects](authoring/markdown#link-effects) as well|
| **style**             | `transparent`   | The style scheme used for the button.<br><br>- by severity: `caution`, `important`, `info`, `note`, `tip`, `warning`<br>- by brand color: `primary`, `secondary`, `accent`<br>- by color: `blue`, `cyan`, `green`, `grey`, `magenta`, `orange`, `red`<br>- by special color: `default`, `transparent`, `code`<br><br>You can also [define your own styles](shortcodes/notice#defining-own-styles). |
| **color**             | see notes       | The [CSS color value](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value) to be used. If not set, the chosen color depends on the **style**. Any given value will overwrite the default.<br><br>- for severity styles: a nice matching color for the severity<br>- for all other styles: the corresponding color |
| **icon**              | see notes       | [Font Awesome icon name](shortcodes/icon#finding-an-icon) set to the left of the title. Depending on the **style** there may be a default icon. Any given value will overwrite the default.<br><br>- for severity styles: a nice matching icon for the severity<br>- for all other styles: _&lt;empty&gt;_<br><br>If you want no icon for a severity style, you have to set this parameter to `" "` (a non empty string filled with spaces) |
| **iconposition**      | `left`          | Places the icon to the `left` or `right` of the title. |
| **type**              | see notes       | The [button type](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button#attr-type) if **href** is JavaScript. Otherwise the parameter is not used. If the parameter is not given it defaults to `button` |
| _**&lt;content&gt;**_ | see notes       | Arbitrary text for the button title. Depending on the **style** there may be a default title. Any given value will overwrite the default.<br><br>- for severity styles: the matching title for the severity<br>- for all other styles: _&lt;empty&gt;_<br><br>If you want no title for a severity style, you have to set this parameter to `" "` (a non empty string filled with spaces) |

## Examples

### Style

#### By Severity

````go
{{%/* button href="https://gohugo.io/" style="caution" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="important" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="info" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="note" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="tip" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="warning" %}}Get Hugo{{% /button */%}}
````

{{% button href="https://gohugo.io/" style="caution" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="important" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="info" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="note" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="tip" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="warning" %}}Get Hugo{{% /button %}}


#### By Brand Colors

````go
{{%/* button href="https://gohugo.io/" style="primary" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="secondary" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="accent" %}}Get Hugo{{% /button */%}}
````

{{% button href="https://gohugo.io/" style="primary" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="secondary" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="accent" %}}Get Hugo{{% /button %}}

#### By Color

````go
{{%/* button href="https://gohugo.io/" style="blue" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="cyan" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="green" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="grey" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="magenta" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="orange" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="red" %}}Get Hugo{{% /button */%}}
````

{{% button href="https://gohugo.io/" style="blue" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="cyan" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="green" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="grey" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="magenta" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="orange" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="red" %}}Get Hugo{{% /button %}}

#### By Special Color

````go
{{%/* button href="https://gohugo.io/" style="default" %}}Get Hugo{{% /button */%}}
{{%/* button href="https://gohugo.io/" style="transparent" %}}Get Hugo{{% /button */%}}
````

{{% button href="https://gohugo.io/" style="default" %}}Get Hugo{{% /button %}}
{{% button href="https://gohugo.io/" style="transparent" %}}Get Hugo{{% /button %}}

### Icon

#### Empty

````go
{{%/* button href="https://gohugo.io/" icon=" " %}}{{% /button */%}}
````

{{% button href="https://gohugo.io/" icon=" " %}}{{% /button %}}

#### Only

````go
{{%/* button href="https://gohugo.io/" icon="download" %}}{{% /button */%}}
````

{{% button href="https://gohugo.io/" icon="download" %}}{{% /button %}}

#### To the Left

````go
{{%/* button href="https://gohugo.io/" icon="download" %}}Get Hugo{{% /button */%}}
````

{{% button href="https://gohugo.io/" icon="download" %}}Get Hugo{{% /button %}}

#### To the Right

````go
{{%/* button href="https://gohugo.io/" icon="download" iconposition="right" %}}Get Hugo{{% /button */%}}
````

{{% button href="https://gohugo.io/" icon="download" iconposition="right" %}}Get Hugo{{% /button %}}

#### Override for Severity

````go
{{%/* button href="https://gohugo.io/" icon="dragon" style="warning" %}}Get Hugo{{% /button */%}}
````

{{% button href="https://gohugo.io/" icon="dragon" style="warning" %}}Get Hugo{{% /button %}}

### Link Effects (Target, Download)

You can use [link effects](authoring/markdown#link-effects) with your `href` to open the link in a different tab or starting a download.

````go
{{%/* button href="https://gohugo.io/?target=_blank" %}}Go Hugo{{% /button */%}}
{{%/* button href="images/magic.gif?download" style="tip" icon="wand-magic-sparkles" %}}Download Magic{{% /button */%}}
````

{{% button href="https://gohugo.io/?target=_blank" %}}Go Hugo{{% /button %}}
{{% button href="images/magic.gif?download" style="tip" icon="wand-magic-sparkles" %}}Download Magic{{% /button %}}

### Other

#### With User-Defined Color, Font Awesome Brand Icon and Markdown Title

````go
{{%/* button href="https://gohugo.io/" color="fuchsia" icon="fa-fw fab fa-hackerrank" %}}Get **Hugo**{{% /button */%}}
````

{{% button href="https://gohugo.io/" color="fuchsia" icon="fa-fw fab fa-hackerrank" %}}Get **Hugo**{{% /button %}}

#### Severity Style with All Defaults

````go
{{%/* button href="https://gohugo.io/" style="tip" %}}{{% /button */%}}
````

{{% button href="https://gohugo.io/" style="tip" %}}{{% /button %}}

#### Button to Internal Page

````go
{{%/* button href="/index.html" %}}Home{{% /button */%}}
````

{{% button href="/index.html" %}}Home{{% /button %}}

#### Button with JavaScript Action

If your JavaScript action does not change the focus afterwards, make sure to call `this.blur()` in the end to unselect the button.

````go
{{%/* button style="primary" icon="bullhorn" href="javascript:alert('Hello world!');this.blur();" %}}Shout it out{{% /button */%}}
````

{{% button style="primary" icon="bullhorn" href="javascript:alert('Hello world!');this.blur();" %}}Shout it out{{% /button %}}

#### Button within a `form` Element

To use native HTML elements in your Markdown, add this in your `hugo.toml`

````toml
[markup.goldmark.renderer]
    unsafe = true
````

````html
<form action="../../search.html" method="get">
  <input name="search-by-detail" class="search-by" type="search">
  {{%/* button type="submit" style="secondary" icon="search" %}}Search{{% /button */%}}
</form>
````

<form action="../../search.html" method="get">
  <div class="searchform" style="width: 20vw;">
    <input name="search-by-detail" class="search-by" type="search" placeholder="Search...">
    {{% button type="submit" style="secondary" icon="search" %}}Search{{% /button %}}
  </div>
</form>
