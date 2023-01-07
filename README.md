# JkImagePlaceholder
Processwire module for easy creation of placeholder images on the frontend. Uses TrueType fonts for the placeholder text
(fe Sorry, no pic!).

Features:

- 2 TTFs are shipped with this module by default (FjallaOne-Regular.ttf and Lobster-Regular.ttf). 
- Allows upload and deletion of other fonts
- Allows scanning the complete site to find and use other TrueTypeFonts (fe used by templates or other modules)
- Preview of all fonts in the select font input field - you can see how the font looks like
- Global setting of various colors: background color, text color,..
- Supports adding of text shadow to the placeholder text
- Set global placeholder text (multi-language)
- Set global CSS class for the placeholder image tag
- If you have installed FieldtypeColor or FieldtypeColorPicker you can select if you want to use one of these fields for color inputs instead of the default text input.

![Placeholderimage](https://raw.githubusercontent.com/juergenweb/JkImagePlaceholder/master/images/placeholderimage.jpg?raw=true)


## Public methods to set/change properties manually
- setTextColor(string)
- setBackgroundColor(string|null)
- setWidth(int)
- setHeight(int)
- setFontFamily(string)
- setFontSize(int)
- setText(string|null)
- setCSSClass(string)
- setShadowColor(string)
- setXOffset(int)
- setYOffset(int)
- setAltText(string)

Use these methods below to set a value or to overwrite default values from the module configuration.

### setText() method
With this method you can set or overwrite the global placeholder text or you can disable the output of any text.
If you have a multilingual site please use translatable strings (fe _('My text')) as value.
By default, there is no placeholder text set after you have installed the module.

`setText(_('My placeholder text'))`

If you want to disable the output of the text, use this method without a parameter inside the parenthesis.

`setText()`

In this case only the image without text inside will be rendered, independent if a global placeholder text was set in 
the backend or not.

### setTextColor() method

Set a hexadecimal color for the text if you want to overwrite the default text color.

`setTextColor('#990000')`

### setBackgroundColor() method

Set a hexadecimal color for the background if you want to add or overwrite the background.

`setBackgroundColor('#000000')`

### setFontFamily() method

Set the name of the Font-Family that should be used. You can only use fonts that you will find inside the font family select inside the module configuration. If you enter a font family name that does not exist, the default font-family will be used instead.
`setFontFamily('myFont')` or `setFontFamily('myFont.ttf')`.
It does not matter if you add the extension or not.

### setWidth() method

Set the width of the image in px.

`setWidth(600)`

### setHeight() method

Set the height of the image in px. If no height is set explicitly the height will be set to the value of the width.

`setHeight(300)`

### setCSSClass() method

Set or overwrite the CSS class of the image tag.

`setCSSClass('my-image')`

### setFontSize() method

Set the fontsize of the placeholder text in px (without entering the px inside the parenthesis).

`setFontSize(30)`

### setShadowColor() method

Set a hexadecimal color for the text if you want to add a shadow to the text.

`setShadowColor('#990000')`

If you want to disable the shadow, do not add a HEX code inside the parenthesis.

`setShadowColor()`

### setXOffset() method

Set the offset for the x-coordinate of the text shadow. You can enter positive and negative values

`setXOffset(3)`

Offset on the x-axis is 3px in this case.

### setYOffset() method

Set the offset for the y-coordinate of the text shadow. You can enter positive and negative values

`setYOffset(3)`

Offset on the y-axis is 3px in this case.

### setAltText() method
With this method you can change the alt attribute of the image tag.

`setAltText('my custom alt text')`


## Examples for usage in templates

### Usage with default values from the module configuration (only the size of the image will be set manually)

`echo $modules->JkImagePlaceholder->render();`

or

`echo $modules->JkImagePlaceholder->render(true);`

The first code outputs the img src as base64 string. In this case you have to write the image tag by yourself.
The second one with boolean true as parameter renders the complete image tag.

### Usage with all parameters set individually (global values will be overwritten)



    echo $modules->JkImagePlaceholder
    ->setFontSize(30)         
    ->setWidth(800)    
    ->setHeight(400)
    ->setBackgroundColor('#dddddd')
    ->setTextColor('#000000')
    ->setText('My placeholder text')
    ->setFontFamily('pacifico.ttf')
    ->setShadowColor('#666666')
    ->setXOffset(-1)
    ->setYOffset(1)
    ->render(true);

Take a look at the render method, which includes true as a boolean parameter.
This means that a complete image tag will be rendered instead of only the src value.
So if you enter true as parameter inside the parenthesis, a whole image tag will be rendered instead of the
image src only.

## Select field type for input field color
If you have installed FieldtypeColor and/or FieldtypeColorPicker you can select if you want to use one of these field types
or not.
Otherwise, an InputfieldText will be displayed for entering color values for text, background and shadow color.

1) Simple text input
![Placeholderimage](https://raw.githubusercontent.com/juergenweb/JkImagePlaceholder/master/images/text-input.jpg?raw=true)

2) Fieldtype ColorPicker input
![Placeholderimage](https://raw.githubusercontent.com/juergenweb/JkImagePlaceholder/master/images/color-picker-input.jpg?raw=true)

3) Fieldtype Color input
![Placeholderimage](https://raw.githubusercontent.com/juergenweb/JkImagePlaceholder/master/images/color-input.jpg?raw=true)

## Preview of font family

The font family selection field provides a preview of all fonts, so it will be much easier for you to decide which font
you want to use.

![Placeholderimage](https://raw.githubusercontent.com/juergenweb/JkImagePlaceholder/master/images/font-families-input.jpg?raw=true)

## Multi-language

This module will be also shipped with the German translation file.
