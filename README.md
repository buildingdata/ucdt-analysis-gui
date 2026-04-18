<p align="center">
 <img width="100px" src="logo.svg" align="center" alt="Logo" />
 <h2 align="center">UCDT Analysis GUI</h2>
 <p align="center">城市建筑能耗和碳排放指标分析核心 GUI</p>
</p>
<p align="center"> <img alt="version" src="https://img.shields.io/github/release/buildingdata/ucdt-analysis-gui"> <img alt="issues" src="https://img.shields.io/github/issues/buildingdata/ucdt-analysis-gui?color=F48D73"> <img alt="license" src="https://img.shields.io/github/license/buildingdata/ucdt-analysis-gui"> </p>

## 项目简介

UCDT Analysis Core 从建筑多边形数据集按 `grid_id` 计算中观尺度城市形态指标。支持 `GPKG` 与 `GeoJSON` 输入，使用 `GeoPandas` 进行空间处理，并提供基于 `Streamlit + pywebview` 的 Windows 桌面 GUI。

## 功能说明

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

## License

[GNU General Public License v3](https://github.com/buildingdata/ucdt-analysis-gui/blob/main/LICENSE)
