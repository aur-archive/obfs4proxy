##	Maintainer: shyokou <shyokou at gmail dot com>
##
pkgname=obfs4proxy
_pkgname=${pkgname%proxy}
pkgver=0.0.5.20150423
pkgrel=1
pkgdesc='A pluggable transport proxy written in Go'
arch=('i686' 'x86_64')
url='https://github.com/Yawning/'${_pkgname}
license=('BSD')
conflicts=('obfs4proxy')
provides=('obfs4proxy')
makedepends=('git' 'go')
optdepends=(
	'tor: you need tor to use this package'
)
source=(
	'git+https://git.torproject.org/pluggable-transports/'${_pkgname}'.git'
)
sha256sums=(
	'SKIP'
)

pkgver()	{
  cd "$srcdir/${_pkgname}"

  ##	tag & date from the last commit
  echo $(git describe --always | sed 's:^'${pkgname}-'::; s:-.*::').$(git log -1 --pretty='%cd' --date=short | tr --delete '-')
}

build()	{
  cd "${srcdir}/${_pkgname}/${pkgname}"

  export GOPATH=~/go
  export GOBIN="."
  go get
  go build
}

package()	{
  cd "${srcdir}/${_pkgname}/${pkgname}"

  #export GOPATH=~/go
  #go install
  install -D -m 0755		"${pkgname}"		"${pkgdir}/usr/bin/${pkgname}"
  install -D -m 0644		"../doc/${pkgname}.1"	"${pkgdir}/usr/share/man/man1/${pkgname}.1"
  install -D -m 0644		"../ChangeLog"		"${pkgdir}/usr/share/doc/${pkgname}/ChangeLog"
  install -D -m 0644		"../LICENSE"		"${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

## vim:set ts=2 sw=2 et:
