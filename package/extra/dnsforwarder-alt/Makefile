include $(TOPDIR)/rules.mk

PKG_NAME:=dnsforwarder-alt
PKG_VERSION:=6.5.3
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/lifenjoiner/dnsforwarder.git
PKG_SOURCE_VERSION:=e6ac595bc39ec674ce1b10ef58f3e77f5af48e20
PKG_MIRROR_HASH:=skip

PKG_FIXUP:=autoreconf

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=net
  CATEGORY:=Network
  TITLE:=A simple DNS forwarder
  URL:=https://github.com/lifenjoiner/dnsforwarder
  DEPENDS:=+libpthread +coreutils-base64
endef

define Package/$(PKG_NAME)/description
Forwarding queries to customized domains (and their subdomains) to specified servers over a specified protocol (UDP or TCP). non-standard ports are supported.
endef

CONFIGURE_ARGS += --enable-downloader=no

TARGET_CFLAGS += -ffunction-sections -fdata-sections -flto
TARGET_LDFLAGS += -Wl,--gc-sections,--as-needed -flto

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/dnsforwarder $(1)/usr/sbin/dnsforwarder
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
