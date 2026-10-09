# Forest

[English](README.md)

适用于 [Zed](https://zed.dev) 的墨绿色主题。关键字采用青色，类型采用黄绿色，常量、数字和布尔值分别使用不同颜色。扩展提供一个名为 **Forest** 的深色主题。

**当前状态：** 0.1.0，可通过开发扩展方式安装，尚未上架 Zed 官方扩展目录。

![Forest 在 Zed Theme Builder 中的预览](preview.jpg)

截图来自网页 Theme Builder。网页预览无法完整反映桌面端的语法分类、字重和语言服务器语义高亮；目前尚未在桌面 Zed 中人工验证安装及渲染效果。

## 安装

克隆仓库，并保留本地目录：

```sh
git clone https://github.com/lazyanubis/zed-forest.git
```

在 Zed 中打开 **Extensions**，点击 **Install Dev Extension**，选择包含 `extension.toml` 的 `zed-forest` 目录。随后在命令面板运行 **theme selector: toggle**，选择 **Forest**。详见官方[开发扩展说明](https://zed.dev/docs/extensions/developing-extensions)。

这是纯主题扩展，无需添加 Rust 代码或 WebAssembly 模块。

## 卸载

先切换到其他主题，再打开 **Extensions**，找到 **Forest** 并选择 **Uninstall**。如果手动合并过可选设置，卸载扩展不会撤回这些设置，需要自行删除或恢复。

## 主要配色

| 内容 | 颜色 |
| --- | --- |
| 编辑区背景 | `#132623` |
| 面板 | `#20403f` |
| 关键字 | `#2ea9aa` |
| 类型，加粗 | `#c6c666` |
| 常量 | `#d6ad75` |
| 数字 | `#c99577` |
| 布尔值 | `#b59bd5` |
| 变量 | `#639dd0` |
| 参数 | `#a093bd` |
| 字段 | `#6baa85` |
| 函数定义 | `#d07bd2` |
| 宏 | `#4eade5` |

主题还包含终端、诊断、选区、搜索匹配及协作配色。标识符最终采用哪种颜色，取决于语言语法和语义高亮如何识别它。

## 可选语义高亮

无需添加任何设置即可使用主题。[settings.example.json](settings.example.json) 仅供手动合并，用于增强 Rust 语义高亮和类型提示；扩展不会自动安装或应用它。

先检查内容，再将需要的字段合并到现有 Zed 设置。不要整份覆盖自己的设置文件，也不要直接替换已有语义规则。

- Rust 使用语法与语义组合高亮，并开启行内提示。
- 全局语义规则将声明、可变变量及宏映射到对应主题样式，也可能影响其他已经开启语义高亮的语言。
- 行内提示的背景设置也是全局设置，可能改变其他语言的提示背景。

支持情况取决于 Zed 版本和语言服务器，不能保证不同语言中的颜色完全一致。参考官方[语义高亮说明](https://zed.dev/docs/semantic-tokens)。

## 发布与许可

剩余人工验证及官方目录提交步骤见 [PUBLISHING.md](PUBLISHING.md)。本仓库尚未向官方目录提交发布 PR。

[MIT](LICENSE) © 2026 Anubis。
