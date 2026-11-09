# Maintainer: David K dk949.david@gmail.com
_pkgname=git-tools
pkgname="${_pkgname}-949sd"
pkgver="unknown"
pkgrel=0
pkgdesc="A set of shell scripts to help with the use of git"
arch=('any')
url="https://github.com/dk949/$_pkgname"
license=('MIT')
depends=(
        'awk'
        'coreutils'
        'git'
        'grep'
        'ncurses'
        'sed'
        'sh'
        )
makedepends=('git')
optdepends=('xdg-utils: open the remote in the default browser with git-open-remote (or set BROWSER)')
provides=(
        'git-before'
        'git-cat-old'
        'git-delref'
        'git-get-default'
        'git-log-q'
        'git-nuke'
        'git-open-remote'
        'git-profile'
        'git-remind'
        'git-today'
        'git-view'
        )
source=("$pkgname::git+$url")
md5sums=() #autofill using updpkgsums
sha256sums=('SKIP')

pkgver() {
    ___DATE="$(git -C "$pkgname" log -1 --format='%cd' --date=format:'%F')"
    ___DATE_TIME="$___DATE 00:00"
    ___COMMIT_COUNT=$(git -C "$pkgname" rev-list --count HEAD --since="$___DATE_TIME")
    echo "$(date -d "$___DATE" +'%Y%m%d')_$___COMMIT_COUNT"
    unset ___DATE
    unset ___DATE_TIME
    unset ___COMMIT_COUNT
}

build() {
    cd "$pkgname"
    make -j
}

package() {
    cd "$pkgname"

    make DESTDIR="$pkgdir/" PREFIX="/usr" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
