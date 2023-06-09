# Change Log
All notable changes to this project will be documented in this file.

## [1.5.0] - 2023-03-15

### Saving all previously set values in module config
If you have changed some of the configuration settings inside the module configuration and you have pressed the button
to scan for new files afterwards, all previously set changes were lost.
In this version, this behavior was eliminated. So if you press the button to update your font files, all previously
done changes inside your module configuration were saved before, so they will not get lost anymore.
Some minor code optimizations were done too to optimize the performance.

## [1.5.1] - 2023-06-09

### New place to store your custom fonts

During this update a new folder will be created outside the module directory. You will find this new folder under this path:
site/assets/files/JkImagePlaceholder/

This step was necessary, because the custom uploaded font files, which have bee stored inside the font folder of this
modules until now, will be deleted during an update.
To prevent the deletion, the custom font will be stored inside this new location now.

You do not have to take care of this behavior during the this update, because all your previously uploaded custom files will be copied
to the new location automatically.
