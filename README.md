# fuxi-firmware

Xiaomi 13 / fuxi (SM8550 / kalama) 专有固件库。目录结构 = `<分区>/<分区内相对路径>/<文件>`，与设备端挂载路径一致。

来源：AOSPA topaz alpha-1（fuxi，2023-09-22）镜像解包：
`vendor.img`、`vendor_dlkm.img`、`odm.img`、`system_dlkm.img`。

## 已收录分区
- `odm/firmware/` —— GPU 签名 ZAP（`a740_zap.*`）、触控固件（`st_fts_m3.ftb`）、
  相机 OIS/ICP、音频校准（cs35l41）等
- `vendor/firmware/` —— `a740_sqe.fw`、`gmu_gen70200.bin`、EVaSS、VPU、
  CAMERA_ICP、触觉 RTP、Wi-Fi（qca_cld/kiwi_v2）
- `vendor/etc/display/` —— 面板校准（qdcm_calib_data_*.json）
- `vendor_dlkm/` —— 内核模块（lib/modules/*.ko）与 etc
- `system_dlkm/` —— 内核模块与 etc

## 未收录（避免仓库过大，需时再补）
- `vendor/etc/camera/`（391M 相机资源）、`vendor/lib/rfsa/adsp/`（392M ADSP 模型）
- `odm/etc/camera/`、`odm/lib64/camera/`（相机调优）
- `system/system_ext/product` 里的 app/so/overlay 等非固件内容
- PAS 固件（adsp/cdsp/slpi/modem/venus 的 .mbn）与签名 bootloader 镜像：
  不在这批 AOSPA 镜像中，需 modem/firmware 分区或官方 fastboot 包补充

## 清单
`proprietary-files.txt`：`path|sha256` 格式，与 `extract-files.py` 的 SOURCE 目录布局对应。
