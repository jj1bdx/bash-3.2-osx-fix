# bash-3.2 for OS X 10.9

* 30-APR-2014: Apple has released [OS X bash Update 1.0 – OS X Mavericks](http://support.apple.com/kb/DL1769), the official release bash-3.2.53.

*NOTE: HIGHLY EXPERIMENTAL* when the `import-function` option is enabled. Use the branch `bash-3.2.54-noimport-function` to avoid merging the `import-function` patch.

* See <http://apple.stackexchange.com/questions/146849/how-do-i-recompile-bash-to-avoid-shellshock-the-remote-exploit-cve-2014-6271-an>
* Patch of bash 3.2.54 and `import-function` patch on <https://svnweb.freebsd.org/ports/head/shells/bash/files/extrapatch-import-functions?view=markup&pathrev=369341> merged
* Patch of OOB memory access on `parser-oob-3.2.patch` at <http://seclists.org/oss-sec/2014/q3/712> also merged

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
