include $(TOPDIR)/rules.mk

PKG_NAME:=whispercpp
PKG_VERSION:=1.8.4
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/ggml-org/whisper.cpp/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=skip
PKG_BUILD_DIR:=$(BUILD_DIR)/whisper.cpp-$(PKG_VERSION)

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/whispercpp
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Telephony
  DEPENDS:=@(aarch64||i386||x86_64) +libstdcpp +libpthread
  TITLE:=Port of OpenAI's Whisper model in C/C++
  URL:=https://github.com/ggml-org/whisper.cpp
endef

define Package/whispercpp/description
 Whisper is a general-purpose speech recognition model.
 Whispercpp is a port of OpenAI's Whisper model in C/C++.
endef

define Package/whispercpp/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/bin/whisper-cli $(1)/usr/bin/whisper-cli
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libggml-base.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libggml-cpu.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libggml.so* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libwhisper.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,whispercpp))
