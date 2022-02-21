#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# This feed is an adaptation of https://github.com/ulli-kroll/rtw88-usb/issues/6

include $(TOPDIR)/rules.mk

PKG_NAME:=morrownr-8821cu
PKG_RELEASE:=2

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=

PKG_SOURCE_URL:=https://github.com/morrownr/8821cu-20210118.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=76c4656cdc460ad47555851b672ea430fddc662b

# PKG_MAINTAINER:=
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/morrownr-8821cu
  SUBMENU:=Wireless Drivers
  TITLE:=Realtek 8821cu's morrownr version
   DEPENDS:=+kmod-cfg80211 +kmod-mac80211 +kmod-usb-core +rtl8821ce-firmware +rtl8822be-firmware +rtl8822ce-firmware +@DRIVER_11N_SUPPORT +@DRIVER_11AC_SUPPORT
  FILES:=\
	$(PKG_BUILD_DIR)/rtw88_pci.ko \
	$(PKG_BUILD_DIR)/rtw88_usb.ko \
	$(PKG_BUILD_DIR)/rtw88_core.ko \
	$(PKG_BUILD_DIR)/rtw88_8822cu.ko \
	$(PKG_BUILD_DIR)/rtw88_8822ce.ko \
	$(PKG_BUILD_DIR)/rtw88_8822c.ko \
	$(PKG_BUILD_DIR)/rtw88_8822b.ko \
	$(PKG_BUILD_DIR)/rtw88_8822be.ko \
	$(PKG_BUILD_DIR)/rtw88_8822bu.ko \
	$(PKG_BUILD_DIR)/rtw88_8723d.ko \
	$(PKG_BUILD_DIR)/rtw88_8723de.ko \
	$(PKG_BUILD_DIR)/rtw88_8821c.ko \
	$(PKG_BUILD_DIR)/rtw88_8821cu.ko
  AUTOLOAD:=$(call AutoProbe, rtw88_8821cu)
endef

define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(LINUX_DIR)" \
		$(KERNEL_MAKE_FLAGS) \
		M="$(PKG_BUILD_DIR)" \
		modules
endef

$(eval $(call KernelPackage,morrownr-8821cu))
