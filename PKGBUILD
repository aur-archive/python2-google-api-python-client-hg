# Author : wxg

pkgname=python2-google-api-python-client-hg
pkgver=632.98bac11c0c1c
pkgrel=2
pkgdesc="Google API Client for Python"
url="http://code.google.com/p/google-api-python-client/"
arch=('any')
license=('APACHE')
depends=('hgsvn' 'python2' 'python2-httplib2' 'python2-gflags' 'python-simplejson')
makedepends=('python2-distribute')
provides=('python2-google-api-python-client')
conflicts=('python2-google-api-python-client')
source=("google-api-python-client::hg+https://code.google.com/p/google-api-python-client/" "goagent.patch")

pkgver() {
  cd google-api-python-client/
  hg identify -ni | awk 'BEGIN{OFS=".";} {print $2,$1}'
}

build() {
  echo 'goagent.patch just for goagent proxy. do you use it?(y/N)'
  read SELECT
  if [ "$SELECT" = 'y' ]; then
    cd google-api-python-client/
    patch 'apiclient/http.py' ../goagent.patch
  fi
}

package() {
  cd google-api-python-client/
  python2 setup.py install --prefix=/usr --root="$pkgdir" || return 1
}

md5sums=('SKIP' '4160a8ed3a47d7df649c4142db095a46')