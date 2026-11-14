# AI 提示词站点（帽子云）

两个产品的 Prompt 都放这一个站点，**按产品分区**（2026-11-15 起）：

    /                 导航页（三条链接）
    /advcmd/          终极造物主方块 · 脚本提示词；配方正文在 /advcmd/r/<键>
    /zombie/script    僵尸包 · 挑战书脚本提示词
    /zombie/book      僵尸包 · 挑战书 JSON 规范

## 真源（改内容只改这三个文件）

| 页面 | 真源 |
|---|---|
| /advcmd/ | `advcmdblock/behavior_pack_advcmd/AdvCmdScripts/AdvCmdSpec.py`（BUILTINS + MANUAL + RECIPES） |
| /zombie/script | `…/PVZZombieScripts/ChallengeSystem/ChallengeScriptSpec.py` |
| /zombie/book | `…/PVZZombieScripts/ChallengeSystem/ChallengeAiDoc.py` 的 `BOOK_SPEC` |

页面地址与版本号也由包内算：`ChallengeAiDoc.script_url()` / `book_url()`，
指纹用 32 位 FNV-1a（游戏内没有 hashlib.sha1，包与生成器必须同一算法）。

## 重新生成

    C:\Python27\python.exe -B "Mod开发知识库\结构生成工具\script_prompt_dump.py"

生成器会打印每条 URL；`/zombie/*` 的版本若与包内算出的不一致，**直接非 0 退出**。

## 发布

    git add -A && git commit -m "update prompt" && git push

帽子云按分支自动构建；构建完再用 HTTP 取一次页面，确认标题/正文是新版（缓存约 20 分钟）。