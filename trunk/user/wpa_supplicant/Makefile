SRC_NAME=wpa_supplicant-2.10
SRC_URL=http://w1.fi/releases/wpa_supplicant-2.10.tar.gz

CFLAGS += -ffunction-sections -fdata-sections
LDFLAGS += -Wl,--gc-sections


all: download_test extract_test config_test
	$(MAKE) -C $(SRC_NAME)/wpa_supplicant

download_test:
	( if [ ! -f $(SRC_NAME).tar.gz ]; then \
		wget -t5 --timeout=20 --no-check-certificate -O $(SRC_NAME).tar.gz $(SRC_URL); \
	fi )

extract_test:
	( if [ ! -d $(SRC_NAME) ]; then \
		tar -xf $(SRC_NAME).tar.gz; \
	fi )

config_test:
	cp -f config.def $(SRC_NAME)/wpa_supplicant/.config
ifeq ($(CONFIG_FIRMWARE_INCLUDE_EAP_PEAP),y)
	echo CONFIG_EAP_TTLS=y >> $(SRC_NAME)/wpa_supplicant/.config
	echo CONFIG_EAP_PEAP=y >> $(SRC_NAME)/wpa_supplicant/.config
	echo CONFIG_EAP_MSCHAPV2=y >> $(SRC_NAME)/wpa_supplicant/.config
else ifeq (,$(wildcard $(STAGEDIR)/lib/pkgconfig/openssl.pc))
	echo CONFIG_TLS=internal >> $(SRC_NAME)/wpa_supplicant/.config
	echo CONFIG_CRYPTO=internal >> $(SRC_NAME)/wpa_supplicant/.config
	echo CONFIG_INTERNAL_LIBTOMMATH=y >> $(SRC_NAME)/wpa_supplicant/.config
	echo CONFIG_INTERNAL_RC4=y >> $(SRC_NAME)/wpa_supplicant/.config
endif

clean:
	$(MAKE) -C $(SRC_NAME)/wpa_supplicant clean

romfs:
	$(ROMFSINST) $(SRC_NAME)/wpa_supplicant/wpa_cli /usr/sbin/wpa_cli
	$(ROMFSINST) $(SRC_NAME)/wpa_supplicant/wpa_supplicant /usr/sbin/wpa_supplicant
