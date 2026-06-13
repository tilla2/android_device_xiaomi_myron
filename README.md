# OrangeFox Recovery — Xiaomi myron (POCO F8 Ultra / Redmi K90 Pro Max)

## 设备信息
| Item | Value |
|---|---|
| SoC | Snapdragon 8 Elite Gen 5 (SM8850 / sun) |
| CPU | Oryon (8 cores) |
| RAM | 12/16 GB |
| Storage | 256/512 GB UFS 4.0 |
| Display | 1200×2608, 120Hz OLED |
| Kernel | GKI 6.12 (Android 16) |
| A/B | Virtual A/B + dedicated recovery partition |
| Encryption | FBE (aes-256-xts + wrappedkey_v0) |
| KeyMint | TEE (vendor.keymint-qti) + Strongbox (Thales JavaCard via se_omapi) |
| Haptics | PMIC HV haptics (qcom-hv-haptics revision 5) |

## 构建
```bash
git clone https://github.com/OrangeFox16/sync.git
cd sync
./orangefox_sync.sh --branch 16.0 --path ~/fox_16.0
cd fox_16.0
source build/envsetup.sh
lunch twrp_myron-bp2a-eng
mka recoveryimage
```
如需使用github actions构建，请自行寻找脚本


## 目前支持的特性
触屏(这个不支持就难绷了)✅  
解密Data ✅  
MTP ❌  
震动 ❌  

剩下的忘了

后续会移除不需要的二进制，修BUG，增加新功能的
## 注意
自行构建的OrangeFox不能直接刷入recovery分区(Release里的是处理好的)，需要使用仓库下的“移植vbmeta.py”脚本把原厂recovery的avb信息移植过去后再刷入  
python 移植vbmeta.py <原厂recovery.img> <被修补的镜像> <修补后的文件>

## Maintainer
haohao3001 - 维护者  
基于[hackpupg001-a11y的设备树](https://github.com/hackpupg001-a11y/android_device_xiaomi_myron)魔改  
recovery/root下的大部分二进制文件来自于 變換風雲@coolapk 的TWRP
