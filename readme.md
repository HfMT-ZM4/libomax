# libomax

libomax is a helper library for using libo in MaxMSP objects, by John MacCallum.

## Building libomax
# Mac
1. Check out the following repositories (all of the following should be in the same folder):
   * [https://github.com/CNMAT/libo](https://github.com/CNMAT/libo)
   * [https://github.com/CNMAT/libomax](https://github.com/CNMAT/libomax)
   * [https://github.com/Cycling74/max-sdk](https://github.com/Cycling74/max-sdk)
   * [https://github.com/pure-data/pure-data](https://github.com/pure-data/pure-data)
2. Install flex and bison
   * Compiling libo requires flex >2.5 and bison >2.4 to be installed. The OS X developer tools come with older versions of flex and bison which will not work.
   * Download the latest version of flex: [http://flex.sourceforge.net](http://flex.sourceforge.net)
   * Download the latest version of bison: [http://www.gnu.org/software/bison/](http://www.gnu.org/software/bison/)
   * Follow the instructions that come with the source code---it should be the usual `./configure; make; sudo make install`.
   * Be aware that Apple's versions of flex and bison are installed in `/usr/bin` and that the ones you install will likely end up in `/usr/local/bin`, so you will either have to remove Apple's, or adjust your path accordingly.
3. Build `libo`
     1. Add the following lines to your .profile, changing 8 to match the version of your OS
   	    * `MAC_SYSROOT = MacOSX10.8.sdk`      
   	    * `export MAC_SYSROOT`
     2. Execute the following commands at the command line:
   	    * `$ cd <path/to/libo>`
   	    * `$ make`
4. Build libomax
   * `$ cd <path/to/libomax>`
   * `$ make`



# Windows
For building on Windows, we are working on Windows 10, using the MinGW-w64 complier on Cygwin64, with separate tool chains for 32 and 64 bit externals.

### 1. Cygwin64
Down and install Cygwin64, available [here](http://www.cygwin.com/install.html).

The Cygwin installation/setup program allows you to select install packages.

Once you arrive at the `Select Packages` page, set `View` to `Full`, and then search for the following packages. You will need to scroll down to find them sometimes.

select and install the following:
* `make` : The GNU Version of the make utility.
* `gcc` : GNU complier collection
* `mingw64-x86_64-gcc-core` : GGC for Win64 toolchain
* `mingw64-i686-gcc-core` : GGC for Win32 toolchain
* `git` : Distributed version control system
* `wget` : Utility to retrieve files from the WWW via HTTP and FTP
* `flex` : A fast lexical analyzer generator
* `bison` : GNU yacc-compatible parser generator
* `zip` : Info-ZIP compression utility (for making the CNMAT-odot release)

(to select for installation, click the `Skip` icon which should then change to the version number)

On the following page, make sure `select required packages` is enabled.


### 2. GitHub repositories

```
git clone https://github.com/CNMAT/libo
git clone https://github.com/CNMAT/libomax
git clone https://github.com/Cycling74/max-sdk
git clone https://github.com/pure-data/pure-data
```

### 3. libo and libomax

#### libo
To build for Windows 64bit, enter the `libo` directory and do:
```
make win64
```
This will compile the library with the win64 tool chain, and create a `libo.a` file in the `/libo/libs/x86_64` folder.

Then to build the Windows 32bit version of the library do:
```
make clean
make win
```
This will  compile the library with the win64 tool chain, and create a `libo.a` file in the `/libo/libs/i686` folder.

Note we need to `make clean` before building the new version, otherwise the library will be created with the already complied `.o` files.

#### libomax

Then do the same for the `libomax` library: enter the `libomax` directory and do:
```
make win64
```
This will  compile the library with the win64 tool chain, and create a `libomax.a` file in the `/libomax/libs/x86_64` folder.

Then to build the Windows 32bit version of the library do:
```
make clean
make win
```
This will  compile the library with the win64 tool chain, and create a `libomax.a` file in the `/libomax/libs/i686` folder.
