# Alfie 跨空间记忆库

> 所有空间共享此文件。格式：
> - `[All]` = 所有空间通用
> - `[Claw]` / `[OpenClaw]` / `[WorkBuddy]` = 来源空间
> - 各空间完整记忆在 `spaces/` 对应目录下
> - Token/凭证一律用占位符，不进仓库

---

## 用户档案 [All]

**姓名：** Alfie
**职业：** 地产广告公司策略+创意双线负责人
**行业：** 房地产广告策略推广全案服务

**高频工作：** 品牌定位、阶段推广策略、广告语创作、创意文案（楼书/海报/视频脚本/软文/推文）、策略提案PPT

**沟通风格：** 像认识很久的朋友，生动自然，可开玩笑，专业性不能丢
**文案偏好：** 有力量感、画面感、击中感，避免平淡套话
**策略输出：** 逻辑链清晰，结论在前，支撑依据紧随其后

---

## 硬件配置 [All]

| 设备 | 配置 | 用途 |
|------|------|------|
| MacBook Pro 14" M3 Pro 18GB | macOS Tahoe 26.5 | 主力工作机 |
| 家里 PC | Win11, i5-12490F, 32GB, RTX 4070 12GB, IP 10.10.10.20 | AI生图服务器 |

### 家庭网络拓扑 [Claw]
```
光猫 → ESXi小主机(10.10.10.1, Celeron N4500, 8GB)
              ├── iKuai (10.10.10.2) - 主路由/DHCP
              ├── iStoreOS (10.10.10.3) - 科学上网
              └── 飞牛OS (10.10.10.10) - NAS, 2TB硬盘直通
```
ESXi SSH: root / Alfie-1210 | iKuai SSH: Alfie / alfie1210 | iStoreOS/飞牛SSH: root / alfie1210

---

## AI生图服务器 [Claw] ⚠️ 重要

**PC配置要求：**
- 启动命令：`python main.py --listen 0.0.0.0 --port 8188`
- ⚠️ CMD窗口不能关（关闭=服务停止）
- 防火墙开放TCP 8188入站

**Mac端脚本（~/.workbuddy/skills/comfyui-client/）：**
- `flux_schnell.py` — FP8快速，4步，英文提示词，输出 ~/Desktop/AI生图/
- `z_turbo.py` — BF16高质量，8步，中文支持好

**Z-Turbo关键配置（已实测正确）：**
- CLIPLoader: `type=qwen_image`
- 文本编码：CLIPTextEncode（不是TextEncodeZImageOmni）
- 调度器：scheduler=sgm_uniform（不是normal）
- shift: 3.0，8步，cfg=1.0

**拓图：**
- `ImageScaleBy` + scale_by=4 — 保持原比例 ✅
- `ImageScale` + width/height — 会变形 ❌

---

## 技能清单 [All]

| 技能 | 路径 | 状态 |
|------|------|------|
| ima-skill / ima-skills | ~/.workbuddy/skills/ima-skills/ | ✅ 已配置 |
| minimax-docx | marketplace | ✅ 已安装 |
| minimax-xlsx | marketplace | ✅ 已安装 |
| minimax-pdf | marketplace | ✅ 已安装 |
| pptx-generator | marketplace | ✅ 已安装 |
| comfyui-client | ~/.workbuddy/skills/comfyui-client/ | ✅ 已配置 |
| browser-use | ~/.workbuddy/skills/browser-use/ | ✅ 已安装 |
| brave-search | ~/.workbuddy/skills/brave-search/ | ✅ 已安装 |
| shell | ~/.workbuddy/skills/shell/ | ✅ 已安装 |
| find-skills | ~/.workbuddy/skills/find-skills/ | ✅ 已安装 |
| text-to-image-prompt-optimizer | ~/.workbuddy/skills/text-to-image-prompt-optimizer/ | ✅ 已安装 |
| shell-executor [Claw] | ~/.workbuddy/skills/shell-executor/ | ✅ 已创建 |
| 地产广告专家 [Claw] | ~/.workbuddy/skills/地产广告专家/ | ✅ 已安装 |

---

## 待处理事项 [All]

> 🔴 高优先级 / 🟡 中优先级 / ✅ 完成 / ❌ 已取消

| 事项 | 状态 | 来源 | 更新 | 备注 |
|------|------|------|------|------|
| 房产营销知识库配置 | 🔴 待执行 | Claw | 2026-03-29 | 存储位置、格式、权限 |
| 财富地产20周年庆PDF合并Word | 🔴 待执行 | Claw | 2026-03-29 | 3大主题：品牌+感恩+项目2期 |
| LLM排行榜短视频生成 | 🔴 待执行 | Claw | 2026-03-29 | OpenRouter数据，20秒竖版 |
| PC端AI生图服务器部署 | 🟡 进行中 | Claw | 2026-04-04 | ComfyUI已就位，Mac端脚本可用 |

---

## 自动化任务 [All]

**每周备份（周日20:00）：** `~/.workbuddy/` 核心配置+技能 → SMB `smb://10.10.10.10/临时中转/wordbuddy备份/`（Claw空间创建）

---

## 技术配置 [All]

### IMA
- Client ID：3641387f2314537894ef545e8fb233a0
- 全局记忆库 doc_id：7446236407799737（标题：workbuddy记忆库，**注意：已臃肿，需整理**）
- 规则：地产广告/策略创意/项目执行/技能/自动化 → 自动保存；系统咨询/测试/闲聊 → 不保存

### GitHub
- 账号：Alfie-deng / Alfiedeng1210
- 仓库：WorkBuddy-Backup
- Token：`ghp_xxxxxxxx`（存本地，不进仓库）
- **跨空间记忆目录：** `memory/`（所有空间共用）
- **各空间记忆备份：** `memory/spaces/{space}/`

### OpenClaw iMessage
- Mac iMessage：jetdeng@126.com
- allowFrom：jetdeng@126.com
- MiniMax reasoning：false（已关闭）

---

## 重要经验教训 [All]

**AI生图路径问题：** ComfyUI直接API调用 → 图片在PC本地；skill脚本 → ~/Desktop/AI生图/；OpenClaw内置调用 → ~/.openclaw/workspace/。**必须强制用skill脚本。**

**MiniMax maxOutputTokens：** 不能设太大，要给prompt+历史留足空间，参考值16384。

**Shell-executor局限性 [Claw]：** AI无法直接调用技能，shell-executor是"更好的手动方案"而非完全自动化。

**GitHub Push Protection：** Token不能进仓库，用占位符代替。

---

## 近期决策日志

### 2026-04-07
**[All]** 跨空间记忆问题：IMA只增不减，API不支持删除，GitHub sync机制未落地。**决定：手工维护IMA，GitHub搭建跨空间记忆库（memory/目录），各空间记忆备份到memory/spaces/。**

**[All]** GitHub Token GH013拦截：Token不能写入仓库，用占位符。

**[All]** OpenClaw ~/.openclaw/memory/main.sqlite（69KB）——OpenClaw主记忆数据库，尚未文本化。

### 2026-04-06
**[All]** OpenClaw M2.7接入成功，主力模型切换minimax/MiniMax-M2.7。

### 2026-04-05
**[Claw]** Z-Image-Turbo BF16工作流验证可用，Nunchaku节点放弃（CUDA DLL问题）。

### 2026-04-04
**[Claw]** PC ComfyUI生图方案确认：EasyTier网络，Mac端脚本就位。

---

## 记忆库结构说明

```
WorkBuddy-Backup/memory/
├── MEMORY.md              ← 本文件：整合所有空间精华长期记忆
├── daily/                 ← 各空间每日日志汇总
│   └── 2026-04-07.md
├── spaces/                ← 各空间原始记忆备份
│   ├── workbuddy_claw/    ← ~/WorkBuddy/Claw/.workbuddy/memory/
│   ├── workbuddy_current/ ← ~/WorkBuddy/20260407165658/.workbuddy/memory/
│   └── openclaw_workspace/ ← ~/.openclaw/workspace/memory/
└── config/
    └── sync_manifest.json ← 同步状态清单
```

**各空间使用规则（绝对优先级：本地 > GitHub，GitHub 只能补充不能覆盖）：**

**新建会话 / 同步记忆时（必须按顺序执行）：**
1. 读本地 `.workbuddy/memory/MEMORY.md` + 当日/近日志（最先，本地为权威）
2. git pull 或 clone GitHub 全局记忆（Alfie-deng/WorkBuddy-Backup，memory/ 目录）
3. **对比并合并**（重要）：本地与 GitHub 版对比，用 GitHub 版**补全**跨空间硬信息，**绝不覆盖**本地已有内容
4. 如需最新动态，读 IMA 笔记 doc_id `7446236407799737`（仅作补充）

**对话结束时：** 本地写 `.workbuddy/memory/YYYY-MM-DD.md`，定期（手动）push 到 GitHub
