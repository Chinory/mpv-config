# mpv——全世界最好的视频播放器——的配置

先说重点：
- 这是我自己常用的 `mpv` 配置，目标是「看番更爽、调速更快、Anime4K 一键切换」。
- 如果你也喜欢边看边调速，这套按键会很顺手。
- 如果你 GPU 不太强，也能跑（默认就是偏稳的组合）。

> 我可太喜欢mpv的进度条了，不需要特别精确的纵轴定位，但横轴反馈却特别准确，允许微调，就比如一秒前闪过一个画面没看清，就很容易拖着进度条找到，而且无论怎么折腾都反应迅速，没有那种每动一下都让播放器被迫重载一大段画面的愚钝感。

## 一眼看懂：这份配置干了什么

| 项目 | 效果 |
| :--- | :--- |
| 默认全屏 | 启动直接沉浸式看片（`fs=yes`） |
| 大缓存 | 网络播放更稳（`cache=yes` + 大 `demuxer` 缓存） |
| 字幕偏好 | 默认优先中文字幕（`slang=zh`） |
| 截图目录 | 自动存到 `~/Pictures/mpv` |
| 变速体验 | 滚轮/按键快速调速，最高可秒切到 `10x`，并保持声调 |
| Anime4K | `Ctrl+1~6` 切换不同画质模式，`Ctrl+0` 一键清空 |

## 目录结构

```text
.
├── mpv.conf          # 主配置
├── input.conf        # 快捷键映射（重点）
├── scripts/
│   └── autoload.lua  # 自动加载同目录媒体到播放列表
├── shaders-low/      # 偏性能友好的一套 Anime4K Shader
└── shaders-high/     # 偏高画质的一套 Anime4K Shader
```

## 安装方式

### 方式 1：直接克隆（推荐）

```bash
git clone https://github.com/Chinory/mpv-config ~/.config/mpv
```

### 方式 2：只拷配置文件

把这几个东西放进你的 `~/.config/mpv`：
- `mpv.conf`
- `input.conf`
- `scripts/autoload.lua`
- `shaders-low/`（至少这个要有）

## 快捷键（魔改重点）

| 按键 | 功能 |
| :--- | :--- |
| `滚轮上 / ]` | `+0.5x` |
| `滚轮下 / [` | `-0.5x` |
| `Home` / `鼠标后退键` | 速度设为 `1.0x` |
| `End` / `鼠标前进键` | 速度设为 `10.0x` |
| `PgUp` / `PgDn` | `-5s / +5s` 精简跳转 |
| `Ctrl+1~6` | 切换 Anime4K 模式（Fast 组合） |
| `Ctrl+0` | 清空 GLSL Shader |

## Anime4K 模式说明

当前启用的是 `shaders-low` 路线（更吃得消）：
- `Ctrl+1` Mode A (Fast)
- `Ctrl+2` Mode B (Fast)
- `Ctrl+3` Mode C (Fast)
- `Ctrl+4` Mode A+A (Fast)
- `Ctrl+5` Mode B+B (Fast)
- `Ctrl+6` Mode C+A (Fast)
- `Ctrl+0` 关闭 Shader

`input.conf` 里也保留了 `shaders-high` 的注释版绑定，机器够强可以自己切过去。

## 小提醒

1. Anime4K 很看 GPU 性能，掉帧就降一级模式。
2. 调速到 `10x` 真的很快乐，但不适合认真看剧情（会错过老婆台词）。
3. `autoload.lua` 会自动把同目录文件加入播放列表，连播党友好。

