# modpdfium
Modified pdfium library from tag _android-5.1.1_r37_ used for [PdfiumAndroid](https://github.com/barteksc/PdfiumAndroid).
Version 5.1.1 is used because next releases contain additional dependecies.

Added functions from 6.0.1 for finding bookmarks.

## How to build?
I recommend building on Linux (virtual machine will suffice),
because Windows is officially not supported and there are many problems on newer versions of OS X.

You will need about 60 GB of free space.

* install OpenJDK 7
* `$ mkdir ~/android_src && cd ~/android_src` or select any other path
* `$ repo init -u https://android.googlesource.com/platform/manifest -b android-5.1.1_r37`

  (detailed description available [here](https://source.android.com/source/downloading.html))
* `$ repo sync`
* `$ cd external`
* `$ rm -r pdfium`
* `$ git clone https://github.com/barteksc/modpdfium.git pdfium`
* `$ cd ..`
* edit `build/core/version_defaults.mk` and change variable _PLATFORM_SDK_VERSION_ to 9 (not sure if this step is required)
* `$ source build/envsetup.sh`
* `$ cd external/pdfium/fpdfsdk`
* `$ lunch` and select architecture
* `$ mma` and wait ~5 minutes
* library is available in `~/android_src/out/target/product/generic*/obj/lib/libmodpdfium.so`, copy it somewhere
* `$ rm -r ~/android_src/out` before next build

It worked for me, but if doesn't work for you, try detailed instruction [here](https://github.com/barteksc/modpdfium/issues/1#issuecomment-259838427)
