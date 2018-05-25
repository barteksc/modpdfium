# modpdfium
Instructions for building Pdfium from tag _android-7.1.2_r36_ with modified makefiles.
This library is used by [PdfiumAndroid](https://github.com/barteksc/PdfiumAndroid).

## How to build?
I recommend building on Linux (virtual machine will suffice),
because Windows is officially not supported and there are many problems on newer versions of OS X.

You will need about 60 GB of free space.

* install git
* install OpenJDK 8
* install [repo](https://source.android.com/setup/build/downloading)
* `$ mkdir ~/android_src && cd ~/android_src` or select any other path
* `$ repo init --depth=1 -u https://android.googlesource.com/platform/manifest -b android-7.1.2_r36`

  (detailed description available [here](https://source.android.com/source/downloading.html))
* `$ repo sync -c -j 6` and wait...
* clone this repo (or download zip with its content)
* replace makefiles in `~/android_src` with corresponding makefiles from this repo
* apply the fixes for [barteksc/AndroidPdfViewer#253](https://github.com/barteksc/AndroidPdfViewer/issues/253) described [here](https://issuetracker.google.com/issues/37131979#comment16)
* `$ source build/envsetup.sh`
* `$ cd external/pdfium/fpdfsdk`
* `$ lunch` and select architecture
* `$ mma -j 6` and wait ~5 minutes
* library is available in `~/android_src/out/target/product/generic*/obj/lib/libmod*.so`, copy it somewhere
* `$ rm -r ~/android_src/out` before next build

It worked for me, on a Ubuntu 16.04.4 64-bit VM I got from [OSBoxes](https://www.osboxes.org/ubuntu/). Just had to configure apt and install git/JDK.
