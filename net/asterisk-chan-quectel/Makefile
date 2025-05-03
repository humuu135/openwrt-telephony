#
# asterisk-chan-quectel - OpenWRT package (Makefile only, source from GitHub)
#
include $(TOPDIR)/rules.mk

PKG_NAME:=asterisk-chan-quectel
PKG_VERSION:=2024.06.15
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/RoEdAl/asterisk-chan-quectel.git
PKG_SOURCE_VERSION:=5552c365bfb319eed7cbbf6300a67028ab70db9e

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=COPYRIGHT.txt LICENSE.md

MODULES_DIR:=/usr/lib/asterisk/modules

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk
 
define Package/asterisk-chan-quectel
  SUBMENU:=Telephony
  SECTION:=net
  CATEGORY:=Network
  URL:=http://github.com/RoEdAl/asterisk-chan-quectel
  DEPENDS:=asterisk +alsa-lib +libsqlite3
  EXTRA_DEPENDS:=kmod-usb2 kmod-usb-acm kmod-usb-serial kmod-usb-serial-option kmod-usb-audio usb-modeswitch
  TITLE:=Quectel module support
endef
 
define Package/asterisk-chan-quectel/description
  Asterisk channel driver for Quectel and SimCOM modules.
endef

define Package/asterisk-chan-quectel/conffiles
/etc/asterisk/quectel.conf
endef

define Package/asterisk-chan-quectel/install
  $(INSTALL_DIR) $(1)/etc/asterisk
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/ipkg-install/etc/asterisk/quectel.conf $(1)/etc/asterisk
	$(INSTALL_DIR) $(1)$(MODULES_DIR)
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipkg-install/$(MODULES_DIR)/chan_quectel.so $(1)$(MODULES_DIR)
endef

define Package/asterisk-chan-quectel/postinst
#!/bin/sh
if [ -z "$${IPKG_INSTROOT}" ]; then
  echo
  echo 'o-------------------------------------------------------------------o'
  echo '| asterisk-chan-quectel notes                                       |'
  echo 'o-------------------------------------------------------------------o'
  echo '| Adding the "asterisk" user to the "dialout" group might be        |'
  echo '| required for Asterisk to be able to access the module.            |'
  echo 'o-------------------------------------------------------------------o'
  echo '| Adding the "asterisk" user to the "audio" group might be          |'
  echo '| required for Asterisk to be able to access the audio device.      |'
  echo 'o-------------------------------------------------------------=^_^=-o'
  echo
fi
exit 0
endef
 
$(eval $(call BuildPackage,asterisk-chan-quectel))

