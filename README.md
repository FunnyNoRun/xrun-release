# Xrun

步道乐跑「Xrun」命令行工具 的公开发布仓库。

> [!tip]
> 强烈推荐使用 `Kitty` 运行本CLI工具～～  

## 限时说明

本仓库的发布版为**限时版**：从构建时刻起 **14 天**有效，过期后程序会提示并阻止运行，
请到这里下载最新版本。桌面端请直接到 [Releases](../../releases) 取对应平台压缩包。

## 下载与安装

到 [Releases](../../releases) 页面下载对应平台的压缩包，解压后即可得到单文件可执行程序。

| 平台 | 架构 | 文件名 |
| --- | --- | --- |
| Linux | x86_64 | `xrun-linux-amd64.tar.gz` |
| Linux | arm64 | `xrun-linux-arm64.tar.gz` |
| macOS | Intel | `xrun-darwin-amd64.tar.gz` |
| macOS | Apple Silicon | `xrun-darwin-arm64.tar.gz` |
| Windows | x86_64 | `xrun-windows-amd64.tar.gz` |
| Windows | arm64 | `xrun-windows-arm64.tar.gz` |


```bash
# Linux / macOS 示例
tar -xzf xrun-linux-amd64.tar.gz
chmod +x xrun-linux-amd64
./xrun-linux-amd64 --help
```

程序为纯静态单文件，无需安装任何运行库。

## 快速上手

```bash
# 1. 登录（QQ 扫码，或微信扫码）
xrun qqlogin          # 扫码绑定乐跑账号
xrun wxlogin          # 也可用微信扫码 / --refresh-token

# 2. 查看当前状态
xrun status

# 3. 跑步（交互式选区域与历史轨迹）
xrun run
xrun run --distance 3500 --time 1200     # 指定里程(米)与时间(秒)
xrun run --set-track                      # 记住本次区域+轨迹，之后沿用它

# 4. 签到
xrun sign
xrun sign --set-sign-area                 # 固定签到点，之后不再询问

# 5. 私信面板与个人主页
xrun contact                              # 全屏私信面板：会话列表 / 消息 / 输入框
xrun msg list                             # 只看会话列表（非全屏）
xrun social avatar                        # 改头像（自动上传到 OSS）
xrun me                                   # 查看个人信息
```

> [!tip]
> `xrun contact` 是全屏面板：↑↓ 选会话、Enter 打开/发送、鼠标点击与滚轮、Ctrl-N 新建、
> Ctrl-R 刷新、Esc 退出。终端支持内联图片（Kitty / iTerm2 / Sixel）时会在消息旁显示头像，
> 不支持则自动降级为纯文字。

## 常用命令

| 命令 | 说明 |
| --- | --- |
| `xrun qqlogin` / `xrun wxlogin` | QQ / 微信扫码登录并绑定乐跑账号 |
| `xrun status` | 查看登录状态、用户信息与 access_token 健康度 |
| `xrun run` | 跑步（可选区域与历史轨迹，自动生成合法参数） |
| `xrun sign` | 签到（可选签到点，支持固定默认点） |
| `xrun contact` | 全屏私信面板（会话列表 / 消息流 / 输入框，支持头像） |
| `xrun msg` | 私信：`send` 发消息、`history` 消息记录、`list` 会话列表 |
| `xrun social` | 个人主页：`nickname` 改昵称、`avatar` 改头像、`post` 发动态 |
| `xrun me` | 查看当前账号个人信息（姓名 / 学号 / 学校等） |
| `xrun profile` | 查看 / 修改本地档案（设备指纹、身份信息） |
| `xrun class` | 体育课：课程信息 / 班级成员 / 课堂签到 |
| `xrun courses` | 本学期全部课程列表 |
| `xrun rank` | 乐跑排行榜（学校榜 / 总榜，周 / 月 / 年） |
| `xrun record` | 查看 / 导出历史跑步记录 |
| `xrun track` | 管理本地跑步轨迹（导入 / 删除） |
| `xrun list_track` | 列出本地全部轨迹 |
| `xrun get_run_info` | 获取跑步区域等服务器信息 |
| `xrun list_sign_area` | 列出当前可用的签到地点 |
| `xrun zone` | 管理本地缓存的跑步区域 |
| `xrun version` | 查看版本号与剩余有效期 |

任意命令加 `-h` 查看详细参数，例如 `xrun run -h`。

## 数据目录

本地数据（登录档案、轨迹、记录、设置）默认存放在：

- Linux / macOS：`~/.config/x-run-cli/`
- Windows：`%APPDATA%\x-run-cli\`

可用 `--data-dir <路径>` 或环境变量 `XRUN_HOME` 覆盖。

## 更新日志

各版本的变更说明见 [CHANGELOG](https://github.com/FunnyNoRun/x-run-cli/blob/main/CHANGELOG.md)；
每个 Release 的正文也同步了对应版本段落。

## 免责声明

本项目仅供学习与个人研究使用，使用产生的一切后果由使用者自行承担。
