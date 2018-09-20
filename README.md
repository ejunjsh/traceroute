# traceroute
a traceroute command line from unp, this code just let me pratice the related gcc command.

__Notice: this code only build on macos__

## build share library

    gcc lib/*.c -shared -fPIC -o libunp.so -w

## build static library

    cd lib/
    gcc -c *.c -w
    cd -
    ar rv libunp2.a lib/*.o

## build executable file with share library

    gcc *.c -Ilib/  -o traceroute  -L. -lunp  -w

## build executable file with static library

    gcc *.c -Ilib/  -o traceroute  -L. -lunp2 -w


## run

    # the raw socket need root permission
    sudo ./traceroute www.baidu.com

## check dependencies of executable file

    # use share library
    otool -L traceroute
    traceroute:
            libunp.so (compatibility version 0.0.0, current version 0.0.0)
            /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1252.50.4)

    # use static library
    otool -L traceroute
    traceroute:
            /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1252.50.4)