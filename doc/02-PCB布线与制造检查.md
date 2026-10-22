# KEPLER V Auxiliary Control Module PCB V1

## 当前状态

- EasyEDA Pro：4.1.78
- 工程 UUID：`f548c6ce5ccadd461f5fdd9284854e74b0a72f84427e5bbb7b8062955da6f821`
- 原理图页 UUID：`0e4bb6c94d56dbf0`
- PCB UUID：`e657fb75da1330a4`
- Board：`KEPLER_V_AUX`
- 尺寸：`25.000 mm × 26.016 mm`
- 层数：4 层
- 器件：36 个
- 走线：501 段，0 条圆弧
- 过孔：47 个
- 覆铜：2 个网络层铜面
- 原生 PCB DRC：通过，0 violation
- 扩展 DFM 检查：0 error，64 warning

当前原生项目归档位于 [source/easyeda/kepler-v-acm-v1.epro2](../source/easyeda/kepler-v-acm-v1.epro2)。最终验证摘要、DRC/DFM 原始结果、Gerber、BOM、CPL 和铜层数据属于本地生成物，保存在 `outputs/`，不上传到公开仓库。

## 板级方案

### 层叠

| 层 | 用途 |
|---|---|
| Top | 主要器件和信号 |
| Inner1 | GND 大面积铜 |
| Inner2 | +3V3 大面积铜 |
| Bottom | CH32、CH340、74HC4053 和背面走线 |

EasyEDA 当前把两个内层都报告为 `SIGNAL` 层，但都已有对应网络的完整覆铜。尝试把 Inner1 改成负片 `PLANE` 时，宿主接口回读失败且没有实际写入，因此最终文件保留了可验证的正片铜面方案。对这块小板的低电流分配已经足够，不把失败的 `PLANE` 切换写成已完成。

### 尺寸取舍

`20 mm × 20 mm` 无法同时容纳当前 USB-C、SWIO、飞控串口和两组舵机/GPIO/DVR 焊盘，并且会牺牲手焊间距。最终把高度增加 `1.016 mm`，得到 `25 × 26.016 mm`，仍低于 `30 × 30 mm` 上限。

### 外部接口

原理图使用 `J1`～`J6` 表示接口；PCB 上保留对应的 2.54 mm 通孔焊盘，但不采购、不安装排针。它们已经从原理图 BOM 排除，焊线时直接使用通孔和铜环。

| 接口 | 网络 |
|---|---|
| J1 | `FC_5V / GND / FC_UART5_TX / FC_UART5_RX` |
| J2 | `SERVO1_PWM / GND` |
| J3 | `SERVO2_PWM / GND` |
| J4 | `GPIO1 / GPIO2 / GPIO3 / GND` |
| J5 | `DVR_AVI_N / DVR_JPG_N / GND` |
| J6 | `+3V3 / GND / SWIO / NRST` |
| J7 | USB-C，连接 CH340N 和 USB ESD |

## 布线与电源

- UART/CH340 切换、USB、SWIO、录像触发和输出信号均已全板连通。
- GND 使用 Inner1 完整覆铜，+3V3 使用 Inner2 完整覆铜；所有可用电源/地焊盘已做缝合，无法安全打孔的位置没有强行放孔。
- `+5V_AUX` 使用加宽走线，不单独占用内层。
- USB 为 CH340N 的 Full-Speed USB，不是 High-Speed。由于板内路径很短，最终没有保留原生 DRC 中 10 mil 级别的不现实等长约束；USB 差分仍按相邻、短路径布线。
- USB-C 定位槽到走线的最小 DRC 规则设为 `8 mil`，对应 `0.2032 mm`。普通铜间距仍为 `6 mil`。下单前必须在 JLC 预览中再次确认槽边不会被扩大或补铜。

## 未收口项

扩展 DFM 仍有 64 个 warning，主要集中在：

- 23 个小器件位号文字与焊盘包围盒相交。
- `C1` 距 LDO 输入脚约 `315 mil`，`C6/C7` 距 MCU 电源脚分别约 `135/222 mil`。
- 19 组局部并行线距离低于 3W 启发式阈值。
- 8 条走线与理想 0/45/90° 网格有偏差，4 处折角低于 90°。
- `+5V_AUX` 仍以 10 mil 走线为主，没有独立铜面。
- USB-C 的 4 个多边形电源/屏蔽焊盘无法由 `pcb check` 做精确 `net-path` 几何证明。

这些 warning 没有产生公开 DRC error，也不包含开路、短路、焊盘内过孔或单层过孔。它们属于下一版布局优化项；制造前应先查看 Gerber 预览和 JLC DFM 结果。

## 预览

- [最终顶层](../assets/images/pcb-top.png)
- [最终底层](../assets/images/pcb-bottom.png)
- [双面 SVG 总览](../assets/images/pcb-overview.svg)

顶层和底层截图为 EasyEDA 当前画布的前台捕获；铜、焊盘和丝印是视觉复核，电气结论以 DRC、DFM 和保存重载回读为准。
