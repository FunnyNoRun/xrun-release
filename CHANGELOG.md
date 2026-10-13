# 更新日志

本文件记录 x-run-cli 的版本变更。格式参考 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)，
版本号遵循[语义化版本](https://semver.org/lang/zh-CN/)。

发布时，每个 Release 的正文会自动取自本文件对应版本段落；
公开仓库（[FunnyNoRun/xrun-release](https://github.com/FunnyNoRun/xrun-release)）
上的发布版为「限时版」，**自构建起 14 天有效**，过期后请到该仓库下载最新版本。

## v0.1.5 - 2026-10-13

### 修复

- `contact`：修复私信面板与常规 IM 不一致的头像布局 —— 对方头像现在贴齐中间分割线、
  自己的头像贴齐最右（此前两者都因列坐标换算错误而错位）；短消息正文也会主动让出
  头像列，不再压到头像上。
- `contact`：修复首次进入时第一个会话显示「暂无消息」、需要切走再切回才加载的问题
  （现在进入即加载当前选中的会话）。
- `contact`：修复切换会话或每敲一个字符时头像反复重载闪烁的问题 —— 头像解码 / 编码
  结果改为缓存，整帧绘制包进终端「同步刷新」一次性提交。
- `contact`：底部输入框改成带边框的多行输入栏，更容易看清。
- `contact`：消息加载失败不再静默，底部提示失败原因，并可用 Ctrl-R 重试。

### 新增

- `contact`：全屏私信面板 —— 左侧会话列表（含最后一条消息摘要）、右侧消息流、底部输入框，
  支持 ↑↓ 选择、Enter 打开/发送、鼠标点击与滚轮、Ctrl-N 新建会话、Ctrl-R 刷新、Esc 退出。
  自己的消息右对齐、对方的左对齐；消息之间留空行。会话与消息按 uid 补齐昵称，
  终端支持内联图片（kitty / iTerm2 / Sixel）时显示头像，不支持则静默降级。
- 登录成功（qqlogin / wxlogin）后展示自己的头像（终端支持时）。
- `msg`：私信命令 —— `msg send` 发消息、`msg history` 消息记录、`msg list` 会话列表。
- `social`：个人主页三件套 —— `social nickname` 改昵称、`social avatar` 改头像
  （自动上传图片到 OSS）、`social post` 发动态。

## [v0.1.4] - 2026-10-13

### 新增

- `rank`：新增排行榜命令，查看乐跑排行榜。
- `courses`：新增 `class` 系列命令，浏览本学期全部课程。
- `version`：新增版本命令，展示版本号与限时版剩余有效期。

### 变更

- 终端二维码支持内联图片，并收窄白边。

### 发布

- 发布拆分为两套产物：私有仓库保留完整发布（永久可用），
  公开仓库 `xrun-release` 发布限时版（14 天有效期，构建期注入时间戳）。
- 两处 Release 正文均同步本 CHANGELOG 的对应版本说明。

## [v0.1.3] - 2026-10-12

### 新增

- `identity`：登录后拉取并展示个人信息。

### 修复

- `runner`：修复跑步时间 / 速度 / 里程限制。

### 变更

- `ui`：优化 TUI 显示。

## [v0.1.2] - 2026-10-11

### 新增

- `history`：跑步 / 签到历史本地缓存与增量同步。

### 修复

- `ui`：交互选择器首行被宽缩进。

## [v0.1.1] - 2026-10-11

### 新增

- `qqlogin` / `wxlogin`：QQ 扫码登录、微信扫码登录（集成 weauth 协议引擎）。
- `run`：跑步流程（轨迹导入、时间 / 速度 / 里程限制、服务器时间窗校验）。
- `sign`：签到与体育课，统一「先选地点后选历史」流程。
- 固定设备指纹、`lp_token` 自动续期与基础配置管理。
- 美化 TUI，新增历史记录驱动的跑步 / dump / set-track。

### 修复

- `qqlogin`：带上扫码会话 cookie，修复扫码无回调。
- 登录支持 `--accesstoken`，并按服务器语义重做签到点字段。
- 微信凭据获取后退出车载版登录。

### 构建

- weauth 协议改为静态链接，六端统一交叉编译。

[未发布]: https://github.com/FunnyNoRun/x-run-cli/compare/v0.1.4...HEAD
[v0.1.4]: https://github.com/FunnyNoRun/x-run-cli/compare/v0.1.3...v0.1.4
[v0.1.3]: https://github.com/FunnyNoRun/x-run-cli/compare/v0.1.2...v0.1.3
[v0.1.2]: https://github.com/FunnyNoRun/x-run-cli/compare/v0.1.1...v0.1.2
[v0.1.1]: https://github.com/FunnyNoRun/x-run-cli/compare/aebffce...v0.1.1
