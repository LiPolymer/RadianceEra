<div align="center">

# RadianceEra (光辉纪元)

<img src="icon.png" alt="RadianceEra Logo" width="600">

**基于 [Radiance](https://github.com/Minecraft-Radiance/Radiance) 的 Minecraft Java 版硬件光追开箱即用整合包**

[GitHub 仓库](https://github.com/LiPolymer/RadianceEra) · [GitLab 仓库](https://gitlab.com/LiPolymer/RadianceEra) · [下载整合包](https://github.com/LiPolymer/RadianceEra/releases/latest)

</div>

## 项目简介

[Radiance](https://github.com/Minecraft-Radiance/Radiance) 是为 Minecraft Java 版带来原生硬件光线追踪（Hardware Ray Tracing）的 Fabric 模组。

由于 Radiance 需要配置特定的原生依赖库（如 NVIDIA DLSS 运行库）和适配的材质包，手动配置较为繁琐。**RadianceEra** 预先完成了所有依赖与资源配置，打包为标准的 `.mrpack` 格式，支持主流启动器一键导入，安装即玩。

### 包含内容

| 类别 | 组件 | 说明 |
| :--- | :--- | :--- |
| **基础环境** | Minecraft `1.21.4` + Fabric Loader | 基础运行平台 |
| **核心模组** | Radiance (`0.1.6-alpha`) | 硬件光追渲染模组（提供 Windows / Linux 版本） |
| **辅助模组** | Fabric API, Mod Menu | 前置依赖与模组设置界面 |
| **运行时** | NVIDIA DLSS (v310.9.1) | 包含 DLSS、DLSS-D (光线重建)、DLSS-G 动态库 |
| **配套材质** | Simple PBR (SPBR) 材质包 | 提供发光矿石、视差草地、镜面反射等 PBR 效果 |

## 运行要求

- **显卡与驱动**：NVIDIA GeForce RTX 系列显卡（需支持 Vulkan 硬件光线追踪；开启 DLSS 需 RTX 显卡），建议安装最新版 NVIDIA 显卡驱动。
- **独显运行（重要）**：笔记本或双显卡用户必须确保游戏使用**高性能独立显卡**运行（集成显卡不支持硬件光追，会导致崩溃或无法开启光追）。
- **运行内存**：光线追踪与 PBR 材质内存消耗较大，建议在启动器中分配 **6 GB - 8 GB** 或更高最大内存（`-Xmx`）。
- **操作系统**：Windows 10 / 11 (64-bit) 或 Linux (x86_64)。
- **Java 环境**：Java 21（启动器自动下载的运行时通常即可）。

## 下载与安装

### 1. 下载整合包
前往 [Releases 页面](https://github.com/LiPolymer/RadianceEra/releases/latest) 下载对应系统的 `.mrpack` 文件：

- **Windows**：`RadianceEra_<版本>_Windows.mrpack`
- **Linux**：`RadianceEra_<版本>_Linux.mrpack`

> **说明**：若网络环境下载模组依赖较慢，可选择带有 `offline` 标识的离线整合包。

### 2. 导入启动器
主流第三方启动器均支持 `.mrpack` (Modrinth) 格式：
- **Prism Launcher / Modrinth App**：点击「添加实例」→「从文件导入」选择 `.mrpack` 文件。
- **PCL2 (Plain Craft Launcher 2)**：直接将 `.mrpack` 文件拖入启动器窗口，或在「版本选择」中点击导入。
- **HMCL (Hello Minecraft! Launcher)**：点击「安装新游戏版本」→「导入整合包」。

### 3. 启动前配置与运行
1. 在启动器的实例设置中，将**最大分配内存**调至 **6 GB 或以上**。
2. 确保已指定使用**独立显卡**运行游戏。
3. 启动游戏即可体验。

## 常见问题与排查 (FAQ)

### 1. 双显卡 / 笔记本用户提示不支持光追或崩溃
**原因**：系统默认调用了 CPU 集成显卡（核显），核显缺少 Vulkan 硬件光线追踪支持。  
**解决方案**：
- **Windows**：在「Windows 设置」→「系统」→「屏幕」→「显示卡」或「NVIDIA 控制面板」中，为当前启动器所使用的 Java 路径（`javaw.exe`）指定「高性能 NVIDIA 处理器」。
- **Linux**：使用 PRIME 渲染卸载（如 `prime-run`）或显卡切换工具启动启动器及游戏。

### 2. Windows 启动游戏闪退 / 崩溃（MSVC 运行库冲突）
**原因**：部分 JDK / JRE（如启动器自带的旧运行时）内置的 VC++ 动态链接库较旧，会触发已知的 [MSVC mutex 冲突问题](https://stackoverflow.com/questions/78598141/first-stdmutexlock-crashes-in-application-built-with-latest-visual-studio)，导致 Radiance 初始化崩溃。  
**解决方案**：
1. 下载并安装最新的 [Microsoft Visual C++ Redistributable (X64)](https://learn.microsoft.com/zh-cn/cpp/windows/latest-supported-vc-redist?view=msvc-170)。
2. 打开启动器中为游戏配置的 JDK 目录下的 `bin` 文件夹（例如 `${JAVA_HOME}/bin/`）。
3. 查找并**删除或重命名**以下三个文件（让 JDK 自动调用系统全局最新的 VC++ 运行库）：
   - `msvcp140.dll`
   - `vcruntime140.dll`
   - `vcruntime140_1.dll`

## 本地构建

本项目使用 [ShulkerRDK](https://github.com/LiPolymer/ShulkerRDK) 进行自动化打包。

### 前置环境
- Git
- [.NET 8.0 SDK](https://dotnet.microsoft.com/download/dotnet/8.0) 或更高版本

### 构建步骤
```bash
# 1. 克隆仓库
git clone https://gitlab.com/LiPolymer/RadianceEra.git
cd RadianceEra

# 2. 赋予脚本执行权限（Linux / macOS）
chmod +x ./srdk

# 3. 执行构建（在线包）
./srdk build

# 若需构建离线完整包：
./srdk build_offline
```

构建产物将保存在 `build/` 目录下。

## 鸣谢与许可

- [Radiance](https://github.com/Minecraft-Radiance/Radiance) — Minecraft Java 版硬件光追模组
- [ShulkerRDK](https://github.com/LiPolymer/ShulkerRDK) — 整合包构建与工程化工具

本项目基于 [MIT License](LICENSE) 开源。
