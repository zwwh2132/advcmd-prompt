# advcmd-prompt

终极造物主方块（可编程指令方块）的 AI 提示词页面，托管在帽子云。

- 入口文件：`index.html`（自包含，无外部请求）
- 内容来源：`advcmdblock/behavior_pack_advcmd/AdvCmdScripts/AdvCmdSpec.py` 的 `script_ai_prompt()`
- 重新生成：`C:\Python27\python.exe -B "Mod开发知识库\结构生成工具\script_prompt_dump.py"`，把产出的 `AI提示词.html` 复制成这里的 `index.html`

## 在帽子云接入

1. 登录 https://dash.maoziyun.com （GitHub 一键登录）
2. 新建应用 → 选 **静态网站 / Static**
3. 授权一次 GitHub（只读权限即可），选这个仓库，分支 `main`
4. 构建：无（纯静态），输出目录填 `/`
5. 部署 → 得到一个 `*.maoziyun.com` 域名

## 验收（改完必跑）

本地与远端做字节比对，三条都过才算成功：

- `HTTP 200`
- `Content-Type: text/html; charset=utf-8`
- 远端文件 SHA256 == 本地 `index.html`
