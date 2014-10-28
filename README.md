# ReadiumJS Viewer for Firefox
This project implements the ReadiumJS Viewer as a Firefox add-on. (@danielweck and others started another implementation which we didn't notice before starting this - https://github.com/readium/readium-js-viewer/tree/feature/firefox-addon/firefox-addon/lib)

## How it's made:
Using the simplified, web-app only version of Readium from https://github.com/readium/readium-js, this project shuffles things around to create a Firefox add-on by running `cfx xpi` from the Firefox command line tools. For reference, see https://developer.mozilla.org/en-US/Add-ons/SDK/Tutorials/Installation and https://developer.mozilla.org/en-US/Add-ons/SDK/Tutorials/Getting_started. For development, `cfx run` from the root directory and a phantom Firefox browser should open with the extension icon available in the toolbar.


## How it works:
*  Save the readium-js-viewer-firefox.xpi file from this repository. In Firefox, go to the Add-Ons panel, or enter about:addons in the url bar. Click the little gear icon and select 'Install Add-on from file', then select the readiumjs.kpi (FIX) file. You should now see the Readium icon. Have fun!
*  To add e-books, place them in the data/epub_content folder, and update the epub_library.json file to reflect the addition. Then, re-run `cfx xpi` to regenerate the xpi file, and re-add it to Firefox.


## To Do:
* Troubleshoot epub import feature so users don't have to manually add them
    *  Firefox docs recommend storing user preferences in the user profile folder.
    *  Our goal is to copy the imported epub there, store the epub_library.json there, and write the new entry into the json file.
    * However, we've been unsuccessful using various Firefox APIs to access the profile directory. When trying to get 'chrome' privileges in Firefox, we could not figure out how to successfully `require('chrome')` as the documentation shows, since that 'require' is a namespace collision with require.js! Have been hacking on this with @dfairaizl to try to namespace require.js according to its docs but can't get it working yet...
* Use the git submodule instead of manually including the readium-js folder
* Update localized messages.json files to reflect that this is not the Chrome extension or Chrome app version
* Add build task to package the Firefox add-on as an xpi file
* Submit pull request!
* Submit to Firefox


Contributors:
@joemerante, @bigbluehat and @dkurth at the Books in Browsers 2014 Hackathon

