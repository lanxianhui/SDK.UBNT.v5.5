#
# Copyright (C) 2007-2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# blogic@openwrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=libXxf86vm
PKG_RELEASE:=4
PKG_VERSION:=1.0.2

PKG_SOURCE_URL:=http://xorg.freedesktop.org/releases/X11R7.4/src/lib/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_BUILD_DIR=$(BUILD_DIR)/Xorg/$(_CATEGORY)/$(PKG_NAME)-$(PKG_VERSION)/
PKG_MD5SUM:=304d37bd0a10d9b58aa9b64469ad73e5
PKG_FIXUP:=libtool
PKG_INSTALL:=1
PKG_BUILD_DEPENDS:=xproto xextproto xf86vidmodeproto

include $(INCLUDE_DIR)/package.mk

define Build/Configure
	$(call Build/Configure/Default, \
		--enable-malloc0returnsnull \
	)
endef

define Package/libXxf86vm
  SECTION:=xorg-lib
  CATEGORY:=Xorg
  SUBMENU:=libraries
  DEPENDS:=+libX11 +libXext
  TITLE:=libXxf86vm
  URL:=http://xorg.freedesktop.org/
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.{so*,a,la} \
		$(1)/usr/lib/
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/* \
		$(1)/usr/lib/pkgconfig/
endef

define Package/libXxf86vm/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/*.so* \
		$(1)/usr/lib/
endef

$(eval $(call BuildPackage,libXxf86vm))
