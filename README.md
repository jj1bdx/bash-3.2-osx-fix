# bash-3.2 for OS X 10.9

*NOTE: EXPERIMENTAL:* functions from environment variables are *NOT* imported as default when the `import-functions` option is compiled. The `master` branch has this option enabled, for better security. You can verify the list of valid command options by `bash --help`.

Use the branch `bash-3.2.57-noimport-function` if you want to avoid merging the `import-function` patch.

* See <http://apple.stackexchange.com/questions/146849/how-do-i-recompile-bash-to-avoid-shellshock-the-remote-exploit-cve-2014-6271-an>
* Patch of bash 3.2.54, 3.2.55, 3.2.56, 3.2.57, and `import-function` patch at <https://svnweb.freebsd.org/ports/head/shells/bash/files/extrapatch-import-functions?view=markup&pathrev=369341> are merged

## Apple has released an official patch

* 30-SEP-2014: Apple has released [OS X bash Update 1.0 - OS X Mavericks](http://support.apple.com/kb/DL1769), the official release of bash-3.2.53 for OS X 10.9.x. Updates for Mountain Lion and Lion are also available.

## How to build

        cd bash-92
        xcodebuild
        # check versions
        cd build/Release
        ./bash --version # GNU bash, version 3.2.54(1)-release
        ./sh --version   # GNU bash, version 3.2.54(1)-release
        # install
        sudo cp -p /bin/sh /bin/sh.OLD # BE CAREFUL 
        sudo cp -p /bin/bash /bin/bash.OLD # BE CAREFUL 
        sudo install -o root -g wheel -m 0555 -c ./bash /bin/bash
        sudo install -o root -g wheel -m 0555 -c ./sh /bin/sh

## Check script

If you see the output `Game over`, your `bash` is vulnerable.

        env ls="() { echo 'Game over'; }" bash -c ls

See also <https://github.com/hannob/bashcheck>
