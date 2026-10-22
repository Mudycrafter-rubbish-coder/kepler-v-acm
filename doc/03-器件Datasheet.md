# KEPLER V 辅助控制模块器件 Datasheet

[项目主页](../README.md) | [English README](../README.md) | [中文 README](../README.zh-CN.md)

`assets/datasheets/` 保存 V1 主要芯片和保护器件的厂商 PDF。文件名带有型号、版本或发布日期，方便复刻时确认资料没有过期。阻容、LED 和 USB-C 连接器没有单独收录。

## 快速索引

| 位号 | BOM 型号 | 厂商 | 封装 | 本地 PDF | 页数 |
|---|---|---|---|---:|---:|
| U1 | CH32V003F4P6 | WCH 沁恒 | TSSOP-20 | [CH32V003F4P6_DS0_v1.8.pdf](../assets/datasheets/CH32V003F4P6_DS0_v1.8.pdf) | 31 |
| U2 | XC6206P332MR-G | Torex | SOT-23-3 | [XC6206_Series_ETR0305_004b.pdf](../assets/datasheets/XC6206_Series_ETR0305_004b.pdf) | 17 |
| U3 | CH340N | WCH 沁恒 | SOP-8 | [CH340_DS1_v3D.pdf](../assets/datasheets/CH340_DS1_v3D.pdf) | 10 |
| U4 | 74HC4053D118 | Nexperia | SOIC-16 | [74HC_HCT4053_Rev9_2016-02-10.pdf](../assets/datasheets/74HC_HCT4053_Rev9_2016-02-10.pdf) | 31 |
| D2 | USBLC6-2SC6 | UMW 友台半导体 | SOT-23-6 | [USBLC6-2SC6_UMW_2024-11.pdf](../assets/datasheets/USBLC6-2SC6_UMW_2024-11.pdf) | 7 |
| D3 | BAT54C,215 | NXP / Nexperia | SOT-23-3 | [BAT54_Series_Rev5_2012-10-05.pdf](../assets/datasheets/BAT54_Series_Rev5_2012-10-05.pdf) | 11 |

## 来源与适用性

### CH32V003F4P6

- 文档：`CH32V003DS0 V1.8`
- 官方下载页：<https://www.wch-ic.com/downloads/CH32V003DS0_PDF.html>
- 立创资料页：<https://item.szlcsc.com/datasheet/CH32V003F4P6/5858783.html>
- 用途：MCU 引脚、复用功能、电源、时钟、SWIO 调试、Flash/RAM 和定时器能力。

### XC6206P332MR-G

- 文档：`XC6206 Series ETR0305_004b`
- 官方 PDF：<https://www.torexsemi.com/file/xc6206/XC6206.pdf>
- 用途：3.3 V LDO 的压差、输出电流、输入输出电容和热限制。

### CH340N

- 文档：`CH340DS1 v3D`
- 官方下载页：<https://www.wch-ic.com/downloads/CH340DS1_PDF.html>
- 立创资料页：<https://item.szlcsc.com/datasheet/CH340N/3390257.html>
- 用途：USB Full-Speed、V3/VCC 供电方式、UART 引脚以及内置时钟配置。

### 74HC4053D118

- 文档：`74HC/HCT4053 Rev. 9, 2016-02-10`
- 官方 PDF：<https://assets.nexperia.com/documents/data-sheet/74HC_HCT4053.pdf>
- 用途：两路 UART 在飞控 UART5 与 CH340 之间切换；重点核对选择端阈值、供电范围、导通电阻和上电默认状态。
- 说明：文档页眉保留旧 NXP 品牌信息，但 Nexperia 当前官方下载地址提供的也是这份器件系列数据手册。

### USBLC6-2SC6

- 文档：`UMW USBLC6-2SC6`，2024 年 11 月
- UMW 官方 PDF：<https://www.umw-ic.com/static/pdf/b2c190f0a00a742e1ffd3347f22dc112.pdf>
- 立创资料页：<https://item.szlcsc.com/datasheet/USBLC6-2SC6/2790619.html>
- 用途：USB D+/D- ESD 保护、I/O 与 VBus 引脚拓扑、钳位和封装。
- 说明：本地文件是板上 BOM 精确厂商 UMW 的资料，不是 ST 原版 USBLC6-2SC6 的替代手册。

### BAT54C,215

- 文档：`BAT54 series Rev. 5, 2012-10-05`
- Nexperia 官方 PDF：<https://assets.nexperia.com/documents/data-sheet/BAT54_SER.pdf>
- 立创实际文件：<https://atta.szlcsc.com/upload/public/pdf/source/20161024/1477288736847.pdf>
- 用途：飞控 5 V 与 USB 5 V 的电源 OR；`BAT54C` 是共阴极双二极管版本，见手册内的器件型号与引脚表。

## 文件校验

| 文件 | SHA-256 |
|---|---|
| CH32V003F4P6_DS0_v1.8.pdf | `2C05B25A3EF9269CA3685DB09DE05A2B31C650E1B389B0CECC735D4176985B91` |
| XC6206_Series_ETR0305_004b.pdf | `8FDA1E40EA3E7C17178353ACEBA9C9A9794E56A1960D02B105C576429CE418ED` |
| CH340_DS1_v3D.pdf | `6A6922D3C4DE2D4FC9B7FB2C938985D2BBD73CD381813F10E940B492BAEBB7C0` |
| 74HC_HCT4053_Rev9_2016-02-10.pdf | `BF85DBC69DAAAE2C4E9987B0E61623E3823E45D31D6CFACFE38D9FB85AC7EB87` |
| USBLC6-2SC6_UMW_2024-11.pdf | `973EA7520F3CD820E2C9326FCF3EE3CA5239CFF491D6F42DE057573942DCDF83` |
| BAT54_Series_Rev5_2012-10-05.pdf | `3EC7FB498B904480ABAB9A548ED918B2EA5504BED6F82D5B0A1E4C304D52214F` |

## 使用说明

原理图、布局和采购检查应以对应的精确型号为准。型号相近但封装或引脚定义不同的器件不能直接替换，尤其是 74HC4053、USBLC6、XC6206 和 BAT54 系列。

这些数据手册由各自的制造商发布。文件保留原厂版权和许可，不适用本项目的 MIT 许可证。
