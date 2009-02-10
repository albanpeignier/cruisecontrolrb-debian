#!/usr/bin/make -f

build:
	@echo "nothing to do"

install:
	cp -a app config daemon lib tasks log public script vendor "${DESTDIR}usr/share/cruisecontrolrb"
	install --mode 644 config/site_config.rb_example ${DESTDIR}etc/cruisecontrolrb/site_config.rb
	install cruise "${DESTDIR}usr/share/cruisecontrolrb"

clean:
	@echo "nothing to do"
