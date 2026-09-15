# nt_helper_release

[H3CoF6/nt_helper](https://github.com/H3CoF6/nt_helper)（私有）构建产物的**公开发布点**。
内容全部由那边的 `Rust-Release-Build` 工作流自动推送，不要手改。

- **Releases**：每个 tag 一份，含 5 个平台的 `nt_helper.node`、装扮资源 `*.dat`、`manifest.json`、`SHA256SUMS`
- **latest.json**：指向最新一份（与那个 Release 里的 `manifest.json` 完全相同）

在 WeQ 里这样取：

```bash
pnpm native:fetch          # 本机平台 + 装扮资源
pnpm native:fetch --all    # 五个平台
pnpm native:fetch --check  # 只比对本地与远端，不改文件
```

⚠️ 同一 tag 里的 `.node` 与 `.dat` 必须配套：装扮资源的 AES key 由构建 commit 派生并烘焙进
`.node`，混用会解不开。CI 构建的 `.node` 还带 30 天有效期，发版前取最新那份即可。
