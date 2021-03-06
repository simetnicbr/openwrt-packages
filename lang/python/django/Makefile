#
# Copyright (C) 2007-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=django
PKG_VERSION:=1.8.19
PKG_RELEASE:=1

PKG_SOURCE:=Django-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/source/D/Django
PKG_HASH:=33d44a5cf9d333247a9a374ae1478b78b83c9b78eb316fc04adde62053b4c047
PKG_BUILD_DIR:=$(BUILD_DIR)/Django-$(PKG_VERSION)

PKG_MAINTAINER:=Alexandru Ardelean <ardeleanalex@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE LICENSE.python
PKG_CPE_ID:=cpe:/a:djangoproject:django

include $(INCLUDE_DIR)/package.mk
include ../python-package.mk

define Package/django
    SUBMENU:=Python
    SECTION:=lang
    CATEGORY:=Languages
    TITLE:=The web framework for perfectionists with deadlines.
    URL:=https://www.djangoproject.com/
    DEPENDS:=+python
endef

define Package/django/description
    The web framework for perfectionists with deadlines.
endef

define Build/Compile
	$(call Build/Compile/PyMod,,install --prefix=/usr --root=$(PKG_INSTALL_DIR))
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/django-admin.py \
	    $(1)/usr/bin
endef

define Package/django/install
	$(INSTALL_DIR) $(1)$(PYTHON_PKG_DIR)
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON_PKG_DIR)/* \
	    $(1)$(PYTHON_PKG_DIR)
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/django-admin.py \
	    $(1)/usr/bin
	# fix python exec path
	sed -i 's/#!.*/#!\/usr\/bin\/python/g' $(1)/usr/bin/django-admin.py
endef

$(eval $(call BuildPackage,django))
