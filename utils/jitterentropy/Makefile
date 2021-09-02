include $(TOPDIR)/rules.mk

PKG_NAME:=jitterentropy
PKG_VERSION:=9d488e7b81c7b9e2a1fabcdd02ac8c9a48aa8b97
PKG_RELEASE:=7

PKG_BUILD_DIR:=$(BUILD_DIR)/jitterentropy-rngd-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_VERSION).zip
PKG_SOURCE_URL:=https://github.com/smuellerDD/jitterentropy-rngd/archive/
PKG_HASH:=aab743d340b015498ab7ded099f2872aab9608bafbf059a689395d2ff39e2d92
PKG_CAT:=unzip
PKG_LICENSE:=GPL-2.0-only BSD-3-Clause

# These flags are simply replicated from the defaults here https://github.com/smuellerDD/jitterentropy-rngd/blob/master/Makefile
TARGET_CFLAGS:=-Wextra -Wall -pedantic -fwrapv --param ssp-buffer-size=4 -fvisibility=hidden -fPIE -Wcast-align -Wmissing-field-initializers -Wshadow -Wswitch-enum -O0
TARGET_LDFLAGS:=-Wl,-z,relro,-z,now -pie

include $(INCLUDE_DIR)/package.mk

define Package/jitterentropy
  SECTION:=base
  CATEGORY:=Utilities
  TITLE:=CPU Jitter Random Number Generator
  URL:=https://github.com/smuellerDD/jitterentropy-rngd
  MAINTAINER:=https://github.com/stoickish
endef

define Package/jitterentropy/description
 Using the Jitter RNG core, the rngd provides an entropy source that feeds into the Linux /dev/random device if its entropy runs low.
 It updates the /dev/random entropy estimator such that the newly provided entropy unblocks /dev/random.
endef

define Package/jitterentropy/install
		$(INSTALL_DIR) $(1)/etc/init.d
		$(INSTALL_BIN) ./files/jitterentropy.init $(1)/etc/init.d/jitterentropy
		$(INSTALL_DIR) $(1)/usr/sbin
		$(INSTALL_BIN) $(PKG_BUILD_DIR)/jitterentropy-rngd $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,jitterentropy))
