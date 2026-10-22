# KEPLER V 项目文档

[English README](../README.md) | [中文 README](../README.zh-CN.md)

这里保存的是供外部审查者阅读的设计说明。准备复刻、修改、制造或写固件时，先看根目录的 README，再按需要打开对应文档。

- [01 原理图设计](01-原理图设计说明.md)：功能划分、供电、UART 自动切换、MCU 引脚、外部接口和固件约束。
- [02 PCB 与制造检查](02-PCB布线与制造检查.md)：25.000 mm × 26.016 mm 四层板、层叠、布线、DRC/DFM 和下单前检查。
- [03 器件 Datasheet](03-器件Datasheet.md)：V1 主要芯片与保护器件的厂商 PDF、版本、来源和校验值。

`outputs/` 中保存 Gerber、BOM、CPL、DRC/DFM 原始数据和本地预览。这个目录不进入 Git。

