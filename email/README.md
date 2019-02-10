# Email sample project

## Device support

### Basic links

- [Testing plattform (EmailOnAcid)](https://www.emailonacid.com/)

- [Link to CSS support for email clients](https://www.campaignmonitor.com/css/color-background/background-image/)

### Tested on:

- Not tested with diffrent devices yet

## Snippets for email

### Unselectable:

```
-webkit-touch-callout: none;-webkit-user-select: none;-khtml-user-select: none;-moz-user-select: none;-ms-user-select: none;user-select: none;
```

### Hide:

```
display: none;mso-hide: all;overflow: hidden;height: 0; max-height: 0;width: 0;max-width: 0;font-size: 0;line-height: 0;
```

### Image:

```html
<img
  src="{image_path}"
  width="{image_width}"
  height="{image_height}"
  border="0"
  alt="{image_alt}"
  style="display: block; border: 0px;"
/>
```

### Outlook: Conditional statements

```html
<!-- Targets Outlook 2007 and up -->
<!--[if mso]>
  Outlook content
<![endif]-->

<!-- Default: Target all but Outlook 2007 and up -->
<!--[if !mso]> <!---->
Non-outlook content
<!-- <![endif]-->
```

### Table container:

```html
<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td>
      Content
    </td>
  </tr>
</table>
```

### Padding-based button:

```html
<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td
      bgcolor="{button_background}"
      style="padding: {button_padding}; border-radius:{button_border_radius};"
      align="{button_align}"
    >
      <a
        href="{button_link}"
        target="_blank"
        style="font-size: {button_font_size}; font-family: {button_font_family}; color: {button_font_color}; text-decoration: {button_font_decoration}; display: {button_display};"
      >
        Link
      </a>
    </td>
  </tr>
</table>
```

### Border-based button:

```html
<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td>
      <a
        href="{button_link}"
        target="_blank"
        style="font-size: {button_font_size}; font-family: {button_font_family}; color: {button_font_color}; text-decoration: {button_font_decoration}; border-radius: {button_border_radius}; background-color: {button_background}; border: {button_border};display: inline-block;"
      >
        Link
      </a>
    </td>
  </tr>
</table>
```

### Padding+border-based button:

```html
<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td
      align="{button_align}"
      style="border-radius: {button_border_radius};"
      bgcolor="#{button_background}"
    >
      <a
        href="{button_link}"
        target="_blank"
        style="font-size: {button_font_size}; font-family: {button_font_family}; color: {button_font_color}; text-decoration: {button_font_decoration}; border-radius: {button_border_radius}; padding: {button_padding}; border: {button_border}; display: inline-block;"
        >{button text}</a
      >
    </td>
  </tr>
</table>
```

### Media queries:

```css
/* BASE MEDIA QUERY */
@media screen and ({declaration}) {
  {content}
}

/* MAX-WIDTH MEDIA QUERY */
@media screen and (max-width: {width}) {
  {content}
}

/* MIN-WIDTH MEDIA QUERY */
@media screen and (min-width: {width}) {
  {content}
}

/* IPAD 1 & 2 + IPAD MINI MEDIA QUERY */
@media screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio: 1) {
    {style}
}

/* IPAD 3 & 4 MEDIA QUERY */
@media screen and (min-device-width: 768px) and (max-device-width: 1024px) and (-webkit-min-device-pixel-ratio: 2) {
    {style}
}

/* IPHONE 2G/3G/3GS MEDIA QUERY */
@media screen and (min-device-width: 320px) and (max-device-width: 480px) and (-webkit-min-device-pixel-ratio: 1) {
    {style}
}

/* IPHONE 4/4S/5/IPHONE 6 (ZOOM VIEW) MEDIA QUERY */
@media screen and (min-device-width: 320px) and (max-device-width: 568px) and (-webkit-min-device-pixel-ratio: 2) {
    {style}
}

/* HTC ONE + SAMSUNG GALAXY S4/S5 MEDIA QUERY */
@media screen and (device-width: 360px) and (device-height: 640px) and (-webkit-device-pixel-ratio: 3) {
    {style}
}

/* IPHONE 6 (STANDARD VIEW) + IPHONE 6 PLUS (ZOOM VIEW) MEDIA QUERY */
@media screen and (max-device-width: 375px) and (max-device-height: 667px) {
	{style}
}

/* IPHONE 6 PLUS (STANDARD VIEW) MEDIA QUERY */
@media screen and (max-device-width: 414px) and (max-device-height: 776px) {
	{style}
}
```
