# Apache #

## <span class="caps">FAQ</span>/Problems ##

### `CFURLWriteDataAndPropertiesToResource(/System/Library/LaunchDaemons/org.apache.httpd.plist) failed: -10` ###

You somehow called (or something similar)

    $ apachectl stop

expecting it will use the macports installation and run `/opt/local/apache2/bin/apachectl` . Unfortunately the Apache installation of OS X is first in the `PATH`. To control the pre-installed Apache its better to use `System Preferences > Sharing >
Web-Sharing`.