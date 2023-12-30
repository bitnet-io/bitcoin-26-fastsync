# requiers gcc-12 to build with bitcoin-26 version minimum

bitcoin staging tree 24.x
===========================



How do I build the software?
----------------------------

The most troublefree and reproducable method of building the repository is via the depends method:

    LINUX

    git clone https://github.com/bitcoin/bitcoin
    cd bitcoin
    cd depends
    make -j12 HOST=x86_64-pc-linux-gnu  # -j12 for 12 cores adjust here
    cd ..
    ./autogen.sh
    CONFIG_SITE=$PWD/depends/x86_64-pc-linux-gnu/share/config.site ./configure --prefix=$PWD/bitcoin-26-shared-linux --disable-tests --disable-bench --disable-fuzz-binary
    make -j12                           # -j12 for 12 cores adjust here
    make -j12 install                   # -j12 for 12 cores adjust here
    files will be placed into bitcoin-26-shared-linux folder

    WINDOWS 64-bit

    git clone https://github.com/bitcoin/bitcoin
    cd bitcoin
    cd depends
    make -j12 HOST=x86_64-w64-mingw32   # -j12 for 12 cores adjust here
    cd ..
    ./autogen.sh # not required when building from tarball
    CONFIG_SITE=$PWD/depends/x86_64-w64-mingw32/share/config.site ./configure --prefix=$PWD/bitcoin-26-shared-windows  --disable-fuzz-binary --disable-bench
    make -j12                           # -j12 for 12 cores adjust here
    make -j12 install                   # -j12 for 12 cores adjust here
    make -j12 deploy                    # for setup.exe adjust 12 cores to your core count requires nsis see doc/build-windows.md for deps


License
-------

bitcoin is released under the terms of the MIT license. See [COPYING](COPYING) for more information or see https://opensource.org/licenses/MIT.

