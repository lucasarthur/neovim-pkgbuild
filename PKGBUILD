# my own build of neovim with some different options

pkgname=neovim
pkgver=0.10.2
pkgrel=1
pkgdesc='vim-fork focused on extensibility and usability'
arch=('x86_64')
url='https://neovim.io'
license=('Apache-2.0')
makedepends=(cmake git ninja unzip curl)
source=(
  git+https://github.com/neovim/neovim.git#tag=v${pkgver}
  'https://gist.githubusercontent.com/lucasarthur/40184e9ccae8a22d03e2f4da1680c7ea/raw/5d7b6156ca7b6664b7d5e10e6d7aca67fdaa57a0/remove_readonly_delay.patch'
)
b2sums=(
  '1eb8d5f83d6dae10e2845ad44cb5440500d4d37281692f683ccbdd1c82a5fd426d9f2470e1723f7a75c3d7945b3f0ca4f5aaec60f3652c134d21a565df844e09'
  '0caea8429162b2473ee77fc24e9441d4a02687427e7d2a699fe7172b137f3cf57333b646e0ec4a9d70f58836f271129343b28c7d3453912f20c784edc6718cab'
)
options=(!debug)

build() {
  cd ${pkgname}
  git apply ../remove_readonly_delay.patch
  make CMAKE_BUILD_TYPE=Release CMAKE_INSTALL_PREFIX=/usr
}

package() {
  cd ${pkgname}
  make DESTDIR="${pkgdir}" install
}
