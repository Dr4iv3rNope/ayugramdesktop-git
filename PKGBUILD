pkgname=ayugram-git
pkgver=1.1.4
pkgrel=1
pkgdesc='Desktop Telegram client with Ghost mode.'
arch=('x86_64')
url="https://github.com/AyuGram/AyuGramDesktop"
license=('GPL3')
depends=('hunspell' 'ffmpeg' 'hicolor-icon-theme' 'lz4' 'minizip' 'openal' 'ttf-opensans'
         'qt6-imageformats' 'qt6-svg' 'qt6-wayland' 'xxhash'
         'rnnoise' 'pipewire' 'libxtst' 'libxrandr' 'jemalloc' 'abseil-cpp' 'libdispatch'
         'openssl-1.1' 'protobuf' 'boost-libs')
makedepends=('cmake' 'git' 'ninja' 'python' 'range-v3' 'tl-expected' 'microsoft-gsl' 'meson'
             'extra-cmake-modules' 'wayland-protocols' 'plasma-wayland-protocols' 'libtg_owt'
             'gobject-introspection' 'mm-common')
optdepends=('webkit2gtk: embedded browser features'
            'xdg-desktop-portal: desktop integration')
provides=("ayugram")
conflicts=("ayugram")
source=("tdesktop::git+https://github.com/AyuGram/AyuGramDesktop.git"
        "telegram-desktop-libtgvoip::git+https://github.com/telegramdesktop/libtgvoip.git"
        "telegram-desktop-GSL::git+https://github.com/desktop-app/GSL.git"
        "telegram-desktop-xxHash::git+https://github.com/Cyan4973/xxHash.git"
        "telegram-desktop-rlottie::git+https://github.com/desktop-app/rlottie.git"
        "telegram-desktop-lz4::git+https://github.com/lz4/lz4.git"
        "telegram-desktop-lib_crl::git+https://github.com/desktop-app/lib_crl.git"
        "telegram-desktop-lib_rpl::git+https://github.com/desktop-app/lib_rpl.git"
        "telegram-desktop-lib_base::git+https://github.com/desktop-app/lib_base.git"
        "telegram-desktop-codegen::git+https://github.com/desktop-app/codegen.git"
        "telegram-desktop-lib_ui::git+https://github.com/AyuGram/lib_ui.git"
        "telegram-desktop-lib_lottie::git+https://github.com/desktop-app/lib_lottie.git"
        "telegram-desktop-lib_tl::git+https://github.com/AyuGram/lib_tl.git"
        "telegram-desktop-lib_spellcheck::git+https://github.com/desktop-app/lib_spellcheck.git"
        "telegram-desktop-lib_storage::git+https://github.com/desktop-app/lib_storage.git"
        "telegram-desktop-cmake::git+https://github.com/desktop-app/cmake_helpers.git"
        "telegram-desktop-expected::git+https://github.com/TartanLlama/expected.git"
        "telegram-desktop-QR::git+https://github.com/nayuki/QR-Code-generator.git"
        "telegram-desktop-lib_qr::git+https://github.com/desktop-app/lib_qr.git"
        "telegram-desktop-hunspell::git+https://github.com/hunspell/hunspell.git"
        "telegram-desktop-range-v3::git+https://github.com/ericniebler/range-v3.git"
        "telegram-desktop-fcitx-qt5::git+https://github.com/fcitx/fcitx-qt5.git"
        "telegram-desktop-nimf::git+https://github.com/hamonikr/nimf.git"
        "telegram-desktop-hime::git+https://github.com/hime-ime/hime.git"
        "telegram-desktop-fcitx5-qt::git+https://github.com/fcitx/fcitx5-qt.git"
        "telegram-desktop-lib_webrtc::git+https://github.com/desktop-app/lib_webrtc.git"
        "telegram-desktop-tgcalls::git+https://github.com/TelegramMessenger/tgcalls.git"
        "telegram-desktop-lib_webview::git+https://github.com/desktop-app/lib_webview.git"
        "telegram-desktop-jemalloc::git+https://github.com/jemalloc/jemalloc.git"
        "telegram-desktop-dispatch::git+https://github.com/apple/swift-corelibs-libdispatch.git"
        "telegram-desktop-plasma-wayland-protocols::git+https://github.com/KDE/plasma-wayland-protocols.git"
        "telegram-desktop-wayland-protocols::git+https://github.com/gitlab-freedesktop-mirrors/wayland-protocols.git"
        "telegram-desktop-kimageformats::git+https://github.com/KDE/kimageformats.git"
        "telegram-desktop-kcoreaddons::git+https://github.com/KDE/kcoreaddons.git"
        "telegram-desktop-cld3::git+https://github.com/google/cld3.git"
        "cppgir::git+https://gitlab.com/mnauw/cppgir.git"
        "cppgir-expected-lite::git+https://github.com/martinmoene/expected-lite.git"
        "https://download.gnome.org/sources/glibmm/2.77/glibmm-2.77.0.tar.xz"
        "fix-arch-linux-desktop-portal.patch"
        "no-ayusync.patch"
        "workaround-for-dbusactivatable.patch"
        "qt_scale_factor-fix.patch_"
)
sha512sums=('SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP')

prepare() {
    #
    # Applying custom patches
    #
    for patch_filepath in *.patch; do
        echo "Applying patch $patch_filepath"

        patch -i $patch_filepath -u -p0 -N -r- || true
    done

    if [[ $PATCH_QT_SCALING -eq 1 ]]; then
        echo "Applying QT_SCALE_FACTOR patch!"

        patch -i qt_scale_factor-fix.patch_ -u -p0 -N -r- || true
    fi

    #
    # Patch end
    #

    cd "$srcdir/tdesktop"
    git submodule init
    git config submodule.Telegram/ThirdParty/libtgvoip.url "$srcdir/telegram-desktop-libtgvoip"
    git config submodule.Telegram/ThirdParty/GSL.url "$srcdir/telegram-desktop-GSL"
    git config submodule.Telegram/ThirdParty/xxHash.url "$srcdir/telegram-desktop-xxHash"
    git config submodule.Telegram/ThirdParty/rlottie.url "$srcdir/telegram-desktop-rlottie"
    git config submodule.Telegram/ThirdParty/lz4.url "$srcdir/telegram-desktop-lz4"
    git config submodule.Telegram/lib_crl.url "$srcdir/telegram-desktop-lib_crl"
    git config submodule.Telegram/lib_rpl.url "$srcdir/telegram-desktop-lib_rpl"
    git config submodule.Telegram/lib_base.url "$srcdir/telegram-desktop-lib_base"
    git config submodule.Telegram/codegen.url "$srcdir/telegram-desktop-codegen"
    git config submodule.Telegram/lib_ui.url "$srcdir/telegram-desktop-lib_ui"
    git config submodule.Telegram/lib_lottie.url "$srcdir/telegram-desktop-lib_lottie"
    git config submodule.Telegram/lib_tl.url "$srcdir/telegram-desktop-lib_tl"
    git config submodule.Telegram/lib_spellcheck.url "$srcdir/telegram-desktop-lib_spellcheck"
    git config submodule.Telegram/lib_storage.url "$srcdir/telegram-desktop-lib_storage"
    git config submodule.cmake.url "$srcdir/telegram-desktop-cmake"
    git config submodule.Telegram/ThirdParty/expected.url "$srcdir/telegram-desktop-expected"
    git config submodule.Telegram/ThirdParty/QR.url "$srcdir/telegram-desktop-QR"
    git config submodule.Telegram/lib_qr.url "$srcdir/telegram-desktop-lib_qr"
    git config submodule.Telegram/ThirdParty/hunspell.url "$srcdir/telegram-desktop-hunspell"
    git config submodule.Telegram/ThirdParty/range-v3.url "$srcdir/telegram-desktop-range-v3"
    git config submodule.Telegram/ThirdParty/fcitx-qt5.url "$srcdir/telegram-desktop-fcitx-qt5"
    git config submodule.Telegram/ThirdParty/nimf.url "$srcdir/telegram-desktop-nimf"
    git config submodule.Telegram/ThirdParty/hime.url "$srcdir/telegram-desktop-hime"
    git config submodule.Telegram/ThirdParty/fcitx5-qt.url "$srcdir/telegram-desktop-fcitx5-qt"
    git config submodule.Telegram/lib_webrtc.url "$srcdir/telegram-desktop-lib_webrtc"
    git config submodule.Telegram/ThirdParty/tgcalls.url "$srcdir/telegram-desktop-tgcalls"
    git config submodule.Telegram/lib_webview.url "$srcdir/telegram-desktop-lib_webview"
    git config submodule.Telegram/ThirdParty/jemalloc.url "$srcdir/telegram-desktop-jemalloc"
    git config submodule.Telegram/ThirdParty/dispatch.url "$srcdir/telegram-desktop-dispatch"
    git config submodule.Telegram/ThirdParty/plasma-wayland-protocols.url "$srcdir/telegram-desktop-plasma-wayland-protocols"
    git config submodule.Telegram/ThirdParty/wayland-protocols.url "$srcdir/telegram-desktop-wayland-protocols"
    git config submodule.Telegram/ThirdParty/kimageformats.url "$srcdir/telegram-desktop-kimageformats"
    git config submodule.Telegram/ThirdParty/kcoreaddons.url "$srcdir/telegram-desktop-kcoreaddons"
    git config submodule.Telegram/ThirdParty/cld3.url "$srcdir/telegram-desktop-cld3"
    git -c protocol.file.allow=always submodule update

    cd "$srcdir/tdesktop/cmake"
    git submodule init
    git config submodule.external/glib/cppgir.url "$srcdir/cppgir"
    git -c protocol.file.allow=always submodule update

    cd "$srcdir/tdesktop/cmake/external/glib/cppgir"
    git submodule init
    git config submodule.expected-lite.url "$srcdir/cppgir-expected-lite"
    git -c protocol.file.allow=always submodule update
}

build() {
    # Telegram is using unstable glibmm, so we need to compile it
    meson setup -D maintainer-mode=true --default-library static --prefix "$srcdir/glibmm" glibmm-2.77.0 glibmm-build
    meson compile -C glibmm-build
    meson install -C glibmm-build

    cd "$srcdir/tdesktop"

    export PKG_CONFIG_PATH='/usr/lib/ffmpeg4.4/pkgconfig:$srcdir/glibmm/lib/pkgconfig'
    cmake \
        -B build \
        -G Ninja \
        -DCMAKE_INSTALL_PREFIX="/usr" \
        -DCMAKE_PREFIX_PATH="$srcdir/glibmm" \
        -DCMAKE_BUILD_TYPE=Release \
        -DTDESKTOP_API_ID=2040 \
        -DTDESKTOP_API_HASH=b18441a1ff607e10a989891a5462e627 \
        -DDESKTOP_APP_DISABLE_AUTOUPDATE=True \
        -DDESKTOP_APP_DISABLE_X11_INTEGRATION=True \
        -DDESKTOP_APP_DISABLE_WAYLAND_INTEGRATION=True
    # Use Qt5 for the time being until kwayland has an easier way to work with Qt6.
    ninja -C build
}

package() {
    cd "$srcdir/tdesktop"
    DESTDIR=$pkgdir ninja -C build install
}
