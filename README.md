<div align=center>
  <h1>
  RadianceEra 光辉纪元
  </h1>

  <img src="icon.png" alt="RadianceEra Icon">

[![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](https://github.com/LiPolymer/RadianceEra)
[![GitLab](https://img.shields.io/badge/GitLab-FC6D26?logo=gitlab&logoColor=fff)](https://gitlab.com/LiPolymer/RadianceEra)



  <p>
    <strong>里程碑式的 Mod <a href="https://github.com/Minecraft-Radiance/Radiance">Radiance</a> 发布，Minecraft Java 终于迎来了硬件光线追踪的时代。</strong>
  </p>
  <p>本 Mod 包旨在解决环境配置问题，让大家都能轻松体验到这款划时代的 Mod。</p>
</div>

## 简介

**RadianceEra（光辉纪元）** 是为 [Radiance](https://github.com/Minecraft-Radiance/Radiance) 打造的即开即用整合包。Radiance 是首个为 Minecraft Java Edition 实现硬件光线追踪的 Mod，让方块世界也能拥有媲美 3A 大作的光影效果。

本整合包预配置了所有必需的依赖项和 DLSS 库，用户无需手动折腾环境，安装即玩。

## 特性

- **开箱即用** — 自动下载安装 Radiance Mod 及所有必需依赖
- **跨平台支持** — 同时提供 Windows 和 Linux 版本
- **提供 .mrpack 格式** — 支持主流启动器一键安装

## 下载并安装

1. 前往 [GitHub Releases](https://github.com/LiPolymer/RadianceEra/releases/latest) 页面
2. 根据你的操作系统下载对应的文件：
   - **Windows 用户** → 下载带有 `Windows` 字样的 `.mrpack` 文件或者同时带有 `offline` 字样的离线包
   - **Linux 用户** → 下载带有 `Linux` 字样的 `.mrpack` 文件或者同时带有 `offline` 字样的离线包
3. 将下载的 `.mrpack` 文件导入支持 Modrinth 格式的启动器即可自动完成安装（大部分主流启动器都支持）

### Windows 修复：调整 JDK 运行时库

由于一个已知的 [MSVC 问题](https://stackoverflow.com/questions/78598141/first-stdmutexlock-crashes-in-application-built-with-latest-visual-studio)，JDK 自带的某些库可能导致 Radiance Mod 启动时崩溃。

如果遇到此问题，可尝试以下解决方案：

1. 找到 JDK 的 `bin` 文件夹（`${PATH_TO_JDK}/bin`），对其中的 `msvcp140.dll`、`vcruntime140.dll` 和 `vcruntime140_1.dll` 进行重命名或删除操作，使这些文件在该目录下不复存在。这一步旨在移除 JDK 对这些旧版本库的依赖。
2. 安装[最新的 Microsoft Visual C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170)，选择版本 `Latest supported v14 (for Visual Studio 2017–2026)`。这一步让 JDK 依赖系统最新的运行时库。

## 构建本项目

- .NET 8.0 及以上运行环境
- Git

```bash
# 克隆本仓库 (GitHub/GitLab)
git clone https://gitlab.com/LiPolymer/RadianceEra
# 开始构建 (Linux / macOS 中您可能需要授予SRDK可执行权限 chmod +x ./srdk)
./srdk build
```

构建产物将输出到 `build/` 目录

本项目持续集成及构建打包由 [ShulkerRDK](https://github.com/LiPolymer/ShulkerRDK) 强力驱动

## 致谢

- [**Radiance**](https://github.com/Minecraft-Radiance/Radiance) — 划时代的光线追踪 Mod

## 许可证

本项目基于 [MIT](LICENSE) 获得许可。

---

<div align=center>
  <p><i>让 Minecraft 的光辉纪元，从此刻开启。</i></p>
</div>

