# OpenClaw 安装记录

**安装日期：** 2026年4月18日  
**版本：** OpenClaw 2026.4.15 (041266a)

## 安装步骤

### 1. 切换到工作目录

```powershell
PS C:\Users\ZZ1704> cd f://workarea
PS F:\workarea> cd F://openclaw
```

### 2. 设置环境变量

```powershell
PS F:\openclaw> $env:OPENCALW_HOME="F://workarea"
```

**注意：** 这里环境变量名称有拼写错误，应该是 `OPENCLAW_HOME` 而不是 `OPENCALW_HOME`

### 3. 执行初始化命令

```powershell
PS F:\openclaw> pnpm exec openclaw onboard
```

## 遇到的问题

### 问题1：无法直接执行 openclaw 命令

尝试查看版本时，直接使用 `openclaw` 命令无法识别：

```powershell
PS F:\openclaw> openclaw -v
openclaw : 无法将"openclaw"项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保
路径正确，然后再试一次。
所在位置 行:1 字符: 1
+ openclaw -v
+ ~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (openclaw:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS F:\openclaw> openclaw -version
openclaw : 无法将"openclaw"项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保
路径正确，然后再试一次。
所在位置 行:1 字符: 1
+ openclaw -version
+ ~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (openclaw:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS F:\openclaw> npm list -g openclaw
D:\npm-global
`-- (empty)

PS F:\openclaw> openclaw --version
openclaw : 无法将"openclaw"项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保
路径正确，然后再试一次。
所在位置 行:1 字符: 1
+ openclaw --version
+ ~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (openclaw:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException

PS F:\openclaw> openclaw version
openclaw : 无法将"openclaw"项识别为 cmdlet、函数、脚本文件或可运行程序的名称。请检查名称的拼写，如果包括路径，请确保
路径正确，然后再试一次。
所在位置 行:1 字符: 1
+ openclaw version
+ ~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (openclaw:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

**解决方案：** 需要使用 `pnpm exec` 前缀来执行 openclaw 命令

```powershell
PS F:\openclaw> pnpm exec openclaw --version
OpenClaw 2026.4.15 (041266a)
```

## 待补充内容

- onboard 命令的执行结果
- 其他安装步骤和配置
- 最终的安装验证

---

*文档持续更新中...*
