# OpenClaw 安装常见问题

## 命令执行问题

### Q: 为什么执行 `openclaw` 命令提示"无法识别"？

**A:** OpenClaw 通过 pnpm 本地安装，需要使用 `pnpm exec` 前缀：

```powershell
pnpm exec openclaw --version
pnpm exec openclaw onboard
```

### Q: 如何查看 OpenClaw 版本？

**A:** 使用以下命令：

```powershell
pnpm exec openclaw --version
```

### Q: 每次都要输入 `pnpm exec` 太麻烦，有简化方法吗？

**A:** 可以在 `package.json` 中添加脚本别名：

```json
{
  "scripts": {
    "oc": "openclaw"
  }
}
```

然后使用：
```powershell
pnpm oc --version
```

---

## 环境配置问题

### Q: 环境变量应该设置为什么？

**A:** 设置 `OPENCLAW_HOME` 环境变量（注意拼写）：

```powershell
$env:OPENCLAW_HOME="F://workarea"
```

**注意**：不是 `OPENCALW_HOME`，中间有字母 L。

---

*持续更新中...*
