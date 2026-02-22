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
zbar.deb: debian/changelog
	debuild -b
