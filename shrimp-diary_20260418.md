# OpenClaw 安装日记

## 2026年04月18日

### 环境信息
- **系统**: Windows 11 Home China 10.0.26100
- **Shell**: PowerShell
- **工作目录**: F:\openclaw
- **OpenClaw 版本**: 2026.4.15 (041266a)
- **包管理器**: pnpm

### 安装过程

#### 1. 初始设置

切换到工作目录并设置环境变量：

```powershell
PS C:\Users\ZZ1704> cd f://workarea
PS F:\workarea> cd F://openclaw
PS F:\openclaw> $env:OPENCALW_HOME="F://workarea"
```

**注意**: 环境变量名称拼写错误，应该是 `OPENCLAW_HOME` 而不是 `OPENCALW_HOME`

#### 2. 执行初始化

```powershell
PS F:\openclaw> pnpm exec openclaw onboard
```

### 遇到的问题

#### 问题1：无法直接执行 openclaw 命令

**问题描述**: 尝试查看 OpenClaw 版本时，直接使用 `openclaw` 命令无法识别

**尝试的命令**:
```powershell
PS F:\openclaw> openclaw -v
PS F:\openclaw> openclaw -version
PS F:\openclaw> openclaw --version
PS F:\openclaw> openclaw version
PS F:\openclaw> npm list -g openclaw
```

**错误信息**:
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

**解决方案**:

使用 `pnpm exec` 前缀来执行 openclaw 命令：

```powershell
PS F:\openclaw> pnpm exec openclaw --version
OpenClaw 2026.4.15 (041266a)
```

**经验总结**:
- OpenClaw 通过 pnpm 本地安装，不在全局 PATH 中
- 所有 openclaw 命令都需要使用 `pnpm exec openclaw` 前缀
- 这是 pnpm 的特性，本地依赖不会自动添加到全局命令

---

*持续更新中...*
