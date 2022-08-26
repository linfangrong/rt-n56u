ROOTDIR=../..
SRC_NAME=uClibc-ng-1.0.42
SRC_ARCHIVE_SUFFIX=tar.xz
SRC_URL=https://downloads.uclibc-ng.org/releases/1.0.42/uClibc-ng-1.0.42.tar.xz

all: download_test extract_test

download_test:
	( if [ ! -f $(SRC_NAME).$(SRC_ARCHIVE_SUFFIX) ]; then \
		wget -t5 --timeout=20 --no-check-certificate -O $(SRC_NAME).tar.xz $(SRC_URL); \
	fi )

extract_test:
	( if [ ! -d $(ROOTDIR)/trunk/libc/$(SRC_NAME) ]; then \
		tar -xJf $(SRC_NAME).$(SRC_ARCHIVE_SUFFIX) -C $(ROOTDIR)/trunk/libc; \
	fi )
