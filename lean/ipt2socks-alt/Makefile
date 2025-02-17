# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2021 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=ipt2socks-alt
PKG_VERSION:=1.1.3
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/zfl9/ipt2socks/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=73a2498dc95934c225d358707e7f7d060b5ce81aa45260ada09cbd15207d27d1

PKG_BUILD_DIR:=$(BUILD_DIR)/$(firstword $(subst -, ,$(PKG_NAME)))-$(PKG_VERSION)
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

PKG_LICENSE:=AGPL-3.0
PKG_LICENSE_FILE:=LICENSE

include $(INCLUDE_DIR)/package.mk

define Package/ipt2socks-alt
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Convert iptables to socks5
	URL:=https://github.com/zfl9/ipt2socks
	DEPENDS:=+libpthread
endef

define Package/ipt2socks/description
  Utility for converting iptables (redirect/tproxy) to socks5.
endef

TARGET_CFLAGS+= $(FPIC) -flto -pthread
MAKE_FLAGS+= \
	CFLAGS="-std=c99 -pthread $(TARGET_CFLAGS)" \
	EVCFLAGS="$(TARGET_CFLAGS)"

define Package/ipt2socks-alt/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/ipt2socks $(1)/usr/bin/ipt2socks-alt
endef

$(eval $(call BuildPackage,ipt2socks-alt))
