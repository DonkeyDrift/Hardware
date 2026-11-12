# MUS4 硬件设计 - v1.0.0

> 一台能跑神经网络的小车，一个能上手的自动驾驶课堂。
>
> MUS4 面向 AI 极客、RC 车手与教育工作者，基于 DonkeyCar / 漂移驴车开源生态打造，融合 LattePanda MU 上位机算力与 ESP32 下位机控制，以纯视觉感知、云端模型训练与一键部署，让每个人都能快速搭建属于自己的端到端自动驾驶小车。

***

## 项目概述

这是 MUS4 自动驾驶小车的硬件设计仓库，包含 KiCad 格式的原理图和 PCB 布局文件。

### 硬件特性

- **LattePanda MU 主控接口**：支持上位机算力模块
- **ESP32 下位机驱动电路**：实时底层运动控制
- **摄像头、电机、舵机、传感器接口**：丰富的外设扩展
- **电源管理与电池监测电路**：安全可靠的供电系统
- **通信接口**：USB / 串口 / I2C / PWM
- **支持直接导出 Gerber 生产文件**：方便 PCB 打样

### 设计文件

| 文件名                           | 描述                |
| ----------------------------- | ----------------- |
| `DonkeyDrift-MUS4.kicad_pro`  | KiCad 项目文件        |
| `DonkeyDrift-MUS4.kicad_sch`  | 原理图文件             |
| `DonkeyDrift-MUS4.kicad_pcb`  | PCB 布局文件          |
| `Controller.kicad_sch`        | 控制器子原理图           |
| `ESP32.kicad_sch`             | ESP32 子原理图        |
| `HDMI.kicad_sch`              | HDMI 接口子原理图       |
| `Interface.kicad_sch`         | 接口子原理图            |
| `LattePanda Module.kicad_sch` | LattePanda 模块子原理图 |
| `M.2 E&amp;M Key.kicad_sch`   | M.2 接口子原理图        |
| `PSU.kicad_sch`               | 电源子原理图            |
| `USB2.0&amp;USB3.0.kicad_sch` | USB 接口子原理图        |

### 目录结构

```
Hardware/
├── BOM/              # 物料清单文件夹
├── Drill/            # 钻孔文件文件夹
├── Gerber/           # Gerber 生产文件文件夹
├── Layout/           # PCB 布局图片文件夹
├── kicad_api_libs/   # KiCad 库文件
└── [主设计文件]      # KiCad 项目、原理图、PCB 文件
```

***

## 为什么选择 MUS4

- **纯视觉端到端架构**：无需激光雷达、高精地图等昂贵传感器，仅凭摄像头即可完成感知与决策
- **双核协同，分工明确**：LattePanda MU（Ubuntu + Python）负责图像感知与模型推理，ESP32（Arduino C++）负责实时底层运动控制
- **一站式硬件平台**：自研 PCB 板打通上下位机通信，无需从零焊接飞线
- **全栈开源，社区共建**：硬件设计、软件代码、训练模型全面开源

***

## 快速开始

### 1. 查看设计文件

使用 KiCad 10.0 或更高版本打开项目文件：

```bash
# 克隆仓库
git clone <your-repo-url>
cd Hardware

# 用 KiCad 打开项目
kiCad DonkeyDrift-MUS4.kicad_pro
```

### 2. 导出 Gerber 文件

1. 在 KiCad PCB Editor 中打开 `DonkeyDrift-MUS4.kicad_pcb`
2. 点击 `File` → `Plot`
3. 选择输出格式为 Gerber
4. 配置各层输出设置
5. 点击 `Plot` 生成 Gerber 文件
6. 生成钻孔文件：`File` → `Fabrication Outputs` → `Drill Files`

### 3. 查看 BOM

物料清单位于 `BOM/` 文件夹中。

### 4. 生产文件

- Gerber 文件已导出到 `Gerber/` 文件夹
- 钻孔文件已导出到 `Drill/` 文件夹

***

## 项目架构

MUS4 硬件系统采用上下位机架构：

```
┌─────────────────────────────────────────┐
│         LattePanda MU (上位机)          │
│  - Ubuntu Linux                         │
│  - Python / OpenCV / TensorFlow         │
│  - 图像采集与模型推理                   │
└──────────────┬──────────────────────────┘
               │ USB/串口通信
┌──────────────▼──────────────────────────┐
│         ESP32 (下位机)                  │
│  - Arduino C++                          │
│  - 实时运动控制                         │
│  - 电机/舵机驱动                        │
│  - 传感器读取                           │
└──────────────┬──────────────────────────┘
               │
┌──────────────▼──────────────────────────┐
│         外设接口                         │
│  - 摄像头                               │
│  - 电机 / 舵机                          │
│  - 电池管理                             │
│  - 其他传感器                           │
└─────────────────────────────────────────┘
```

***

## 相关资源

- **主代码库**：[https://github.com/DonkeyDrift](https://github.com/DonkeyDrift/DonkeyDrift)
  - 软件库：<https://github.com/DonkeyDrift/DonkeyDrift>
  - 固件库：<https://github.com/DonkeyDrift/Firmware>
  - 硬件库：<https://github.com/DonkeyDrift/Hardware>
- **产品指南**：\[待补充]
- **3D 打印模型**：\[待补充]
- **DonkeyDrift 社区**：[donkeydrift.com](https://www.donkeydrift.com)

***

## 一台小车，七种能力

MUS4 不仅是一台自动驾驶小车，更是一套全栈式的学习平台：

- **Linux 操作系统**：系统管理、环境配置、服务部署
- **Python 编程**：图像处理、数据采集、模型推理
- **神经网络与机器学习**：端到端自动驾驶模型训练
- **计算机视觉**：OpenCV 图像处理、车道线识别
- **单片机与嵌入式开发**：ESP32 编程、Arduino C++
- **多协议处理**：USB、串口、I2C、PWM 等硬件协议
- **RC 赛车技术**：车架结构、电机调校、转向微调

***

## 开源协议（v1.1 · 分层授权）

本仓库按**客体分层授权**，自社区委员会《开源许可证分层授权决议》生效之日起适用：

| 客体 | 许可证 | 全文 |
| --- | --- | --- |
| 本仓库硬件设计文件（原理图、PCB、封装库、Gerber、钻孔、BOM、结构图、Layout 图）及其衍生实物 | **CERN Open Hardware Licence Version 2 - Permissive（CERN-OHL-P-2.0）** | [LICENSE](LICENSE) |
| 配套固件与软件（`Firmware` 仓库 MUS4_FW、上位机代码） | **Apache License 2.0** | 见 `Firmware` 仓库根目录 `LICENSE` |
| 文档与课程资料 | 逐项单独标注 | 含 CC BY-NC 等非商业限制的材料不随开源包分发，仅外链并注明 |

- **变体必须写全**：CERN-OHL-P-2.0 第 7.3 条规定，未写明变体会被默认按 CERN-OHL-S（强互惠）解释；所有对外声明一律使用 `CERN-OHL-P-2.0 / Version 2 - Permissive` 全称。
- **商标与认证**：两个协议都不授予「漂移驴车 / DonkeyDrift」名称、Logo、商标或「官方认证套件」资格，使用须经社区委员会书面批准，非官方版本须标注「非官方认证」。
- **生效边界**：Apache-2.0 授权不可撤销。此前已按 Apache-2.0 取得本设计的接收方，其已获授权不追溯变更；历史全文存档于 [LICENSE-Apache-2.0.archive.txt](LICENSE-Apache-2.0.archive.txt)。
- **版权主体与 Notice**：详见 [NOTICE.md](NOTICE.md)；最终署名以社区委员会书面决议为准。

完整发布口径与四处一致性检查见《漂移驴车-华秋开源发布准备方案》v1.1 第 4.2、4.7 节。

***

## 社区与贡献

漂移驴车社区邀请所有热爱技术、勇于创新的你加入！

- **问题反馈**：提交 Issue
- **贡献指南**：欢迎提交 Pull Request
- **联系方式**：<contact@donkeydrift.com>

***

> 因为热爱，所以极致。
>
> **漂移驴车社区，与您一同驶向智能车的未来！**

