#
# Copyright (C) 2008 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# This feed is an adaptation of https://github.com/ulli-kroll/rtw88-usb/issues/6

include $(TOPDIR)/rules.mk

PKG_NAME:=rtw88-usb
PKG_RELEASE:=2

PKG_LICENSE:=GPLv2
PKG_LICENSE_FILES:=

PKG_SOURCE_URL:=https://github.com/ulli-kroll/rtw88-usb.git
PKG_SOURCE_PROTO:=git
# Branch backports to keep usint taskled_init
PKG_SOURCE_VERSION:=55687e7477154a4e8a0d0cd32ee4e1f9669180eb

# PKG_MAINTAINER:=
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/rtw88-usb
  SUBMENU:=Wireless Drivers
  TITLE:=Realtek rtw88-usb head version
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

$(eval $(call KernelPackage,rtw88-usb))
