# 
# Copyright (C) 2007 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 12622 2008-09-18 09:09:19Z aaron $

include $(TOPDIR)/rules.mk

PKG_NAME:=olsrd-mod-actions
PKG_VERSION:=0.6.1
PKG_RELEASE:=1
OLSRD_BUILD_DIR=$(BUILD_DIR)/olsrd-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/olsrd-mod-actions
  TITLE:=OLSR (Optimized Link State Routing) daemon
  TITLE:=A plugin for triggering actions on route changes
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Routing and Redirection
  URL:=http://www.olsr.org/
  MENU:=1
  DEPENDS:=olsrd
endef

define Build/Configure
endef

define Build/Compile
	rm -rf $(PKG_INSTALL_DIR)
	mkdir -p $(PKG_INSTALL_DIR)
	rm -rf $(OLSRD_BUILD_DIR)/lib/actions
	cp -r ./actions $(OLSRD_BUILD_DIR)/lib/actions
	$(MAKE) -C "$(OLSRD_BUILD_DIR)" \
		$(TARGET_CONFIGURE_OPTS) \
		NODEBUG=1 \
		CFLAGS="$(TARGET_CFLAGS) -fPIC" \
		OS="linux" \
		INSTALL_PREFIX="$(PKG_INSTALL_DIR)" \
		LIBDIR="$(PKG_INSTALL_DIR)/usr/lib" \
		SBINDIR="$(PKG_INSTALL_DIR)/usr/sbin/" \
		ETCDIR="$(PKG_INSTALL_DIR)/etc" \
		MANDIR="$(PKG_INSTALL_DIR)/usr/share/man" \
		STRIP="true" \
		INSTALL_LIB="true" \
		SUBDIRS="actions" \
		all libs install install_libs
endef

define Package/olsrd-mod-actions/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/lib/actions/olsrd_actions.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,olsrd-mod-actions))
