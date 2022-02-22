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

PKG_SOURCE_URL:=https://github.com/Pix13/8821cu-20210118.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=2c2b9ae607abd0b9a42c26ac8a79d6e5c15f1fac

# PKG_MAINTAINER:=
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/morrownr-8821cu
  SUBMENU:=Wireless Drivers
  TITLE:=Realtek 8821cu's morrownr version
   DEPENDS:=+@USB_SUPPORT +kmod-cfg80211 +kmod-mac80211 +rtl8821ce-firmware +@DRIVER_11N_SUPPORT +@DRIVER_11AC_SUPPORT
  FILES:=$(PKG_BUILD_DIR)/8821cu.ko
  AUTOLOAD:=$(call AutoProbe,8821cu)
  MODPARAMS:="rtw_drv_log_level=0 rtw_led_ctrl=0 rtw_vht_enable=2 rtw_power_mgnt=1 rtw_beamform_cap=0 rtw_dfs_region_domain=1"
  PROVIDES:=kmod-rtl8821cu
endef

FILTERED_KERNEL_MAKE_FLAGS=$(filter-out KERNELRELEASE=$(LINUX_VERSION),$(KERNEL_MAKE_FLAGS))

MAKE_OPTS:= \
	$(FILTERED_KERNEL_MAKE_FLAGS) \
	SUBDIRS="$(PKG_BUILD_DIR)" \
	PROJECT_DIR="$(PKG_BUILD_DIR)" \
	src="$(PKG_BUILD_DIR)" \
	KSRC="$(LINUX_DIR)" 
	
define Build/Compile
	+$(MAKE) $(PKG_JOBS) -C "$(PKG_BUILD_DIR)" \
		$(MAKE_OPTS) \
		modules
endef

$(eval $(call KernelPackage,morrownr-8821cu))
