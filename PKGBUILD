pkgname='perl-class-date'
pkgver='1.1.10'
pkgrel='1'
pkgdesc="Class::Date - Class for easy date and time manipulation"
arch=('any')
license=('PerlArtistic' 'GPL')
options=('!emptydirs')
depends=('perl')
makedepends=()
url='http://search.cpan.org/dist/Class-Date'
source=("http://search.cpan.org/CPAN/authors/id/D/DL/DLUX/Class-Date-${pkgver}.tar.gz")
md5sums=('d9f305bf7cf5a1ca67354339e2fff5d5')

build() {
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""                 \
      PERL_AUTOINSTALL=--skipdeps                            \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'"     \
      PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
      MODULEBUILDRC=/dev/null

    cd "${srcdir}/Class-Date-$pkgver"
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "${srcdir}/Class-Date-$pkgver"
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {
  cd "${srcdir}/Class-Date-$pkgver"
  make install
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
