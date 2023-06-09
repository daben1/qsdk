# Copyright (c) 2015 Qualcomm Atheros, Inc..
#
# All Rights Reserved.
# Qualcomm Atheros Confidential and Proprietary.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=qca-wifi-fw
PKG_VERSION:=CNSS.PS.2.5-00006-S-1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)$(BUILD_VARIANT)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=http://vm-cnsswebserv/cnss_win/santaclara/dev01/CNSS.PS.2.5/$(PKG_VERSION)/src
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)$(BUILD_VARIANT)-$(PKG_VERSION)
include $(INCLUDE_DIR)/package-version-override.mk
include $(INCLUDE_DIR)/package.mk

PKG_BUILD_DEPENDS:=

define WifiFirmware
  define Package/$(PKG_NAME)$(1)
    SECTION:=QCA
    CATEGORY:=QCA Proprietary software
    URL:=http://www.qca.qualcomm.com
    MAINTAINER:=Qualcomm Atheros
    TITLE:=QCA Wifi Firmware$(1)
    VARIANT:=$(2)
    PKGARCH:=all
  endef

  define Package/$(PKG_NAME)$(1)/description
    This package contains the qca-wifi firmware($(1)) used in 10.x drivers
  endef

  define Package/$(PKG_NAME)$(1)/config
  $(call Package/$(PKG_NAME)/override_source_path,$(PKG_NAME)$(1))
  $(call Package/$(PKG_NAME)/override_version,$(PKG_NAME)$(1),$(PKG_SUPPORTED_VERSION))
  endef

  define Package/$(PKG_NAME)-hw3-10.4-asic/install
	$(INSTALL_DIR) $$(1)/lib/firmware/$(3)
	$(HOST_TAR) jxvf $(DL_DIR)/$(PKG_SOURCE) -C $(PKG_BUILD_DIR) --strip-components=1
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/athwlan.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/fakeBoardData_AR6004.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/boarddata_0.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/boardData_4_QC98XX_xb241_gld.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/boardData_4_QC98XX_xb243_gld.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/boarddata_0_xb242.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/otp.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/utf.bin $$(1)/lib/firmware/$(3)
  endef

  define Package/$(PKG_NAME)-hw6-10.4-asic/install
	$(INSTALL_DIR) $$(1)/lib/firmware/$(3)
	$(HOST_TAR) jxvf $(DL_DIR)/$(PKG_SOURCE) -C $(PKG_BUILD_DIR) --strip-components=1
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/athwlan.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/atf.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/lteu.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/fakeBoardData_AR6004.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/boardData_2_QC98XX_xb143_gld.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/boardData_3_QC98XX_xb141_gld.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/boardData_2_QC98XX_cus223_523_gld.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/boardData_3_QC98XX_cus261_gld.bin $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/otp.bin  $$(1)/lib/firmware/$(3)
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/utf.bin $$(1)/lib/firmware/$(3)
  endef
  $$(eval $$(call BuildPackage,$(PKG_NAME)$(1)))
endef

Build/Prepare=true
Build/Compile=true

$(eval $(call WifiFirmware,-hw3-10.4-asic,-AR9887_hw_1,AR9887))
$(eval $(call WifiFirmware,-hw6-10.4-asic,-AR9888_hw_2,AR9888/hw.2))
