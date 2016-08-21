# STK-wiki-theme

A modern and responsive wiki skin for SuperTuxKart.

## Installation
The theme is based on mediawiki, so first of all you'll need to download and setup MediaWiki.

Once mediawiki is ready, you need to copy this skin to the `skins` folder. Now you should have a new folder called `skins/stk-wiki-theme`. Rename that folder to `SuperTuxKart`.

If you want to properly run the SuperTuxKart wiki, you also need to install three mediawiki extensions: [Youtube](https://www.mediawiki.org/wiki/Extension:YouTube), [CSS](https://www.mediawiki.org/wiki/Extension:CSS) and [Purge](https://www.mediawiki.org/wiki/Extension:Purge).

To configure everything as needed for the SuperTuxKart wiki, add the following at the end of `LocalSettings.php`:

```
# Enable the skin
require_once "$IP/skins/SuperTuxKart/SuperTuxKart.php";
$wgDefaultSkin = "SuperTuxKart";
$wgStylePath   = "$wgScriptPath/skins";
$wgLogo        = "$wgStylePath/SuperTuxKart/images/logo.png";
$wgFavicon     = "$wgStylePath/SuperTuxKart/images/favicon.png";

# Enable the extensions (optional)
require_once "$IP/extensions/YouTube/YouTube.php";
require_once "$IP/extensions/CSS/CSS.php";
require_once "$IP/extensions/Purge/Purge.php";

# Prevent account creation
$wgGroupPermissions['*']['createaccount'] = false;
$wgGroupPermissions['*']['edit'] = false;
$wgGroupPermissions['*']['read'] = true;
$wgGroupPermissions['*']['createtalk'] = false;

# Necessary for e.g. the download page
$wgRawHtml = true; # Not the best solution, but still better than using javascript

# Enable file uploads and also enable svg
$wgEnableUploads = true;
$wgFileExtensions[] = 'svg';
wfLoadExtension( 'ParserFunctions' );
```

## Coding Convetions
 * All stylesheets are written in less, stored in the `css/` folder and included in `supertuxkart.less`.
 * Values such as colors that will be used in multiple location are declared as variables in `css/general.less`
 * All code is indented with 4 spaces
 * Avoid javascript wherever possible
 * Avoid loading resources from external server due to privacy and availability issues
 * All custom fonts are saved in the `fonts` folder in different formats and included using `@font-face`

