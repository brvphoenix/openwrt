include $(TOPDIR)/rules.mk

PKG_NAME:=qca-ppe
PKG_RELEASE:=1

PKG_VERSION:=1

PKG_BUILD_PARALLEL:=1
PKG_FLAGS:=nonshared

include $(INCLUDE_DIR)/kernel.mk
include $(INCLUDE_DIR)/package.mk

define KernelPackage/qca-ppe
  SECTION:=kernel
  CATEGORY:=Kernel modules
  SUBMENU:=Network Devices
  DEPENDS:=@(TARGET_qualcommax_ipq807x||TARGET_qualcommax_ipq60xx) +kmod-qca-edma +kmod-qca-uniphy
  TITLE:=Qualcomm PPE switch driver
  FILES:=$(PKG_BUILD_DIR)/qca_ppe.ko
  AUTOLOAD:=$(call AutoLoad,32,qca_ppe)
endef

define KernelPackage/qca-ppe/Description
  Driver for Qualcomm PPE (Packet Processing Engine) switches.
endef

define Build/Compile
	+$(KERNEL_MAKE) $(PKG_JOBS) \
		-C "$(LINUX_DIR)" \
		M="$(PKG_BUILD_DIR)" \
		EXTRA_CFLAGS="-I$(STAGING_DIR)/usr/include" \
		modules
endef

$(eval $(call KernelPackage,qca-ppe))
