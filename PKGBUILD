# Maintainer: David K david.dk949@gmail.com
pkgname=git-tools
pkgver="unknown"
pkgrel=0
pkgdesc="A set of shell scripts to help with the use of git"
arch=('any')
url="https://github.com/dk949/git-tools"
license=('MIT')
depends=('git')
makedepends=('git')
optdepends=('firefox: (Or any other browser) used by open-remote')
provides=(
        'git-cat-old'
        'git-delref'
        'git-get-default'
        'git-goback'
        'git-ignore'
        'git-log-q'
        'git-nuke'
        'git-open-remote'
        'git-remind'
        'git-today'
        'git-view'
        )
backup=()
options=()
install=
source=("git+https://github.com/dk949/$pkgname")
noextract=()
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
    make
}

package() {
    cd "$pkgname"

    make DESTDIR="$pkgdir/" PREFIX="/usr" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
