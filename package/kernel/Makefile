# 
# Copyright (C) 2006 OpenWrt.org
# Copyright (C) 2010,2011 NDM Systems
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=kernel

PKG_BUILD_DIR:=$(KERNEL_BUILD_DIR)/packages
SCAN_DEPS=modules/*.mk

include $(INCLUDE_DIR)/package.mk
ifeq ($(DUMP),)
  -include $(LINUX_DIR)/.config
  NF_KMOD:=1
  include $(INCLUDE_DIR)/netfilter.mk
endif
  
define Build/Prepare
	mkdir -p $(PKG_BUILD_DIR)
endef

define Build/Configure
endef

define Build/Compile
endef

#CONFIG_PACKAGE_kernel=y
define Package/kernel
  SECTION:=sys
  CATEGORY:=Kernel
  DEFAULT:=y
  TITLE:=Virtual kernel package
  VERSION:=$(LINUX_VERSION)-$(BOARD)-$(LINUX_RELEASE)
endef

define Package/kernel/install
  # nothing to do
endef

$(eval $(if $(DUMP),,$(call BuildPackage,kernel)))

#include $(TOPDIR)/target/linux/*/modules.mk
include ./modules/*.mk
