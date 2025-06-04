# HM Gothic (鸿盟细黑 / 鴻盟細黑)

HM Gothic 是一个从 [Sarasa Gothic](https://github.com/be5invis/Sarasa-Gothic) 修改而来的字体构建流程，基于 [Inter](https://github.com/rsms/inter)、[Iosevka](https://github.com/be5invis/Iosevka) 和 [HarmonyOS Sans](https://developer.huawei.com/consumer/cn/design/resource/) 字型设计，适合在中英文之间混排的场景使用，主要用于操作系统页面和编程字体。

> [!CAUTION]
> 本仓库仅开源过程。不得在公开场合宣传本字体的任何信息。
> 由于部分字体的协议写明”不得对其任何单个组件进行任何修改“，使用可能存在风险。如果侵犯到您的权益，请发 issue 告知删除。
>
> 查看更多：https://blog.xinshijiededa.men/font-license/

## 安装说明

强烈建议在更新此字体前，完全卸载已安装的旧版字体。许多操作系统或软件的字体缓存系统在处理大型TTC字体时可能会遇到问题。

## 如何下载

~~进入[最新发布版本](https://github.com/xrgzs/HM-Gothic/releases)页面，根据需要下载对应系列的字体包，下载后解压并安装。~~

由于部分字体的协议限制和性能问题，原则上不提供下载，需要您自行下载构建。您需要承担一切风险。

## 下载说明

HM Gothic 提供了多种字形风格、字重的组合，以满足不同的场景和需求。对于仅需安装作为编程字体的用户，推荐选择 "Mono SC"。下载后，在 IDE 设置字体为 `等距鸿盟细黑 SC`。

### 字型(Variant)

**鸿盟细黑**  
西文字符基于 [Inter](https://github.com/rsms/inter) 字型设计。

- Gothic: 标准字型，全宽引号。
- UI: 专为UI界面设计的字型，半宽引号。

**等距鸿盟细黑**  
西文字符基于 [Iosevka](https://github.com/be5invis/Iosevka) 字型设计。

- Mono: 等宽字型，全宽破折号。
- Term: 等宽字型，半宽破折号。
- Fixed: 等宽字型，半宽破折号，无连字。

**Slab**: 粗衬线体。在原字形基础上增加了 Slab serif 的特征，使其更具有辨识度。

**连字** (Ligature) 遇到特定连续的字符时会进行组合，优化阅读体验。在编程语言中，连字特性也能让数学运算符号更容易的阅读，如输入 `!=` 时，会显示为 `≠`

### 地区语言(Variant)

根据特定语言和地区主要使用的字形来选择字体。

- `SC`: 简体中文
- `TC`: 台湾繁体中文
- `CL`: 传统旧字形

### 其他说明

**Unhinted**: 没有进行微调字形的版本，也就是使用 Iosevka 和 HarmonyOS Sans 原版的字形。 文件大小比其他版本更小，但可能在某些字的结构上，显示没那么清晰，特别是小字号效果更为不佳。仅需要在极端的环境中，需要更小的字体文件，且不在意字体的显示清晰效果时选择。一般用户建议不选。

> [!IMPORTANT]
> HarmonyOS Sans 原版字体无 hint。此字体不需要进行 hint 就可以在低分屏上获得较好的显示效果，且进行 hint 需要花费大量时间和算力，因此不启用 hint 版本。
>
> 如需启用 hint，可在 `verdafile.mjs`、`tools/generate-release-notes.mjs` 中取消注释。请确保您的 CPU 和内存足够强大，并且有足够的耐心等待。

**TTF**: 如果不知道怎么选，选 TTF 肯定没错。但 TTF 通常体积较大。旧系统用户可选。

**TTC**: 相当于一个字体压缩包，在里面塞了很多个 TTF 的字体文件，可以包含多个 TrueType 字体的文件格式。好处就是，让文件更小。

**SuperTTC**: 是 TTC 的升级版，有更高效的打包方式，可以往里面塞更多的可变字体。进一步节省空间。

## 从源文件创建字体

### 要求

安装 [Node.js](https://nodejs.org/en/)、[AFDKO](https://github.com/adobe-type-tools/afdko) 和 [ttfautohint](https://www.freetype.org/ttfautohint)

将项目下载到本地。仓库历史记录较大，建议使用 GitHub Download Zip 仅下载最新版本。

```bash
wget https://github.com/xrgzs/HM-Gothic/archive/refs/heads/dev.zip
unzip dev.zip
cd HM-Gothic-dev
```

从终端进入项目文件夹运行以下命令，安装依赖。

```bash
pnpm install
```

### 修改生成信息

可按需更改 `config.json` 文件中的信息。比如精简构建的字重等等。

### 生成字体文件

生成 TTF 文件, 将会导出到 `out/ttf` 目录。

```bash
pnpm run build ttf
```

生成 TTC 文件，将会导出到 `out/ttc` 目录。

```bash
pnpm run build ttc
```

请注意，打包 TTC 时将会占用 _非常高_ 的内存，因为包含了大量的子家族字符集的组合。

构建所有字体，将会导出到 `out` 目录。

```bash
pnpm run build all
```

## 安装说明

具体安装略。

### 替换 Windows 系统字体

使用 https://github.com/GuiWonder/WeiFonts 可将字体转换为指定字体的代替字体。然后将电脑重启到 WinRE 或者 WinPE 环境下，备份之前的字体，将处理好的字体替换到 `C:\Windows\Fonts` 下即可。
