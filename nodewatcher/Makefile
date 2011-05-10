include $(TOPDIR)/rules.mk

PKG_NAME:=nodewatcher
PKG_VERSION:=0.3
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/nodewatcher
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Nodewatcher
  DEPENDS:=+netprofscripts +nodeupgrade +nodewatcher-clients +nodewatcher-watchdog +olsrd-mod-actions +olsrd +iptables +kmod-ipt-core
  TITLE:=Nodewatcher Metapackage
endef

$(eval $(call BuildPackage,nodewatcher))
