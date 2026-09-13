# thaichinesejournal
Official Website of Thai Chinese Journal

## 双域名自动发布

- 唯一内容来源：本仓库的 `main` 分支，继续通过 GitHub Pages 发布到 `https://thaichinesejournal.org/`。
- `.github/workflows/sync-com.yml` 在每次推送到 `main` 后，将最新内容同步到 `wangpump/thaichinesejournal-com` 的 `main` 分支，由目标仓库的 GitHub Pages 发布到 `https://thaichinesejournal.com/`。
- 在本仓库 Settings → Secrets and variables → Actions 中设置 `COM_SYNC_TOKEN`。使用仅授权目标仓库、具有 Contents 读写权限的细粒度令牌。令牌到期前需重新生成并更新此 Secret；不要把令牌写入文件或聊天。
- 两个仓库的 Pages 均使用 `main` 分支根目录发布。目标仓库保留 `.com` 域名，源仓库的 `CNAME` 不变；同步不会复制 `.git` 或 `.github`，避免复制凭据及循环触发同步。
- 目标仓库仅用于发布，请在本仓库修改网页、图片和 PDF。同步会覆盖目标仓库的对应文件，并删除源仓库已删除的发布文件；不会强制推送或重写目标提交历史。
- 首次推送工作流后，在本仓库 Actions → Sync COM website 查看结果。也可选择 Run workflow（`main` 分支）手动重试；无内容差异时不会创建提交。
- 同步完成后，目标仓库还需完成 Pages 构建、DNS 生效和 HTTPS 证书签发。两个网站更新可能相差几分钟；源站发布不依赖同步是否成功。
