#
# Copyright (C) 2011-2013 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=inadyn
PKG_VERSION:=1.99.2-20121212
PKG_RELEASE:=1

PKG_REV:=18e109c1936cc07c6dca16b1ff95fce9d49cd9bb
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://github.com/vampik/inadyn.git
PKG_SOURCE_VERSION:=$(PKG_REV)

include $(INCLUDE_DIR)/package.mk

define Package/inadyn
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=IP Addresses and Names
	TITLE:=a simple and small DDNS client
	URL:=https://github.com/vampik/inadyn
endef

define Package/inadyn/description
 Inadyn is a simple and small DDNS client written in the C language. It can
 maintain multiple host names with the same IP address, and has a web based
 IP detection which runs well behind a NAT router. This is a fork by
 Andrey Tikhomirov.
endef

TARGET_CFLAGS += -Iinclude -DVERSION_STRING=\"$(VERSION)\"

define Package/inadyn/conffiles
/etc/inadyn.conf
endef

define Package/inadyn/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/inadyn $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/K11inadyn $(1)/etc/init.d/K11inadyn
	$(INSTALL_DATA) ./files/inadyn.conf $(1)/etc/inadyn.conf
endef

$(eval $(call BuildPackage,inadyn))
