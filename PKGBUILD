# Maintainer: Aaron Esau <moome@arinerron.com>
pkgname="moome-server"
pkgver="1.0"
pkgrel="1"
license=("GPL")
arch=("i686" "x86_64")
md5sums=("SKIP")
url="https://github.com/BlackberryCode/moome-server"
pkgdesc="a server for the Moome client"
source=("${pkgname}-${pkgver}::git+https://github.com/BlackberryCode/moome-server.git#branch=main")
makedepends=("jdk-openjdk" "java-environment-common")
depends=("java-runtime-common")

rinstall() {
    if [ -f "$1" ]; then
        install -D "$1" "$2/" "$3" "$4"
        return 0
    fi

    for file in $(find "$1" -type f -printf '%P\n'); do
        install -D "$1/$file" "$2/$file" "$3" "$4"
    done

    return 0
}

prepare() {
    # pre_build

    cd "${srcdir}/${pkgname}-${pkgver}"
    
}

build() {
    # build

    #cd "${srcdir}/${pkgname}-${pkgver}"
    cd "${srcdir}/${pkgname}-${pkgver}"
    ./compile.sh
}

check() {
    # post_build

    cd "${srcdir}/${pkgname}-${pkgver}"
    
}

package() {
    # ensure target directories exist
    mkdir -p "$pkgdir/usr/bin"
    mkdir -p "$pkgdir/usr/share/moome-server"
    
    # copy files over and change perms
    install "${srcdir}/${pkgname}-${pkgver}/src/_run.sh" "${pkgdir}/usr/bin/moome-server" --mode=755 --owner="root" --group="root"
    rinstall "${srcdir}/${pkgname}-${pkgver}/src" "${pkgdir}/usr/share/moome-server" --mode=755 --owner="root" --group="root"
}
