# Skills Updater

管理、更新和发现 Claude Code 技能，支持多种安装来源。

[English](README.en.md)

## 功能特性

- **更新检查** - 扫描已安装技能，检查可用更新
- **自动安装** - 市场更新后自动重新安装受影响的技能
- **技能推荐** - 从 skills.sh 发现热门技能
- **国际化支持** - 自动检测语言环境（中文/英文）

## 安装

将 `skills-updater` 文件夹复制到 Claude Code 技能目录：

```bash
cp -r skills-updater ~/.claude/skills/
```

或通过 marketplace 安装（如可用）：

```bash
claude /install skills-updater@<marketplace>
```

## 快速开始

### 检查更新

```bash
python ~/.claude/skills/skills-updater/scripts/check_updates.py
```

输出示例：
```
📦 已安装技能状态
━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ 已是最新 (15):
   • skill-creator@daymade-skills (1.2.2)
   ...

⬆️ 有可用更新 (2):
   • document-skills@anthropic-agent-skills
     本地: e5c60158 → 远程: 69c0b1a0
```

### 更新市场并自动安装

```bash
# 更新市场仓库并重新安装受影响的技能
python ~/.claude/skills/skills-updater/scripts/update_marketplace.py anthropic-agent-skills --auto-install
```

输出示例：
```
📡 正在获取远程更新...

当前提交: e5c60158df67
远程提交: 69c0b1a06741
状态: 落后 6 个提交

📦 受影响的技能: document-skills

📥 正在更新市场: anthropic-agent-skills
✅ 市场更新成功

🔄 正在重新安装受影响的技能...
   ✅ 已安装: document-skills
```

### 发现新技能

```bash
python ~/.claude/skills/skills-updater/scripts/recommend_skills.py
```

## 语言支持

自动从环境变量检测（`LANG`、`LC_ALL`），或手动指定：

```bash
# 中文
python scripts/check_updates.py --lang zh

# 英文
python scripts/check_updates.py --lang en
```

## 脚本说明

| 脚本 | 功能 |
|------|------|
| `check_updates.py` | 扫描并对比已安装与远程版本 |
| `update_marketplace.py` | 更新市场仓库并自动重装技能 |
| `recommend_skills.py` | 获取热门技能推荐 |
| `i18n.py` | 国际化模块 |

## 详细文档

查看 [SKILL.md](SKILL.md) 获取完整文档，包括：
- 完整工作流指南
- 版本检测方法
- 智能合并策略
- 错误处理
- 添加新语言

## 支持的市场

查看 [references/marketplaces.md](references/marketplaces.md) 获取完整列表。

**官方：**
- `anthropics/skills` - Anthropic 示例技能
- `anthropics/claude-plugins-official` - 官方插件

**社区：**
- `daymade/claude-code-skills` - 社区技能集合
- `obra/superpowers-marketplace` - 扩展能力
- `skills.sh` - npx 技能排行榜

## 许可证

MIT
