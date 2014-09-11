## DESCRIPTION

Converts an [*Ico Moon*](https://icomoon.io/app) project file into a SASS file for use in a [*Sencha Touch*](www.sencha.com/products/touch) project.  

Basically I got tied of having to manually re-enter character codes everytime I updated the font file since it's difficult to avoid changing them and the CSS file provide by *Ico Moon* does not work with the SASS `icon()` macro used by Sencha Touch apps.

You can also assign names your icons in your *Ico Moon* project and they become `iconCls` names (with an `ico-` prefix) in your Sencha project.  

## INSTALL

    $ npm install -g sencha-ico-moon 


## USAGE

    $ sencha-ico-moon <icomoon-project>.json <font-name>

## Creating a custom icon font for Sencha Touch using IcoMoon 

I typically replace the standard *pictos* font that come standard with *Sencha Touch* since I can select from a larger set of matching icons at Ico Moon. Every icon you add increases the loading time of your app so in general only select the ones you need.

You can just use the default names given to each icon but I recommend you consider renaming your icons to the **purpose** you're using them for in your app and given them. You can do this in Ico Moon. This will make your iconCls values more readable and then if you want to change the icon later you can select a new one and give it the old name with no change to the rest of your app.  I find I make less errors using this approach. 

To create an icon file for Sencha Touch ...

**Step 1**.  Visit [https://icomoon.io/app](https://icomoon.io/app), create a new Project and select your icons from the many hundreds of free and less free font icons.  

Make sure that you **name your project** using the online *Project Manager* to your font name (`myfont` in this example).  No spaces in the name please*!*    

**Step 2**.Download Project and font ZIP file ... 

Before saving the files I recommend that you reset the codes to start from code 21 ('!') so that they are all printable characters. 

- Save `myfont.zip` 
   - Saved via Font > Download
   - You can reset the codes from here.
- Save ico-moon project: `myfont.json` 
   - Saved via Menu (top left button) > Manage Projects > Download


**Step 3**. Copy your font files into your Sencha Touch project: 

- Create folder called `resources/sass/stylesheets/fonts/myfonts`
- Copy font files in `myfont.zip/fonts/` into this folder.

Your font file names should match your Ico Moon project name. If not, you'll need to rename them. Example: `myfont.svg`, `myfont.ttf`, `myfont.woff`. 


**Step 3**. Run this app to generate your SASS icon file from the Ico-Moon project file:

     $ sencha-ico-moon myfont.json myfont
     Writing _icons-myfont.scss ...

**Step 4**. Copy `_icons-myfont.scss` to `resources/sass/_icons-myfont.scss`
  
**NOTE**: Import files must start with an underscore to prevent SASS compiler generating another CSS output file.


**Step 5**. Add this line to your `resources/sass/app.scss` file after Sencha's `@import` commands:

  -	`@import '_icons-myfont.scss'`

All the icons have a `ico-` prefix to avoid name collisions with other CSS styles.


