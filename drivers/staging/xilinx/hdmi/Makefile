# mainlining: remove CFLAGS<...> += -I$(src)/include
# see below for further mainlining hints

# in same cases only used to check against presence, i.e. >0, actual number is not used
ccflags-y := -DXPAR_XVPHY_NUM_INSTANCES=4
ccflags-y += -DXPAR_XV_HDMIRXSS_NUM_INSTANCES=4
ccflags-y += -DXPAR_XV_HDMITXSS_NUM_INSTANCES=4
ccflags-y += -DXPAR_XV_HDMIRX_NUM_INSTANCES=4
ccflags-y += -DXPAR_XV_HDMITX_NUM_INSTANCES=4
ccflags-y += -DXPAR_XVTC_NUM_INSTANCES=4

ccflags-y += -DXPAR_VPHY_0_TRANSCEIVER=5
ccflags-y += -DXPAR_VPHY_0_RX_PROTOCOL=1
ccflags-y += -DXPAR_VPHY_0_TX_PROTOCOL=1
ccflags-y += -DXPAR_XV_HDMIRX_0_DEVICE_ID=0
ccflags-y += -DXPAR_XV_HDMITX_0_DEVICE_ID=0

ccflags-y += -DXPAR_XHDCP_NUM_INSTANCES=4
ccflags-y += -DXPAR_XHDCP22_RX_NUM_INSTANCES=4
ccflags-y += -DXPAR_XHDCP22_TX_NUM_INSTANCES=4
ccflags-y += -DXPAR_XHDCP22_MMULT_NUM_INSTANCES=4
ccflags-y += -DXPAR_XHDCP22_CIPHER_NUM_INSTANCES=8
ccflags-y += -DXPAR_XHDCP22_RNG_NUM_INSTANCES=8
ccflags-y += -DXPAR_XTMRCTR_NUM_INSTANCES=16

ccflags-y += -I${src}/phy-xilinx-vphy

# the BSP code uses C99 style declarations. The kernel is on C89, but steps to C11 are underway.
ccflags-y += -Wno-declaration-after-statement
ccflags-y += -Wno-unused-function
ccflags-y += -Wno-unused-label
ccflags-y += -Wno-unused-value
ccflags-y += -Wno-unused-variable

# V4L2 (HDMI RX)
# mainlining: drivers/media/platform/xilinx/Makefile
obj-$(CONFIG_VIDEO_XILINX_HDMI_RX) += xilinx-hdmi-rx.o

# top-level Linux driver source
xilinx-hdmi-rx-objs := xilinx-hdmirx.o

# the C API around the IP registers
CFLAGS_xilinx-hdmirx.o += -I$(src)/xilinx-hdmi-rx/
CFLAGS_xilinx-hdmirx.o += -I$(src)/include/ -Idrivers/media/platform/xilinx/
xilinx-hdmi-rx-objs += xilinx-hdmi-rx/xv_hdmirx.o
xilinx-hdmi-rx-objs += xilinx-hdmi-rx/xv_hdmirx_sinit.o
xilinx-hdmi-rx-objs += xilinx-hdmi-rx/xv_hdmirx_intr.o
xilinx-hdmi-rx-objs += xilinx-hdmi-rx/xv_hdmirxss.o
xilinx-hdmi-rx-objs += xilinx-hdmi-rx/xv_hdmirxss_log.o
xilinx-hdmi-rx-objs += xilinx-hdmi-rx/xv_hdmirxss_coreinit.o
xilinx-hdmi-rx-objs += xilinx-hdmi-rx/xv_hdmirxss_hdcp.o
xilinx-hdmi-rx-objs += xilinx-hdmi-rx/xv_hdmirx_vsif.o


# DRM (HDMI TX)
# mainlining: drivers/gpu/drm/xilinx/Makefile

obj-$(CONFIG_DRM_XILINX_HDMI) += xilinx-hdmi-tx.o

# top-level Linux driver source
xilinx-hdmi-tx-objs := xilinx_drm_hdmi.o

# the C API around the IP registers
CFLAGS_xilinx_drm_hdmi.o += -I$(src)/xilinx-hdmi-tx/
CFLAGS_xilinx_drm_hdmi.o += -I$(src)/include/ -Idrivers/gpu/drm/xilinx/

xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xv_hdmitx.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xv_hdmitx_sinit.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xv_hdmitx_intr.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xv_hdmitxss.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xv_hdmitxss_log.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xv_hdmitxss_coreinit.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xv_hdmitxss_hdcp.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xv_hdmitx_vsif.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xvtc.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xvtc_intr.o
xilinx-hdmi-tx-objs += xilinx-hdmi-tx/xvtc_sinit.o

# module interdependency during linking
# (probably only needed when building separate modules)
#KBUILD_EXTRA_SYMBOLS += ../../../phy/Modules.symvers

# PHY (HDMI RX/TX)
# mainlining: drivers/phy/Makefile

obj-$(CONFIG_PHY_XILINX_VPHY)		+= phy-xilinx-vphy.o

# top-level Linux driver source
phy-xilinx-vphy-objs := phy-vphy.o

# the C API around the IP registers
CFLAGS_phy-vphy.o += -I$(src)/phy-xilinx-vphy/
CFLAGS_phy-vphy.o += -I$(src)/include/

phy-xilinx-vphy-objs += phy-xilinx-vphy/xdebug.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvphy.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvphy_i.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvphy_gthe4.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvphy_hdmi.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvphy_hdmi_intr.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvphy_intr.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvphy_log.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvphy_sinit.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvidc.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvidc_edid.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xvidc_timings_table.o

#hdcp1x sources
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_platform.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_port.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_port_intr.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_port_hdmi_rx.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_port_hdmi_tx.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_cipher.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_cipher_intr.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_rx.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_tx.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_intr.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_sinit.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp1x_selftest.o

#hdcp22 common
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_cipher.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_cipher_sinit.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_mmult.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_mmult_sinit.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_rng.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_rng_sinit.o

#hdcp library
phy-xilinx-vphy-objs += phy-xilinx-vphy/bigdigits.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/aes.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/hmac.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/sha1.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/sha2.o

#hdcp key/password decryption
phy-xilinx-vphy-objs += phy-xilinx-vphy/aes256.o

#timer
phy-xilinx-vphy-objs += phy-xilinx-vphy/xtmrctr.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xtmrctr_l.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xtmrctr_sinit.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xtmrctr_options.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xtmrctr_intr.o

#hdcp22-tx
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_tx.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_tx_crypt.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_tx_sinit.o

#hdcp22-rx
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_rx.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_rx_crypt.o
phy-xilinx-vphy-objs += phy-xilinx-vphy/xhdcp22_rx_sinit.o
