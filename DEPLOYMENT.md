# GitHub Pages 部署说明

## 配置说明

本项目已配置 GitHub Actions 自动化部署到 GitHub Pages，部署路径为 `/blog`。

## 部署流程

1. **自动触发**：当代码推送到 `main` 分支时，GitHub Actions 会自动触发部署流程
2. **构建过程**：
   - 检出代码和子模块（如主题）
   - 安装 Hugo 和必要依赖
   - 使用 Hugo 构建静态站点，baseURL 设置为 `https://<your-username>.github.io/blog/`
   - 上传构建产物
3. **部署过程**：将构建好的静态文件部署到 GitHub Pages

## GitHub 仓库设置

在你的 GitHub 仓库中，需要进行以下设置：

### 1. 启用 GitHub Pages

1. 进入仓库的 **Settings** > **Pages**
2. 在 **Source** 下选择 **GitHub Actions**
3. 确保 **Build and deployment** 是 **GitHub Actions**

### 2. 确认权限设置

在仓库的 **Settings** > **Actions** > **General** 中：

1. 确保 **Actions permissions** 允许运行 actions
2. 在 **Workflow permissions** 中：
   - 选择 **Read and write permissions**
   - 勾选 **Allow GitHub Actions to create and approve pull requests**

## 访问你的博客

部署成功后，你的博客将在以下地址访问：

```
https://<your-username>.github.io/blog/
```

将 `<your-username>` 替换为你的 GitHub 用户名。

## 本地开发

本地开发时，继续使用以下命令：

```bash
hugo server -D
```

本地开发使用根路径 `/`，部署到 GitHub Pages 时会自动使用 `/blog/` 路径。

## 手动触发部署

如果需要手动触发部署，可以：

1. 进入仓库的 **Actions** 标签页
2. 选择 **Deploy Hugo site to GitHub Pages** workflow
3. 点击 **Run workflow** 按钮
4. 选择 `main` 分支并确认运行

## 注意事项

1. **分支名称**：确保你的默认分支名称是 `main`，如果是 `master` 需要修改 `.github/workflows/deploy.yaml` 中的分支名称
2. **子模块**：如果你的主题是通过 git submodule 添加的，workflow 会自动拉取
3. **构建时间**：首次部署可能需要几分钟，后续部署会更快
4. **HTTPS**：GitHub Pages 自动提供 HTTPS 支持

## 故障排查

如果部署失败，可以：

1. 查看 **Actions** 标签页中的构建日志
2. 确认仓库设置中 GitHub Pages 已正确配置
3. 确认 workflow 权限设置正确
4. 检查 Hugo 版本兼容性（当前使用 v0.140.2）

## 自定义域名（可选）

如果你想使用自定义域名：

1. 在仓库的 **Settings** > **Pages** 中设置 **Custom domain**
2. 在你的域名提供商处添加 CNAME 记录指向 `<your-username>.github.io`
3. 更新 `hugo.toml` 中的 `baseURL` 为你的自定义域名
4. 修改 `.github/workflows/deploy.yaml` 中的 baseURL 设置
