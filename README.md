# JkImagePlaceholder
Processwire module for easy creation of placeholder images on the frontend. Uses TrueType fonts for the placeholder text (fe Sorry, no pic!).
2 TTFs are installed by default (FjallaOne-Regular.ttf and Lobster-Regular.ttf). If you have stored TTF under your site/template document tree, this module will also take care of it.
If you want to use a TTF which is not existent on the system, you can upload it inside the configuration page or you add it under your template folder.
You can set default values that should be used for all placeholder images, but you can overwrite every param (size, text color, background color,...) on the fly on each instance.

![Placeholderimage](https://raw.githubusercontent.com/juergenweb/JkImagePlaceholder/master/placeholderimage.jpg?raw=true)

## Configuration options
- Set the default text for the placeholder image (multilanguage)
- Set the default background color for the image in hexadecimal color code
- Set the default color for the text in hexadecimal color code
- Set the default font for the text from a select field
- Set a default CSS class for the placeholder images
- Set the default fontsize

Additional font files in TrueType format (ttf) can be uploaded via an upload field.
If you are using TTF files inside your template, you can use them too. This module scans all directories under the site/template folder for TTF files and saves the name and the path of TTF files found to a database field. So you can use these fonts for your placeholder images too.
This is very useful, because you do not have to store font files twice (inside the template and inside the module).

## Setting Methods
- setTextColor(string)
- setBackgroundColor(string)
- setWidth(int)
- setHeight(int)
- setFontFamily(string)
- setFontSize(int)
- setText(string)
- setCSSClass(string)

Use these methods to set a value or to overwrite default values from the module configuration.

### setTextColor() method

Set a hexadecimal color for the text if you want to overwrite the default text color.
`setTextColor('#990000')`

### setBackgroundColor() method

Set a hexadecimal color for the background if you want to add or overwrite the background. On default there is no color set (transparent background).
`setBackgroundColor('#000000')`

### setFontFamily() method

Set the name of the Font-Family that should be used. You can only use fonts that you will find inside the font family select inside the module configuration. If you will enter a font family name that does not exist, the default font-family will be used instead.
`setFontFamily('myFont')`

### setWidth() method

Set the width of the image in px.
`setWidth(600)`

### setHeight() method

Set the height of the image in px.
`setHeight(300)`

If you want the placeholder image to be squared, do not enter a height.

### setCSSClass() method

Set or overwrite the CSS class of the image tag.
`setCSSClass('my-image')`

### setFontSize() method

Set the fontsize of the placeholdertext in px.
`setFontSize(30)`

## Examples for usage in templates

### Usage with default values from the module configuration (only the size of the image will be set manually)

`echo $modules->JkImagePlaceholder->setWidth(800)->setHeight(400)->render();`

This will output the img src as base64 string.

### Usage with all parameters set individually (default values will be overwritten)

`echo $modules->JkImagePlaceholder->setFontSize(30)->setWidth(800)->setHeight(400)->setBackgroundColor('#dddddd')->setTextColor('#000000')->setText('My placeholder')->setFontFamily('pacifico')->render(true);`

Take a look at the render method, which includes true as a boolean value. This means that a complete image tag will be rendered instead of only the src value.

## Multilanguage

The text for the placeholder can be set multilingual (in module configuration and via setText() method). By setting the text via setText() method in template, please use translateable strings(fe _('My text')) for multilanguage text.
