# Google Chrome

## Extensions / Apps

### Cache problems

If errors manifest in an extension or app, it might be necessary to clear its
cache. Each extension or app stores its cache within the directory:

> `${HOME}/.config/google-chrome/Default/Storage/ext`

Each directory within represents an extension or app, named after its ID. Clear
the cache for the extension or app by removing its directory. The directories
are named by ID; for example, "`hmjkmjkepdijhoojdojkdfohbdgmmhki`" is the ID for
the Google Keep app, so to clear that apps cache you may execute:

````````````````````````````````````````````````````````````````````````````` sh
rm -rf "${HOME}/.config/google-chrome/Default/Storage/ext/hmjkmjkepdijhoojdojkdfohbdgmmhki"
````````````````````````````````````````````````````````````````````````````````
