SHELL := /bin/bash
all: Makefile
	$(MAKE) -f $<
requirements:
	sudo apt install \
	  libv4l-dev libxv-dev libdbus-1-dev \
	  libjpeg-dev libmagickwand-dev \
	  libgtk-3-dev python3-dev python3-setuptools \
	  qtbase5-dev libqt5x11extras5-dev \
	  default-jdk gettext xmlto doxygen \
	  libgirepository1.0-dev gobject-introspection
%: Makefile
	$(MAKE) -f $< $@
Makefile: configure
	./$<
configure:
	autoreconf -vfi
package: ../python3-zbar_0.23.93-8-jc_amd64.deb
../python3-zbar_0.23.93-8-jc_amd64.deb: debian/changelog
	debuild -b -us -uc
	git checkout -- perl/examples/{processor,read_one}.pl
debian/changelog: debian
debian: ../../zbar-0.23.93/debian
	cp -r $< .
	rm -f debian/patches/000[23]*
	sed -i -n '/^0001/p' debian/patches/series
	@echo Must update debian/changelog before continuing >&2
	false
pkginstall: ../libzbar0t64_*.deb ../python3-zbar_*.deb
	sudo apt install $+
