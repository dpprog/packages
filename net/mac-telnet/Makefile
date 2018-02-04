#
# Copyright (C) 2014-2015 OpenWrt.org
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mac-telnet
PKG_VERSION:=0.0.0
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/dpprog/MAC-Telnet.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=04c83fce71a504fd8257b1d4a8d48a352e1c6929
PKG_SOURCE:=$(PKG_NAME)-$(VERSION)-$(PKG_SOURCE_VERSION).tar.gz

PKG_LICENSE:=GPL-2.0+
PKG_MAINTAINER:=Jo-Philipp Wich <jo@mein.io>

PKG_FIXUP:=libtool autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/mac-telnet/Default
  SECTION:=net
  CATEGORY:=Network
  TITLE:=MAC-Telnet
  DEPENDS:=+librt
endef

define Package/mac-telnet-server
  $(call Package/mac-telnet/Default)
  TITLE+= server
endef

define Package/mac-telnet-client
  $(call Package/mac-telnet/Default)
  TITLE+= client
endef

define Package/mac-telnet-ping
  $(call Package/mac-telnet/Default)
  TITLE+= ping
endef

define Package/mac-telnet-server/install
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mactelnetd $(1)/bin/
endef

define Package/mac-telnet-client/install
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/mactelnet $(1)/bin/
endef

define Package/mac-telnet-ping/install
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/macping $(1)/bin/
endef

$(eval $(call BuildPackage,mac-telnet-server))
$(eval $(call BuildPackage,mac-telnet-client))
$(eval $(call BuildPackage,mac-telnet-ping))
