# bash-3.2 for OS X 10.9

*NOTE: HIGHLY EXPERIMENTAL* when the `import-function` option is enabled. Use the branch `bash-3.2.53-noimport-function` to avoid merging the `import-function` patch.


* See <http://apple.stackexchange.com/questions/146849/how-do-i-recompile-bash-to-avoid-shellshock-the-remote-exploit-cve-2014-6271-an>
* Patch of bash 3.2.53 and `import-function` patch on <https://svnweb.freebsd.org/ports/head/shells/bash/files/extrapatch-import-functions?view=markup&pathrev=369341> merged

## How to build

        cd bash-92
        xcodebuild
        # check versions
        cd build/Release
        ./bash --version # GNU bash, version 3.2.53(1)-release
        ./sh --version   # GNU bash, version 3.2.53(1)-release
        # install
        sudo cp -p /bin/sh /bin/sh.OLD # BE CAREFUL 
        sudo cp -p /bin/bash /bin/bash.OLD # BE CAREFUL 
        sudo install -o root -g wheel -m 0555 -c ./bash /bin/bash
        sudo install -o root -g wheel -m 0555 -c ./sh /bin/sh

## Check script

If you see a date in the output of that command your `bash` or `sh` is vulnerable.

        rm -f echo
        env X='() { (a)=>\' sh -c "echo date"; cat echo

