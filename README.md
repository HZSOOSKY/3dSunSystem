# 太阳系 3D 可视化 · 3dSunSystem

基于 three.js 的浏览器端 3D 可视化：真实开普勒轨道根数驱动的太阳系状态展示与演进系统。

## 在线访问

**https://hzsoosky.github.io/3dSunSystem/**

打开即用，无需安装、无需联网。建议使用桌面版 Chrome / Edge / Firefox（需支持 WebGL 2）。

## 功能

| 功能 | 说明 |
| --- | --- |
| 真实轨道 | 八大行星采用 JPL 轨道根数，任意时刻位置由开普勒方程精确求解 |
| 时间演进 | 实时 / 分 / 时 / 天 / 月 五档倍速，支持暂停、倒放、1900–2100 日期拖动 |
| 双尺度模式 | 写实模式保持真实比例；可视化模式压缩距离、放大天体，0.6 秒平滑过渡 |
| 光效 | 太阳 FBM 噪声米粒组织 + 双层加色日冕 + 径向辉光；UnrealBloom 泛光 |
| 交互 | 射线拾取悬停高亮，点击天体 1.2 秒平滑聚焦并持续跟随 |
| 细节 | 土星环、1200 个小行星带、7000 颗恒星与银河带、卫星轨道 |
| 界面 | 天体列表、实时参数面板、时间轴、图层开关、首次引导浮层 |

操作：左键拖拽旋转，滚轮缩放，右键平移，点击天体查看详情。

快捷键：`空格` 暂停 · `R` 复位 · `F` 聚焦选中 · `1`–`8` 切换行星 · `L` 标签 · `O` 轨道线 · `H` 隐藏 UI（截图用）。

## 本仓库内容

本仓库是**在线演示站**（GitHub Pages），存放构建产物而非源码。

| 路径 | 内容 |
| --- | --- |
| `index.html` | 入口页 |
| `assets/` | 构建产物（JS / CSS，已压缩） |
| `.nojekyll` | 禁用 Jekyll 处理 |

完整开发源码、单元测试与文档归档在 `3dcodinglabs` 仓库的 `projects/3dSunSystem/`。

## 本地运行源码

```bash
git clone https://github.com/HZSOOSKY/3dcodinglabs.git
cd 3dcodinglabs/projects/3dSunSystem
npm install
npm run dev        # 开发服务器
npm run build      # 生产构建
npm test           # 56 个单元测试
```

## 技术栈

- [three.js](https://threejs.org/) r180（MIT）— 渲染、OrbitControls、EffectComposer + UnrealBloomPass、CSS2DRenderer
- TypeScript 5.7（strict）+ Vite 6
- 全部贴图由代码在运行时程序化生成（Canvas 2D + 值噪声 / GLSL Simplex 噪声），无外部素材依赖，完全离线可用

## 说明

- 轨道数据为 JPL《Approximate Positions of the Planets》一阶近似星历，
  1800–2050 年间位置误差小于约 10 角分，适合可视化演示，**不可用于精密轨道计算或航天任务设计**。
- 卫星采用椭圆轨道近似，不含摄动与共振项。
- 写实模式下行星退化为「点」（教学定位是展示空间关系），依赖标签与轨道线提供可读性。
- 第三方授权：three.js（MIT），版权声明保留在依赖中。

完整开发源码与文档归档在 `3dcodinglabs` 仓库的 `projects/3dSunSystem/`。
