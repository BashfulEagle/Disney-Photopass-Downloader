# Disney Photopass Downloader
[logo]: https://raw.githubusercontent.com/schrauger/Disney-Photopass-Downloader/master/images/logo_rectangle_64.png
This repo contains two programs designed to download medium resolution Photopass images. These images are the same ones seen in the built-in slideshow page on the Photopass website. If you want full resolution images, you'll have to actually purchase them, but the medium resolution images are sufficient for facebook.

The first program is a [UserScript](#userscript), which installs to your browser and gives you a couple of links on the Photopass website to download your photos.

Alternatively, the [Python script](#python-linux-script), which currently only runs on Linux, lets you batch download all the photos, and it also saves the files with useful names and sets the proper timestamps.

## UserScript
A UserScript (greasemonkey script) that alters the Photopass page, allowing you to download each photo individually in medium resolution (max 1280 pixels on one edge). It will also save the filename based on the location and date/time that the photo was taken.

### Installation Instructions
The easiest way to install the script is to first have [GreaseMonkey][greasemonkey] ([Firefox][gm_firefox]) or [TamperMonkey][tampermonkey] ([Chrome][tm_chrome], [Safari][tm_safari], [Opera][tm_opera]). If you have those addons installed already, simply [open the script][script] and follow the prompts to install it.

For more detailed steps, [follow these instructions][instructions] for your particular browser.
[greasemonkey]: http://www.greasespot.net/
[gm_firefox]: https://addons.mozilla.org/en-us/firefox/addon/greasemonkey/
[tampermonkey]: https://tampermonkey.net/index.php
[tm_chrome]: https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkf
[tm_safari]: https://tampermonkey.net/index.php?ext=dhdg&browser=safari
[tm_opera]: https://addons.opera.com/en/extensions/details/tampermonkey-beta/
[script]: https://raw.githubusercontent.com/schrauger/Disney-Photopass-Downloader/master/greasemonkey/Photopass_Downloader.user.js
[instructions]: http://stackapps.com/tags/script/info

### How to Use
After the script is installed and enabled, you will see new buttons to download your images. You can download a range of photos (20 at a time), or you can download them all at once.

Each photo will open its own download prompt, so if you have a lot of photos, be prepared to click OK on them all (or set the default action to Download).

| Standard Page  | With Userscript  |
|---|---|
|![Before][before]|![After][after] |

[before]: /images/without_script.png?raw=true "Before script is installed"
[after]: /images/with_script.png?raw=true "After script is installed"

### Known Issues
* Firefox prevents this script from opening more than 20 tabs, even if popups are explicitely allowed for the photopass site.
 * Workaround: Use the range function to download photos 20 at a time. After you save the first 20, increment the range input and click 'Open' to download the next 20.
* Images do not contain date/time EXIF information. This cannot be altered by JavaScript and thus cannot be modified solely with this Greasemonkey script. Try the Linux Python script for those advanced features.
* New versions of Chrome prevent the script from installing.
 * Workaround: Open a new window and go to the url "chrome:extensions". Then drag-and-drop the [script url][script] onto the extensions page, where Chrome will then let you install the script.

## Python Linux Script
Run from a command prompt, this automatically downloads all photos, names them with a date and location filename, and sets both the EXIF timestamp and OS timestamp.

Requires the `jhead` package (for EXIF manipulation).

To run, first copy `sample.config.py` to `config.py`. Fill in your username (email) and password. Then run `python photopass-downloader.py`. It will download all photos to the script folder.
