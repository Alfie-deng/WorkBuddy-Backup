# 跨空间记忆库

> 所有空间共享。格式规则：
> - `[All]` = 所有空间通用
> - `[WorkBuddy]` / `[OpenClaw]` = 来源空间
> - 同一事项多来源时，保留各空间视角，标注更新时间

---

## 用户档案 [All]

**身份：** Alfie，地产广告公司策略+创意双线负责人
**行业：** 房地产广告策略推广全案服务
**沟通风格：** 像认识很久的朋友，生动自然，可开玩笑，专业性不能丢
**文案偏好：** 有力量感、画面感、击中感，不平淡
**策略输出：** 逻辑链清晰，结论在前，支撑依据紧随其后

---

## 硬件配置 [All]

| 设备 | 配置 | 用途 |
|------|------|------|
| MacBook Pro 14" M3 Pro 18GB | Apple M3 Pro, 18GB | 主力工作机 |
| 家里 PC | Win11, i5-12490F, 32GB, RTX 4070 12GB | AI生图服务器 |

---

## 技能清单 [All]

| 技能 | 功能 | 状态 |
|------|------|------|
| ima-skill | IMA笔记/知识库管理 | ✅ 已配置 |
| minimax-docx | Word文档处理 | ✅ 已安装 |
| minimax-xlsx | Excel表格处理 | ✅ 已安装 |
| minimax-pdf | PDF处理 | ✅ 已安装 |
| pptx-generator | PPT演示文稿生成 | ✅ 已安装 |
| comfyui-client | PC远程ComfyUI生图 | ✅ 已配置 |
| browser-use | 浏览器自动化 | ✅ 已安装 |
| brave-search | 网页搜索 | ✅ 已安装 |
| shell | Shell脚本参考 | ✅ 已安装 |
| find-skills | 发现新技能 | ✅ 已安装 |

---

## 待处理事项 [All]

> 状态：🔴 高优先级 / 🟡 中优先级 / ✅ 完成 / ❌ 已取消

| 事项 | 状态 | 来源 | 更新日期 | 备注 |
|------|------|------|----------|------|
| 房产营销知识库配置 | 🔴 待执行 | WorkBuddy | 2026-03-29 | 需求：配置存储位置、格式、权限 |
| 财富地产20周年庆PDF合并 | 🔴 待执行 | WorkBuddy | 2026-03-29 | 将PDF推广内容合并到Word文档 |
| LLM排行榜短视频生成 | 🔴 待执行 | WorkBuddy | 2026-03-29 | 基于OpenRouter数据，20秒竖版视频 |
| PC端AI生图服务器部署 | 🟡 进行中 | WorkBuddy | 2026-04-04 | ComfyUI + Ollama，EasyTier网络 |

---

## 近期关键决策 [All]

### 2026-04-07
**[All]** MiniMax M2.7 上下文满 2013 报错修复：`maxOutputTokens` 从 131000 降到 16384

**[All]** OpenClaw ComfyUI 生图路径修复：禁止直接调用API，统一走 `flux_schnell.py` / `z_turbo.py`，图片保存到 `~/Desktop/AI生图/`

### 2026-04-06
**[All]** OpenClaw M2.7 接入成功，主力模型切换为 minimax/MiniMax-M2.7

**[All]** GitHub Issue #30983 确认：OpenClaw 本地模型慢是框架设计问题，非硬件

### 2026-04-05
**[All]** 跨空间记忆同步方案确定：三层架构 L1本地 → L2 GitHub → L3 IMA（未实施）

### 2026-04-04
**[All]** AI生图方案确定：PC作为生图服务器，Mac通过EasyTier远程调用ComfyUI

### 2026-04-03
**[WorkBuddy]** Qwen3.5 32B Q4 本地运行测试：Mac M3 Pro 18GB内存不够，建议14B Q4

### 2026-04-02
**[All]** MiniMax办公套装全部安装完毕（docx/xlsx/pdf/pptx-generator）

---

## 技术配置 [All]

### IMA
- Client ID：3641387f2314537894ef545e8fb233a0
- 全局记忆库 doc_id：7446236407799737（标题：workbuddy记忆库）
- 自动同步规则：工作范畴（地产广告/策略创意/项目执行/技能/自动化）自动保存；非工作（系统咨询/测试/闲聊）不保存

### GitHub
- 账号：Alfie-deng / Alfiedeng1210
- 主仓库：WorkBuddy-Backup
- Token：`ghp_xxxxxxxxxxxxxxxxxxxx`（存储在本地 ~/.netrc 或 keychain，不进仓库）
- 跨空间记忆同步目录：`memory/MEMORY.md`、`memory/daily/`

### AI生图（PC ComfyUI）
- PC IP：10.10.10.20:8188
- 脚本：`~/.workbuddy/skills/comfyui-client/flux_schnell.py`（FP8，4步，英文提示词）
- 脚本：`~/.workbuddy/skills/comfyui-client/z_turbo.py`（BF16，8步，中文支持）
- 输出目录：`~/Desktop/AI生图/`
- 默认尺寸：1024×768
- ⚠️ Z-Turbo 正确配置：CLIPLoader(type=qwen_image)，CLIPTextEncode，scheduler=sgm_uniform

### iMessage（OpenClaw）
- Mac iMessage：jetdeng@126.com
- allowFrom：jetdeng@126.com
- MiniMax reasoning：false（已关闭）
- 图片保存路径（OpenClaw内置调用）：`~/.openclaw/workspace/`
