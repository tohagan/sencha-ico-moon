### DESCRIPTION

Converts an [*Ico Moon*](https://icomoon.io/app) project file into a SASS file for use in a [*Sencha Touch*](www.sencha.com/products/touch) project.  

Basically I got tied of having to manually re-enter character codes everytime I updated the font file since it's difficult to avoid changing them and the CSS file provided by *Ico Moon* does not work with the SASS `icon()` macro used by Sencha Touch apps.

You can also assign names your icons in your *Ico Moon* project and they become `iconCls` names (with an `ico-` prefix) in your Sencha project.  

### INSTALL

    $ npm install -g sencha-ico-moon 

### USAGE

    $ sencha-ico-moon <icomoon-project>.json <font-name>


### EXAMPLE DATA

- **Input**: [myfont.json](https://raw.githubusercontent.com/tohagan/sencha-ico-moon/master/myfont.json) - *Ico Moon Project file*

- **Output**: [_icons-myfont.scss](https://github.com/tohagan/sencha-ico-moon/blob/master/_icons-myfont.scss) - *Sencha Touch SASS icon import file*

### Creating a custom icon font for Sencha Touch using IcoMoon 

I usually replace the *pictos* font that installs with a new *Sencha Touch* project since I can select from a larger set of matching icons at Ico Moon. Just keep in mind that every icon you add increases the loading time of your app.

You can just use the default names given to each icon but I recommend you consider renaming your icons to the *purpose* you're using them for in your app. You can do this online in the Ico Moon project. Then, if you want to change the icon later, you can select a new one and give it the old name with no change to the rest of your app. This will make your `iconCls` values more readable and reduce coding errors.

*To create a set of icon font files for your Sencha Touch app ...*

**Step 1**.  Visit [https://icomoon.io/app](https://icomoon.io/app), create a new Project and rename via the using the online *Project Manager* to your font name (`myfont` in this example).  Must be no spaces in the project name *!*

To navigate to the Project Manager, select the top left drop down menu on the Ico Moon site.  

**Step 2**. Select your icons from the many hundreds of free and less free font icons. When you're ready, select the "Font" button at the bottom and then rename each selected icon to the purpose your using it for in your app. 

**Step 3**. Download both Project and font ZIP file ... 

Before saving the files I recommend that you reset the codes to start from code 21 ('!') so that they are all printable characters. 

- Save `myfont.zip` 
   - Saved via: **Font** > **Download**
   - You can also reset the icon codes before you download here.
- Save ico-moon project: `myfont.json` 
   - Saved via: **Menu** (top left button) > **Manage Projects** > **Download**


**Step 4**. Copy your font files into your Sencha Touch project: 

- Create folder called `resources/sass/stylesheets/fonts/myfonts`
- Copy font files in `myfont.zip/fonts/myfont.*` into this folder.

Your font file names should match your Ico Moon project name. If not, you'll need to rename them. Example: `myfont.svg`, `myfont.ttf`, `myfont.woff`.  (Tip: In Windows 7 you can select ALL the font files (Ctrl-A) then rename them ALL *in one step* by hitting F2 and typing the new name and pressing ENTER). Probably works for Windows 8.


**Step 5**. Run this app to generate your SASS icon file from the Ico-Moon project file:

     $ sencha-ico-moon myfont.json myfont
     Writing _icons-myfont.scss ...

**Step 6**. Copy `_icons-myfont.scss` to `resources/sass/_icons-myfont.scss`
  
**NOTE**: Import files must start with an underscore to prevent SASS compiler generating another CSS output file.


**Step 7**. Add this line to your `resources/sass/app.scss` file after Sencha's `@import` commands:

  -	`@import '_icons-myfont.scss'`

All the icons have an `ico-` prefix to avoid name collisions with other CSS styles.
