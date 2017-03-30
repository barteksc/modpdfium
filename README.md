# modpdfium
Instructions for building Pdfium from tag _android-7.1.1_r28_ with modified makefiles.
This library is used by [PdfiumAndroid](https://github.com/barteksc/PdfiumAndroid).

## How to build?
I recommend building on Linux (virtual machine will suffice),
because Windows is officially not supported and there are many problems on newer versions of OS X.

You will need about 60 GB of free space.

* install OpenJDK 8
* `$ mkdir ~/android_src && cd ~/android_src` or select any other path
* `$ repo init -u https://android.googlesource.com/platform/manifest -b android-7.1.1_r28`

  (detailed description available [here](https://source.android.com/source/downloading.html))
* `$ repo sync` and wait...
* clone this repo (or download zip with its content)
* replace makefiles in `~/android_src` with corresponding makefiles from this repo
* `$ cd ~/android_src`
* `$ source build/envsetup.sh`
* `$ cd external/pdfium/fpdfsdk`
* `$ lunch` and select architecture
* `$ mma` and wait ~5 minutes
* library is available in `~/android_src/out/target/product/generic*/obj/lib/libmod*.so`, copy it somewhere
* `$ rm -r ~/android_src/out` before next build

It worked for me, but if doesn't work for you, try installing additional packages listed [here](https://github.com/barteksc/modpdfium/issues/1#issuecomment-259838427).
