ROOTDIR=../../..
SRC_NAME=xz-5.2.6
SRC_ARCHIVE_SUFFIX=tar.xz
SRC_URL=https://tukaani.org/xz/xz-5.2.6.tar.xz

all: download_test extract_test
	sed -i '/^SRC_NAME2=*/cSRC_NAME2=$(SRC_NAME)' $(ROOTDIR)/trunk/tools/mksquashfs_xz/Makefile

download_test:
	( if [ ! -f $(SRC_NAME).$(SRC_ARCHIVE_SUFFIX) ]; then \
		wget -t5 --timeout=20 --no-check-certificate -O $(SRC_NAME).$(SRC_ARCHIVE_SUFFIX) $(SRC_URL); \
	fi )

extract_test:
	( if [ ! -d $(ROOTDIR)/trunk/libc/$(SRC_NAME) ]; then \
		tar -xJf $(SRC_NAME).$(SRC_ARCHIVE_SUFFIX) -C $(ROOTDIR)/trunk/tools/mksquashfs_xz; \
	fi )
