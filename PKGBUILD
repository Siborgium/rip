pkgname=rip-git
pkgdesc="rip: a safe and ergonomic alternative to rm"
pkgver=0.12.0.r4.e1317cb
pkgrel=1
makedepends=('rust' 'cargo')
arch=('i686' 'x86_64' 'armv6h' 'armv7h')
url="https://github.com/nivekuil/rip"
source=("$pkgname::git+https://github.com/nivekuil/rip")
sha1sums=('SKIP')
license=('GPL-3.0+')

build() {
    cd "$pkgname"
    cargo build --release --locked
}

pkgver() {
    cd "$pkgname"
    local tag=$(git tag --sort=-v:refname | grep '^[0-9]' | head -1)
    local commits_since=$(git rev-list $tag..HEAD --count)
    echo "$tag.r$commits_since.$(git log --pretty=format:'%h' -n 1)"
}

package() {
    cd "$pkgname"
    install -Dm 755 "target/release/rip" "${pkgdir}/usr/bin/rip"
}
