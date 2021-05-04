include $(TOPDIR)/rules.mk
 
PKG_NAME:=jitterentropy
PKG_VERSION:=1.2.2
PKG_RELEASE:=1
PKG_BUILD_DIR:=$(BUILD_DIR)/jitterentropy-rngd-$(PKG_VERSION)
PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/smuellerDD/jitterentropy-rngd/archive/refs/tags/
PKG_HASH:=4fb5ba0f954815186411c20dd3fd988c3f009df9dcde9f59fc1b28bc31424d37
PKG_LICENSE:=GPL-2.0-only
TARGET_CFLAGS:=-O0
 
include $(INCLUDE_DIR)/package.mk
 
define Package/jitterentropy
  SECTION:=base
  CATEGORY:=Utilities
  TITLE:=CPU Jitter Random Number Generator
  URL:=https://github.com/smuellerDD/jitterentropy-rngd
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