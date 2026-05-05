<div align=center>
  <h1>
  RadianceEra 光辉纪元
  </h1>

  <img src="icon.png" alt="RadianceEra Icon">

  <p>
    <strong>里程碑式的 Mod <a href="https://github.com/Minecraft-Radiance/Radiance">Radiance</a> 发布，Minecraft Java 终于迎来了硬件光线追踪的时代。</strong>
  </p>
  <p>本 Mod 包旨在解决环境配置问题，让大家都能轻松体验到这款划时代的 Mod。</p>
</div>

## 简介

**RadianceEra（光辉纪元）** 是为 [Radiance](https://github.com/Minecraft-Radiance/Radiance) 打造的即开即用整合包。Radiance 是首个为 Minecraft Java Edition 实现硬件光线追踪的 Mod，让方块世界也能拥有媲美 3A 大作的光影效果。

本整合包预配置了所有必需的依赖项和 DLSS 库，用户无需手动折腾环境，安装即玩。

## 特性

- **开箱即用** — 预装 Radiance Mod 及所有必需依赖
- **跨平台支持** — 同时提供 Windows 和 Linux 版本
- **mrpack 格式** — 支持主流启动器一键安装

## 构建说明

本项目使用 [ShulkerRDK](https://github.com/LiPolymer/ShulkerRDK) 打包工具。

### 环境准备

- .NET SDK 8.0
- Git

### 构建步骤

```bash
# Linux / macOS
chmod +x ./srdk
./srdk build

# Windows
.\srdk.exe build
```

构建产物将输出到 `build/` 目录。

## 致谢

- **[Minecraft-Radiance](https://github.com/Minecraft-Radiance/Radiance)** — 划时代的光线追踪 Mod

## 许可证

本项目采用 [MIT License](LICENSE)。

---

<div align=center>
  <p><i>让 Minecraft 的光辉纪元，从此刻开启。</i></p>
</div>

