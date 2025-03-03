#
# Copyright (C) 2020-2022 HandsomeMod Project
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=qcom-firmware
PKG_VERSION:=r1034.2.1
PKG_RELEASE:=4

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/sunny-chao/qcom-firmware.git
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_VERSION:=decfb6ac2716fd8b88e861cde0b2187edef2db18
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=sunnychao <sunnychao816@gmail.com>
STRIP:=:

include $(INCLUDE_DIR)/package.mk

define Package/modem-default
  SECTION:=firmware
  CATEGORY:=Firmware
  TITLE:=MSM8916 modem firmware ($(1))
endef

define Package/wcnss-default
  SECTION:=firmware
  CATEGORY:=Firmware
  TITLE:=MSM8916 wifi/bluetooth firmware ($(1))
endef

define Package/nv-default
  SECTION:=firmware
  CATEGORY:=Firmware
  TITLE:=MSM8916 wifi nvmem ($(1))
endef

define Package/nv-install
	$(INSTALL_DIR) $(1)/lib/firmware/wlan/prima
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/$(2)-nv.bin \
		$(1)/lib/firmware/wlan/prima/WCNSS_qcom_wlan_nv.bin
endef

define Package/wcnss-install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/$(2)/wcnss.* \
		$(1)/lib/firmware
endef

define Package/modem-install
	$(INSTALL_DIR) $(1)/lib/firmware
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/$(2)/mba.mbn \
		$(1)/lib/firmware
	$(INSTALL_DATA) \
		$(PKG_BUILD_DIR)/$(2)/modem.* \
		$(1)/lib/firmware
endef

define Package/compile
	mkdir $(PKG_BUILD_DIR)/$(1)
	mcopy -i $(PKG_BUILD_DIR)/$(1)-modem.bin -p -m -v \
		::image/mba.mbn ::image/modem.* ::image/wcnss.* $(PKG_BUILD_DIR)/$(1)
endef

define Build/Compile
	$(call Package/compile,dragonboard)		
	$(call Package/compile,openstick-ufi001b)
	$(call Package/compile,openstick-ufi001c)
	$(call Package/compile,openstick-ufi003)
	$(call Package/compile,openstick-ufi103s)
	$(call Package/compile,openstick-sp970)
	$(call Package/compile,openstick-uz801)
	$(call Package/compile,wt88047)
	$(call Package/compile,wt86047)
	$(call Package/compile,openstick-mf32)
	$(call Package/compile,openstick-mf601)
	$(call Package/compile,openstick-mf601s)
endef

#======================================================================
#  APQ8016

define Package/apq8016-wcnss
  $(call Package/wcnss-default,Dragonboard APQ8016)
endef

define Package/apq8016-wcnss/install
  $(call Package/wcnss-install,$(1),dragonboard)
endef
$(eval $(call BuildPackage,apq8016-wcnss))

define Package/apq8016-nv
  $(call Package/nv-default,Dragonboard APQ8016)
endef

define Package/apq8016-nv/install
  $(call Package/nv-install,$(1),dragonboard)
endef
$(eval $(call BuildPackage,apq8016-nv))

define Package/apq8016-modem
  $(call Package/modem-default,Dragonboard APQ8016)
endef

define Package/apq8016-modem/install
  $(call Package/modem-install,$(1),dragonboard)
endef
$(eval $(call BuildPackage,apq8016-modem))

#======================================================================
#  MF32

define Package/msm8916-mf32-wcnss
  $(call Package/wcnss-default,Openstick MF32)
endef

define Package/msm8916-mf32-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-mf32)
endef
$(eval $(call BuildPackage,msm8916-mf32-wcnss))

define Package/msm8916-mf32-nv
  $(call Package/nv-default,Openstick MF32)
endef

define Package/msm8916-mf32-nv/install
  $(call Package/nv-install,$(1),openstick-mf32)
endef
$(eval $(call BuildPackage,msm8916-mf32-nv))

define Package/msm8916-mf32-modem
  $(call Package/modem-default,Openstick MF32)
endef

define Package/msm8916-mf32-modem/install
  $(call Package/modem-install,$(1),openstick-mf32)
endef
$(eval $(call BuildPackage,msm8916-mf32-modem))

#======================================================================
#  MF601

define Package/msm8916-mf601-wcnss
  $(call Package/wcnss-default,Openstick MF601)
endef

define Package/msm8916-mf601-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-mf601)
endef
$(eval $(call BuildPackage,msm8916-mf601-wcnss))

define Package/msm8916-mf601-nv
  $(call Package/nv-default,Openstick MF601)
endef

define Package/msm8916-mf601-nv/install
  $(call Package/nv-install,$(1),openstick-mf601)
endef
$(eval $(call BuildPackage,msm8916-mf601-nv))

define Package/msm8916-mf601-modem
  $(call Package/modem-default,Openstick MF601)
endef

define Package/msm8916-mf601-modem/install
  $(call Package/modem-install,$(1),openstick-mf601)
endef
$(eval $(call BuildPackage,msm8916-mf601-modem))

#======================================================================
#  MF601S

define Package/msm8916-mf601s-wcnss
  $(call Package/wcnss-default,Openstick MF601S)
endef

define Package/msm8916-mf601s-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-mf601s)
endef
$(eval $(call BuildPackage,msm8916-mf601s-wcnss))

define Package/msm8916-mf601s-nv
  $(call Package/nv-default,Openstick MF601S)
endef

define Package/msm8916-mf601s-nv/install
  $(call Package/nv-install,$(1),openstick-mf601s)
endef
$(eval $(call BuildPackage,msm8916-mf601s-nv))

define Package/msm8916-mf601s-modem
  $(call Package/modem-default,Openstick MF601S)
endef

define Package/msm8916-mf601s-modem/install
  $(call Package/modem-install,$(1),openstick-mf601s)
endef
$(eval $(call BuildPackage,msm8916-mf601s-modem))

#=============================================================================
#  UFI001B

define Package/msm8916-ufi001b-wcnss
  $(call Package/wcnss-default,Openstick UFI001B)
endef

define Package/msm8916-ufi001b-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-ufi001b)
endef
$(eval $(call BuildPackage,msm8916-ufi001b-wcnss))

define Package/msm8916-ufi001b-nv
  $(call Package/nv-default,Openstick UFI001B)
endef

define Package/msm8916-ufi001b-nv/install
  $(call Package/nv-install,$(1),openstick-ufi001b)
endef
$(eval $(call BuildPackage,msm8916-ufi001b-nv))

define Package/msm8916-ufi001b-modem
  $(call Package/modem-default,Openstick UFI001B)
endef

define Package/msm8916-ufi001b-modem/install
  $(call Package/modem-install,$(1),openstick-ufi001b)
endef
$(eval $(call BuildPackage,msm8916-ufi001b-modem))

#==========================================================================
#  UFI001C

define Package/msm8916-ufi001c-wcnss
  $(call Package/wcnss-default,Openstick UFI001C)
endef

define Package/msm8916-ufi001c-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-ufi001c)
endef
$(eval $(call BuildPackage,msm8916-ufi001c-wcnss))

define Package/msm8916-ufi001c-nv
  $(call Package/nv-default,Openstick UFI001C)
endef

define Package/msm8916-ufi001c-nv/install
  $(call Package/nv-install,$(1),openstick-ufi001c)
endef
$(eval $(call BuildPackage,msm8916-ufi001c-nv))

define Package/msm8916-ufi001c-modem
  $(call Package/modem-default,Openstick UFI001C)
endef

define Package/msm8916-ufi001c-modem/install
  $(call Package/modem-install,$(1),openstick-ufi001c)
endef
$(eval $(call BuildPackage,msm8916-ufi001c-modem))

#========================================================================
#  UFI003

define Package/msm8916-ufi003-wcnss
  $(call Package/wcnss-default,Openstick UFI003)
endef

define Package/msm8916-ufi003-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-ufi003)
endef
$(eval $(call BuildPackage,msm8916-ufi003-wcnss))

define Package/msm8916-ufi003-nv
  $(call Package/nv-default,Openstick UFI003)
endef

define Package/msm8916-ufi003-nv/install
  $(call Package/nv-install,$(1),openstick-ufi003)
endef
$(eval $(call BuildPackage,msm8916-ufi003-nv))

define Package/msm8916-ufi003-modem
  $(call Package/modem-default,Openstick UFI003)
endef

define Package/msm8916-ufi003-modem/install
  $(call Package/modem-install,$(1),openstick-ufi003)
endef
$(eval $(call BuildPackage,msm8916-ufi003-modem))

#============================================================================
#  UFI103S

define Package/msm8916-ufi103s-wcnss
  $(call Package/wcnss-default,Openstick UFI103S)
endef

define Package/msm8916-ufi103s-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-ufi103s)
endef
$(eval $(call BuildPackage,msm8916-ufi103s-wcnss))

define Package/msm8916-ufi103s-nv
  $(call Package/nv-default,Openstick UFI103S)
endef

define Package/msm8916-ufi103s-nv/install
  $(call Package/nv-install,$(1),openstick-ufi103s)
endef
$(eval $(call BuildPackage,msm8916-ufi103s-nv))

define Package/msm8916-ufi103s-modem
  $(call Package/modem-default,Openstick UFI103S)
endef

define Package/msm8916-ufi103s-modem/install
  $(call Package/modem-install,$(1),openstick-ufi103s)
endef
$(eval $(call BuildPackage,msm8916-ufi103s-modem))

#===============================================================================
#  SP970

define Package/msm8916-sp970-wcnss
  $(call Package/wcnss-default,Openstick SP970)
endef

define Package/msm8916-sp970-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-sp970)
endef
$(eval $(call BuildPackage,msm8916-sp970-wcnss))

define Package/msm8916-sp970-nv
  $(call Package/nv-default,Openstick SP970)
endef

define Package/msm8916-sp970-nv/install
  $(call Package/nv-install,$(1),openstick-sp970)
endef
$(eval $(call BuildPackage,msm8916-sp970-nv))

define Package/msm8916-sp970-modem
  $(call Package/modem-default,Openstick SP970)
endef

define Package/msm8916-sp970-modem/install
  $(call Package/modem-install,$(1),openstick-sp970)
endef
$(eval $(call BuildPackage,msm8916-sp970-modem))

#===================================================================
#  UZ801

define Package/msm8916-uz801-wcnss
  $(call Package/wcnss-default,Openstick UZ801)
endef

define Package/msm8916-uz801-wcnss/install
  $(call Package/wcnss-install,$(1),openstick-uz801)
endef
$(eval $(call BuildPackage,msm8916-uz801-wcnss))

define Package/msm8916-uz801-nv
  $(call Package/nv-default,Openstick UZ801)
endef

define Package/msm8916-uz801-nv/install
  $(call Package/nv-install,$(1),openstick-uz801)
endef
$(eval $(call BuildPackage,msm8916-uz801-nv))

define Package/msm8916-uz801-modem
  $(call Package/modem-default,Openstick UZ801)
endef

define Package/msm8916-uz801-modem/install
  $(call Package/modem-install,$(1),openstick-uz801)
endef
$(eval $(call BuildPackage,msm8916-uz801-modem))

#===============================================================
#  wt8x047 NV

define Package/msm8916-wt8x047-nv
  $(call Package/nv-default,wt8x047)
endef

define Package/msm8916-wt8x047-nv/install
  $(call Package/nv-install,$(1),wt8x047)
endef
$(eval $(call BuildPackage,msm8916-wt8x047-nv))

#==============================================================
#  wt86047

define Package/msm8916-wt8x047-wcnss
  $(call Package/wcnss-default,Wingtech wt86047)
endef

define Package/msm8916-wt86047-wcnss/install
  $(call Package/wcnss-install,$(1),wt86047)
endef
$(eval $(call BuildPackage,msm8916-wt8x047-wcnss))

define Package/msm8916-wt86047-modem
  $(call Package/modem-default,Wingtech wt86047)
endef

define Package/msm8916-wt86047-modem/install
  $(call Package/modem-install,$(1),wt86047)
endef
$(eval $(call BuildPackage,msm8916-wt86047-modem))

#==============================================================
#  wt88047

define Package/msm8916-wt88047-wcnss
  $(call Package/wcnss-default,Wingtech wt88047)
endef

define Package/msm8916-wt88047-wcnss/install
  $(call Package/wcnss-install,$(1),wt88047)
endef
$(eval $(call BuildPackage,msm8916-wt88047-wcnss))

define Package/msm8916-wt88047-modem
  $(call Package/modem-default,Wingtech wt88047)
endef

define Package/msm8916-wt88047-modem/install
  $(call Package/modem-install,$(1),wt88047)
endef
$(eval $(call BuildPackage,msm8916-wt88047-modem))

#==============================================================
