# my-docs

这是 dx0110 的个人技术文档网站，用于练习通过 GitHub Actions 将 MkDocs 静态文档自动部署到 GitHub Pages。网站包含首页、关于、使用指南和 API 参考四页，提供个人实践介绍、表格、代码示例和页面间链接。

- [访问文档网站](https://dx0110.github.io/my-docs/)
- [个人实验报告](report/README.md)
- [查看 Actions 记录](https://github.com/dx0110/my-docs/actions)
- [GitHub 个人主页](https://github.com/dx0110)

## 本地构建与预览

在项目根目录执行以下命令（Windows PowerShell）：

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
python -m mkdocs build --strict
python -m mkdocs serve
```

macOS / Linux 将激活命令替换为 `source .venv/bin/activate`；Windows Git Bash 使用 `source .venv/Scripts/activate`。

预览启动后打开终端显示的地址，本项目截图中的地址为 `http://127.0.0.1:8000/my-docs/`。按 `Ctrl+C` 停止预览。若 PowerShell 限制激活脚本，可直接使用 `.\.venv\Scripts\python.exe` 替代上述安装、构建和预览命令中的 `python`。

## 项目结构与发布

- `docs/`：四页 Markdown 文档源文件。
- `mkdocs.yml`：站点地址、主题和导航配置。
- `requirements.txt`：MkDocs 与 Material 主题依赖。
- `.github/workflows/deploy.yml`：自动构建和发布 Pages 的工作流。
- `report/README.md` 与 `report/images/`：个人报告及实际操作截图。
- `site/`：本地构建产物，已通过 `.gitignore` 排除。

向 `main` 推送 `docs/**`、`mkdocs.yml`、`requirements.txt` 或部署工作流的修改时，会自动构建与部署；也可手动触发。仅修改报告、报告图片或根目录 README 不会触发本工作流部署，这是路径过滤的预期行为。
