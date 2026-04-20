# OpenClaw 故障排查指南

## 安装问题

### 问题：无法直接执行 openclaw 命令

**问题描述**

在 Windows PowerShell 中直接执行 `openclaw` 命令时，系统提示无法识别该命令。

**环境信息**
- 系统：Windows 11
- Shell：PowerShell
- 包管理器：pnpm
- OpenClaw 版本：2026.4.15 (041266a)

**错误信息**

```powershell
openclaw : 无法将"openclaw"项识别为 cmdlet、函数、脚本文件或可运行程序的名称。
请检查名称的拼写，如果包括路径，请确保路径正确，然后再试一次。
所在位置 行:1 字符: 1
+ openclaw -v
+ ~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (openclaw:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

**原因分析**

OpenClaw 通过 pnpm 安装在项目本地的 `node_modules/.bin` 目录中，而不是全局安装。因此：

1. openclaw 可执行文件不在系统的 PATH 环境变量中
2. 直接执行 `openclaw` 命令时，系统无法找到该程序
3. 这是 pnpm 的设计特性，本地依赖默认不会添加到全局命令路径

**解决方案**

#### 方案1：使用 pnpm exec（推荐）

在所有 openclaw 命令前添加 `pnpm exec` 前缀：

```powershell
pnpm exec openclaw --version
pnpm exec openclaw onboard
pnpm exec openclaw [其他命令]
```

**优点**：
- 无需修改系统配置
- 适用于所有 pnpm 管理的本地依赖
- 不会污染全局环境

#### 方案2：使用 pnpm 脚本

在项目的 `package.json` 中添加脚本：

```json
{
  "scripts": {
    "openclaw": "openclaw"
  }
}
```

然后使用：
```powershell
pnpm openclaw --version
pnpm openclaw onboard
```

#### 方案3：全局安装（不推荐）

如果确实需要全局访问：

```powershell
pnpm install -g openclaw
```

**注意**：全局安装可能导致版本冲突问题。

**相关参考**
- pnpm 官方文档：https://pnpm.io/cli/exec
- OpenClaw 文档：待补充

---
