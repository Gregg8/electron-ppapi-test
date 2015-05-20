## Testing Electron's 'ppapi-flash-path' command line switch under Windows

Started off with the demo code in https://github.com/atom/electron/blob/master/docs/tutorial/using-pepper-flash-plugin.md

Modified three things:
 1. Updated the `ppapi-flash-path` path to be `D:\\dev\\electron\\electron-ppapi-test\\pepflashplayer32_17_0_0_188.dll`
      - Copied this file from it's default location (`C:\Windows\SysWOW64\Macromed\Flash`, or could be other locations like `C:\Windows\System32\Macromed\Flash`) into the same folder as the js file, but referred to it using an absolute path.
      - Renamed the Flash dll in the default location so it couldn't be picked up.
 2. Added the braces for `{'plugins': true}` to make it a valid object. Please update the doco.
 3. Made it load `http://taggalaxy.de` as the URL.

On running this with the `electron .` command, it does not work. It explains: "You need a newer Version of the Adobe Flash Player to view the Tag Galaxy Website."

If the `... appendSwitch('ppapi-flash-path' ...` line is commented out and the default DLL renamed back, it works just fine.

Have tried many different combinations of specifying the dll for the `ppapi-flash-path`:
 - `D:/dev/electron/electron-ppapi-test/pepflashplayer32_17_0_0_188.dll`
 - `pepflashplayer32_17_0_0_188.dll`
 - `.\\pepflashplayer32_17_0_0_188.dll`
 - `./pepflashplayer32_17_0_0_188.dll`

but to no avail.

Same issue when I specify this on the command line, with `-ppapi-flash-path=pepflashplayer32_17_0_0_188.dll` etc.
