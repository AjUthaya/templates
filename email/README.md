# Email sample

## Device support ([EmailOnAcid](https://www.emailonacid.com/))

### Tested on:

- Placeholder

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
  src="{src}"
  width="{width}"
  height="{height}"
  border="0"
  alt="{alt}"
  style="{style}; display: block; border: 0px;"
/>
```

### Link:

```html
<a href="#" style="{style}">{style}</a>
```

### Outlook conditional statement

```html
<!--[if mso]>
  Outlook content
<![endif]-->

<!--[if !mso]> <!---->
Non-outlook content
<!-- <![endif]-->
```

### Padding-based button:

```html
<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td
      bgcolor="#{bgcolor}"
      style="padding: {padding}; -webkit-border-radius: {webkit-border-radius}; border-radius:{border-radius};"
      align="{align}"
    >
      <a
        href="{link}"
        target="_blank"
        style="font-size: {font-size}px; font-family: {font}; color: #{color}; text-decoration: {decoration}; display: {display};"
        >{button text}</a
      >
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
        href="{link}"
        target="_blank"
        style="font-size: {font-size}px; font-family: {font}; color: #{color}; text-decoration: {decoration}; border-radius: {border-radius}px; -webkit-border-radius: {webkit-border-radius}px; background-color: #{bgcolor}; border-top: {border-top}; border-bottom: {border-bottom}; border-right: {border-right}; border-left: {border-left}; display: inline-block;"
        >{button text}</a
      >
    </td>
  </tr>
</table>
```

### Padding+border-based button:

```html
<table border="0" cellspacing="0" cellpadding="0">
  <tr>
    <td
      align="{align}"
      style="border-radius: {border-radius}px;"
      bgcolor="#{bgcolor}"
    >
      <a
        href="{link}"
        target="_blank"
        style="font-size: {font-size}px; font-family: {font}; color: #{color}; text-decoration: {decoration}; border-radius: {border-radius}px; padding: {padding}; border: {border}; display: inline-block;"
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
