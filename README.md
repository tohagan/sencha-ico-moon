## DESCRIPTION

Converts an ICO-Moon project file into a SASS _icons.scss file for use in your Sencha Touch project.

## USAGE

    $ sench-ico-moon <icomoon-project>.json <font-name>

## Creating a custom icon font file for Sencha Touch using IcoMoon 

To create an icon file for Sench Touch ...

Visit [https://icomoon.io/app](https://icomoon.io/app), create a Project and select your icons from the many free and less free font icons.

Make sure that you **name your project* using the online **Project Manager** to your font name (`myfont` in this example).  

Download Project and font ZIP file ... 

1. Save ico-moon project: `myfont.json` 
   - Saved via Menu (top left button) > Manage Projects > Download
2. Save `myfont.zip` 
   - Saved via Font > Download
3. Create folder called `resources/sass/stylesheets/fonts/myfonts`
4. Copy font files in `myfont.zip/fonts/` into this folder.
  - If you named your in Ico Moon Project == `myfont` then your font files should now have the corresponding name like `myfont.svg`, `myfont.ttf`, `myfont.woff`. If not, you'll need to rename them. 

Now run this app to generate your SASS icon file from the Ico-Moon project file:

     $ sench-ico-moon myfont.json myfont
     Writing _icons-myfont.scss ...

Now copy the 

1. Copy `_icons-myfont.scss` to `resources/sass/_icons-myfont.scss`  
   - Import files must start with an underscore to prevent SASS compiler generating another CSS output file.
2. Add this line to your `resources/sass/app.scss` file after sencha's `@import` commands:
  -	`@import '_icons-myfont.scss'`


