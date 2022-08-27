ROOTDIR=../../..
SRC_NAME=squashfs-tools-4.5.1
SRC_ARCHIVE_SUFFIX=tar.gz
SRC_URL=https://github.com/plougher/squashfs-tools/archive/refs/tags/4.5.1.tar.gz

all: download_test extract_test
	sed -i '/^SRC_NAME1=*/cSRC_NAME1=$(SRC_NAME)/squashfs-tools' $(ROOTDIR)/trunk/tools/mksquashfs_xz/Makefile

download_test:
	( if [ ! -f $(SRC_NAME).$(SRC_ARCHIVE_SUFFIX) ]; then \
		wget -t5 --timeout=20 --no-check-certificate -O $(SRC_NAME).$(SRC_ARCHIVE_SUFFIX) $(SRC_URL); \
	fi )

extract_test:
	( if [ ! -d $(ROOTDIR)/trunk/tools/mksquashfs_xz/$(SRC_NAME) ]; then \
		tar -xzf $(SRC_NAME).$(SRC_ARCHIVE_SUFFIX) -C $(ROOTDIR)/trunk/tools/mksquashfs_xz; \
	fi )
