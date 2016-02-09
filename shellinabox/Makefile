#
# Copyright (C) 2016 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# Initial port of shellinabox to OpenWrt - Jan Jaeger 25-MAR-2010
#
# Makefile from OnionIoT/OpenWRT-Packages was used as a start
#

include $(TOPDIR)/rules.mk

PKG_NAME:=shellinabox
PKG_VERSION:=2.19
PKG_REV:=1a8010f2c94a62e7398c4fa130dfe9e099dc55cd
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_URL:=https://github.com/shellinabox/shellinabox.git
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=$(PKG_REV)

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/shellinabox
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Shell In A Box
	DEPENDS:=+libopenssl
	URL:=https://github.com/shellinabox/shellinabox
	MAINTAINER:=Entware team, http://entware.net
endef

define Package/shellinabox/description
 Web based AJAX terminal emulator
endef

CONFIGURE_ARGS += \
	--disable-pam \
	--disable-runtime-loading \
	--bindir="/opt/sbin"

define Package/shellinabox/install
	# install the binary
	$(INSTALL_DIR) $(1)/opt/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/shellinaboxd $(1)/opt/sbin
	# install the init.d file
	$(INSTALL_DIR) $(1)/opt/etc/init.d
	$(INSTALL_BIN) ./files/S88shellinaboxd $(1)/opt/etc/init.d
	# install the css files
	$(INSTALL_DIR) $(1)/opt/lib/shellinabox
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/shellinabox/{black-on-white,color,monochrome,white-on-black}.css $(1)/opt/lib/shellinabox
endef

$(eval $(call BuildPackage,shellinabox))