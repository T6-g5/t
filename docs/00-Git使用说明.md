# A3 项目 Git 使用说明

> 项目名称：基于大模型的个性化资源生成与学习多智能体系统开发
> 赛题来源：第十五届中国软件杯 A组 A3 题

---

## 一、环境检查

### 1.1 检查 Git 是否安装

```bash
git --version
```

**成功输出示例**：
```
git version 2.54.0.windows.1
```

**如未安装**：访问 `https://git-scm.com/downloads` 下载安装。

### 1.2 检查是否已初始化仓库

```bash
# 检查 .git 目录是否存在
ls -la .git  # macOS/Linux
dir .git     # Windows
```

---

## 二、初始化 Git 仓库

### 2.1 创建新仓库

```bash
# 当前目录不是 Git 仓库时执行
git init
```

**成功输出**：
```
Initialized empty Git repository in E:/pencilfile/.git/
```

### 2.2 设置用户信息

```bash
git config user.name "你的名字"
git config user.email "你的邮箱"

# 可选：设置全局用户信息（首次使用）
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

---

## 三、.gitignore 配置

### 3.1 已生成的忽略规则

项目根目录已创建 `.gitignore` 文件，包含以下规则：

```
# Node.js 项目
node_modules/
dist/
build/

# 环境变量和密钥
.env
.env.*

# 日志和临时文件
logs/
tmp/

# 系统文件
.DS_Store
*.local

# 密钥文件
api_keys.txt
api_key.json
*.key
*.secret
credentials.json
secrets.yaml
*.pem
*.cer

# 导出文件
export/
exports/
*.png
*.jpg
*.jpeg
*.pdf
*.svg

# IDE 配置
.vscode/
.idea/

# Python 项目
__pycache__/
*.pyc
*.pyo

# 包管理
*.egg-info/

# 日志文件
npm-debug.log*
yarn-debug.log*

# 测试覆盖
coverage/
```

### 3.2 修改忽略规则

如需添加新的忽略规则，编辑 `.gitignore` 文件：

```bash
# 使用编辑器打开
notepad .gitignore  # Windows
code .gitignore     # VS Code
```

---

## 四、远程仓库配置

### 4.1 推荐远程仓库平台

| 平台 | 优点 | 推荐场景 |
|------|------|---------|
| **Gitee** | 国内访问速度快，支持私有仓库 | 国内团队协作 |
| **GitCode** | 华为云出品，国内访问快 | 国内团队协作 |
| **GitHub** | 全球最大平台，开源生态好 | 国际协作、开源项目 |

### 4.2 添加远程仓库

```bash
# 添加远程仓库（替换为你的仓库地址）
git remote add origin https://gitee.com/your-name/a3-project.git
# 或
git remote add origin https://github.com/your-name/a3-project.git
```

### 4.3 验证远程仓库配置

```bash
git remote -v
```

**成功输出**：
```
origin  https://gitee.com/your-name/a3-project.git (fetch)
origin  https://gitee.com/your-name/a3-project.git (push)
```

### 4.4 推送代码到远程

```bash
# 首次推送
git push -u origin main

# 后续推送
git push
```

---

## 五、分支管理规范

### 5.1 推荐分支结构

| 分支名 | 用途 | 说明 |
|--------|------|------|
| **main** | 主分支 | 稳定版本，仅接收合并请求 |
| **dev** | 开发分支 | 日常开发，合并各 feature 分支 |
| **feature-prototype** | 原型开发 | UI 原型设计相关 |
| **feature-frontend** | 前端开发 | 前端页面和交互 |
| **feature-backend** | 后端开发 | API、数据库、业务逻辑 |
| **feature-ai** | AI 功能开发 | RAG、多智能体、大模型集成 |
| **feature-test** | 测试 | 测试用例和验证 |

### 5.2 分支操作命令

```bash
# 创建并切换到新分支
git checkout -b feature-prototype

# 查看所有分支
git branch -a

# 切换分支
git checkout dev

# 合并分支（在目标分支执行）
git checkout dev
git merge feature-prototype

# 删除分支（已合并后）
git branch -d feature-prototype
```

---

## 六、提交规范

### 6.1 推荐提交前缀

| 前缀 | 说明 | 示例 |
|------|------|------|
| **docs:** | 更新文档 | `docs: 添加赛题要求文档` |
| **feat:** | 新增功能 | `feat(profile): 实现学生画像构建` |
| **fix:** | 修复 Bug | `fix(api): 修复登录接口错误` |
| **test:** | 添加测试 | `test: 添加学生画像单元测试` |
| **chore:** | 构建/工具相关 | `chore: 更新依赖版本` |
| **refactor:** | 代码重构 | `refactor: 重构智能体调度逻辑` |
| **style:** | 代码格式 | `style: 格式化代码` |

### 6.2 提交命令

```bash
# 查看状态
git status

# 添加所有修改
git add .

# 添加指定文件
git add docs/00-Git使用说明.md

# 提交（必须使用规范前缀）
git commit -m "docs: 添加Git使用说明文档"

# 撤销提交（未推送时）
git reset --soft HEAD~1
```

---

## 七、阶段提交点规划

### 7.1 提交里程碑

| 阶段 | 提交内容 | 建议提交消息 |
|------|---------|-------------|
| **阶段 0** | 赛题要求文档 | `docs: 提取赛题要求` |
| **阶段 1** | AI 工具使用规范 | `docs: 添加AI工具使用规范` |
| **阶段 2** | PRD 文档 | `docs: 生成产品需求文档` |
| **阶段 3** | UI 原型 | `feat(prototype): 完成系统原型设计` |
| **阶段 4** | 技术方案文档 | `docs: 编写技术设计方案` |
| **阶段 5** | 项目骨架 | `chore: 初始化项目代码结构` |
| **阶段 6** | AI 核心功能 | `feat(ai): 实现学生画像和多智能体` |
| **阶段 7** | 测试修复 | `fix: 修复测试发现的问题` |
| **阶段 8** | 交付文档 | `docs: 完成部署手册和演示PPT` |

### 7.2 首次提交（已完成）

```bash
# 已执行的首次提交
git commit -m "docs: 添加赛题要求和AI工具使用规范文档"
```

---

## 八、安全规范

### 8.1 禁止提交的内容

**❌ 绝对禁止提交**：
- API Key（如 `DEEPSEEK_API_KEY`、`XUNFEI_API_KEY`）
- 访问令牌（如 `PENCIL_CLI_KEY`、GitHub Token）
- 账号密码（明文或加密）
- 真实个人隐私数据（姓名、手机号、身份证号等）
- 大模型服务凭证
- 私钥文件（`.pem`、`.key`）

### 8.2 安全检查清单

```bash
# 提交前检查（防止误提交敏感信息）
git diff --cached | grep -i "key\|secret\|password\|token"

# 全局搜索敏感信息
grep -r "api_key\|secret\|password" --include="*.js" --include="*.ts" --include="*.py" .
```

### 8.3 应急处理

如不慎提交敏感信息：

```bash
# 撤销最后一次提交（未推送）
git reset --hard HEAD~1

# 已推送时，需要重写历史（谨慎使用）
git filter-branch --force --index-filter \
  'git rm --cached --ignore-unmatch path/to/sensitive-file' \
  --prune-empty -- --all

git push --force
```

---

## 九、常用命令速查表

| 命令 | 说明 |
|------|------|
| `git status` | 查看工作区状态 |
| `git add .` | 添加所有修改 |
| `git commit -m "message"` | 提交更改 |
| `git push` | 推送到远程仓库 |
| `git pull` | 拉取远程更新 |
| `git branch` | 查看分支 |
| `git checkout -b <name>` | 创建并切换分支 |
| `git merge <branch>` | 合并分支 |
| `git log` | 查看提交历史 |
| `git diff` | 查看文件差异 |
| `git stash` | 暂存修改 |
| `git reset` | 撤销提交 |

---

## 十、协作规范

### 10.1 开发流程

```
1. 从 dev 分支创建 feature 分支
2. 在 feature 分支开发
3. 开发完成后推送到远程
4. 创建合并请求（Merge Request / Pull Request）
5. 团队审查后合并到 dev
6. 测试通过后合并到 main
```

### 10.2 冲突处理

```bash
# 拉取最新代码
git pull origin dev

# 查看冲突文件
git status

# 手动解决冲突后提交
git add .
git commit -m "fix: 解决合并冲突"
git push
```

---

## 十一、当前项目状态

### 11.1 Git 状态

```bash
# 当前分支
git branch

# 最近提交
git log --oneline -5
```

### 11.2 已提交文件

| 文件 | 说明 |
|------|------|
| `.gitignore` | Git 忽略规则 |
| `docs/00-赛题要求-A3.md` | 赛题要求文档 |
| `docs/00-AI工具使用规范.md` | AI 工具使用规范 |

### 11.3 待提交文件

| 文件 | 说明 |
|------|------|
| `docs/00-Git使用说明.md` | 本文件 |
| `course-prototype.pen` | 原型文件（如需要） |

---

## 十二、下一步建议

1. **创建远程仓库**：在 Gitee/GitHub 创建空仓库
2. **配置远程地址**：执行 `git remote add origin <仓库地址>`
3. **推送代码**：执行 `git push -u origin main`
4. **创建开发分支**：执行 `git checkout -b dev`
5. **继续开发**：按阶段提交点规划进行后续开发

---

## 附录：Git 配置建议

### 设置默认分支为 main

```bash
git config --global init.defaultBranch main
```

### 设置自动换行

```bash
# Windows 用户
git config --global core.autocrlf true

# macOS/Linux 用户
git config --global core.autocrlf input
```

### 设置编辑器

```bash
git config --global core.editor "code --wait"
```