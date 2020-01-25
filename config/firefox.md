# Mozilla Firefox

## about:config

`browser.backspace_action`  
What action should be performed when the Backspace key is pressed without having
a text editing element in focus.  
_Default: `2`_  
_Options:_

- `0`: Go back
- `1`: Scroll up
- _Other_: Nothing

`browser.tabs.closeWindowWithLastTab`  
Whether to close a window when its last tab is closed.  
_Default: `true`_  

`browser.urlbar.trimURLs`  
Whether to hide the `http` protocol and `www` subdomain in the address bar.  
_Default: `true`_  

`devtools.webextensions.*`  
Whether to show a WebExtension's tab in the developer tools panel.  
_Default: `true`_  

`layers.acceleration.force-enabled`  
Whether to force-enable GPU-accelerated rendering.  
_Default: `false`_  

`privacy.resistFingerprinting`  
Whether to enable special protections against browser fingerprinting.  
_Default: `false`_  

`ui.key.menuAccessKeyFocuse`  
Whether the ALT key should temporarily show and focus the menu bar.  
_Default: `true`_  

`widget.chrome.allow-gtk-dark-theme`  
Whether to enable the dark variant of your GTK theme (if enabled system-wide).  
_Default: `false`_  

`xpinstall.signatures.required`  
Whether extensions must be signed by Mozilla to be installed. This option might
not be available on your build of Firefox.  
_Default: `true`_  
