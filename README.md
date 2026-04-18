<p align="center">
 <img width="100px" src="assets/logo.png" align="center" alt="Logo" />
 <h2 align="center">UCDT Analysis Core</h2>
 <p align="center">CLI 优先的中观尺度城市形态分析工具，附带桌面 GUI</p>
</p>
<p align="center">
 <a href="https://github.com/buildingdata/ucdt-analysis-core"><img alt="Github" src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white" /></a>
 <img alt="Windows" src="https://img.shields.io/badge/Windows-0078D6?style=for-the-badge&logo=windows&logoColor=white" />
 <img alt="Python" src="https://img.shields.io/badge/Python-3.12+-3776AB?style=for-the-badge&logo=python&logoColor=white" />
</p>

## 概述

> [!IMPORTANT]
> 本项目以 **CLI 为核心接口**。GUI 是对同一套 core 服务的封装，不允许偏离 CLI 行为。

UCDT Analysis Core 从建筑多边形数据集按 `grid_id` 计算中观尺度城市形态指标。支持 `GPKG` 与 `GeoJSON` 输入，使用 `GeoPandas` 进行空间处理，并提供基于 `Streamlit + pywebview` 的 Windows 桌面 GUI。

## 功能特性

- CLI 作为权威接口
- 支持 `GPKG` 和 `GeoJSON` 输入（推荐 GPKG）
- 按 `grid_id` 分组计算指标
- 内置指标：`MLI`、`MBF`、`MBI`、`FAR`、`BCR`、`MHT`、`WSC`、`UHT`
- 桌面 GUI：无需外部浏览器，启动时展示 Logo + Loading 动画
- 侧边栏布局：分析层级、主题切换、硬件信息、版权版本
- 自动 / 浅色 / 深色 主题切换并持久化
- 空间概览按建筑类型（`building_type_level2`）染色并显示图注
- 导入文件后悬停显示圆形删除按钮
- 版本号集中管理，Nuitka 单文件打包

## 项目结构

```text
ucdt-analysis-core/
├── core/                # 核心指标引擎、元数据、设置、I/O
│   └── metrics/         # 指标实现
├── cli/                 # Typer CLI
├── ui/                  # Streamlit GUI、主题、样式
├── launcher/            # pywebview 桌面启动器（含 Loading 页）
├── assets/              # logo 和 favicon
├── example-input-data/  # 示例输入数据
├── build/               # 打包脚本
├── GUIDE.md             # 中文使用指南
├── AGENTS.md            # AI 代码规范
├── ARCHITECTURE.md      # 架构文档（英文）
├── TASKS.md             # 任务状态（英文）
└── INTERFACE.md         # 接口契约（英文）
```

## 快速开始

### 1. 安装依赖

```powershell
uv sync
```

### 2. 检查示例数据

```powershell
uv run ucdt inspect --input .\example-input-data\e105_n35_e110_n30_0_0_1.gpkg --layer buildings
```

### 3. 计算指标

```powershell
uv run ucdt compute --input .\example-input-data\e105_n35_e110_n30_0_0_1.gpkg --layer buildings
```

### 4. 启动桌面 GUI

```powershell
uv run ucdt-gui
```

## GUI 布局

侧边栏 + 工作区布局：

- **侧边栏**
  - 品牌区（Logo + 产品名称）
  - 分析层级选择
  - 主题设置（自动 / 浅色 / 深色 三段式切换）
  - 硬件信息摘要
  - 底部版权与版本号
- **工作区上方**
  - 「导入数据」卡片：居中 GIS 图标、拖拽或点击导入、文件卡片悬停删除
  - 「空间概览」卡片：建筑轮廓按类型染色、推导网格叠加、类型图注
- **工作区下方**
  - 当前网格详情（grid_id 选择器、建筑数量、推导面积）
  - 指标结果卡片（值 + LaTeX 公式）

## 打包

使用提供的 PowerShell 脚本：

```powershell
.\build\build-onefile.ps1
```

## 说明

- 若源数据未提供显式网格多边形，程序将从建筑范围推导展示用网格几何。
- GitHub Release 在线更新检查暂未接入，版权区版本号已预留扩展入口。

## 文档

- 英文 AI 向文档：[`AGENTS.md`](AGENTS.md) · [`ARCHITECTURE.md`](ARCHITECTURE.md) · [`TASKS.md`](TASKS.md) · [`INTERFACE.md`](INTERFACE.md)
- 中文使用指南：[`GUIDE.md`](GUIDE.md)
