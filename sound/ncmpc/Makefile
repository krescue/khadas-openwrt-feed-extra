#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=ncmpc
PKG_VERSION:=0.27
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=http://www.musicpd.org/download/ncmpc/0
PKG_HASH:=121c99645fa2ba6dc86db28a46944ebb

PKG_LICENSE:=GPL-2.0+
PKG_LICENSE_FILES:=COPYING
PKG_MAINTAINER:=hyphop

include $(INCLUDE_DIR)/package.mk

define Package/ncmpc
  SECTION:=sound
  CATEGORY:=Sound
  DEPENDS:=+libmpdclient +glib2 +libncursesw
  TITLE:=Music Player Daemon Console Client
  URL:=http://www.musicpd.org/
endef

define Package/ncmpc/description
	MPC is client for MPD ;-) 
endef

define Build/Configure
$(call Build/Configure/Default, \
	--disable-iconv \
	--enable-chat-screen \
	--enable-colors \
	--disable-nls \
)
endef


define Build/Compile
$(call Build/Compile/Default,\
		CFLAGS="$(TARGET_CFLAGS) -std=gnu99" \
		prefix="/usr" \
		all \
)
endef

define Package/ncmpc/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/ncmpc $(1)/usr/bin/
#	$(INSTALL_BIN) ./files/pls-handler.sh $(1)/usr/bin/
endef

$(eval $(call BuildPackage,ncmpc))
