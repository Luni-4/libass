## Cross Compilation for Windows

To avoid that the Linux libraries conflicts with the cross-compilation of
`libass`, you have to remove their paths from the `PKG_CONFIG_PATH`
environment variable first.

Below you can find a list of commands to cross-compile `libass` for `Windows`.

- Windows 32-bit

        meson build-windows32 \
              --buildtype release \
              -Ddirectwrite=enabled \
              --cross-file cross_mingw_i686.txt
        ninja -C build-windows32


- Windows 64-bit

        meson build-windows64 \
              --buildtype release \
              -Ddirectwrite=enabled \
              --cross-file cross_mingw_x86_64.txt
        ninja -C build-windows64

It is also possible to build a statically-linked library, a DLL that contains 
all of its dependencies inside it.

- Windows 32-bit

        meson build-windows32 \
              --buildtype release \
              -Ddirectwrite=enabled \
              -Ddefault_library=static \
              -Dcompile-statically=true \
              --cross-file cross_mingw_i686.txt
        ninja -C build-windows32


- Windows 64-bit

        meson build-windows64 \
              --buildtype release \
              -Ddirectwrite=enabled \
              -Ddefault_library=static \
              -Dcompile-statically=true \
              --cross-file cross_mingw_x86_64.txt
        ninja -C build-windows64
