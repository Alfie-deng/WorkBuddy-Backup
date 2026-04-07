# 长期记忆

## 用户硬件设备

### MacBook Pro 14寸（主力电脑）
- **芯片**：Apple M3 Pro
- **统一内存**：18GB
- **硬盘**：1TB
- **系统**：macOS Tahoe 26.5
- **使用地点**：工作日放公司，周末放家里

### 家里 PC（Win11）
- **处理器**：Intel i5-12490F（第12代，6核12线程，非13代）
- **内存**：32GB
- **显卡**：RTX 4070（12GB 显存）
- **使用场景**：周末在家时使用
- **固定IP**：10.10.10.20
- **AI工具目录**：E:\ai\（已安装ComfyUI）
- **Ollama待安装**：模型存储 E:\ai\ollama_models

### 网络连接
- **EasyTier**：打通家里和公司的网络，包括下面的子网设备

---

## 家庭网络硬件配置与拓扑

### 核心设备：弱电箱小主机
- **处理器**：Intel Celeron N4500
- **内存**：8GB
- **硬盘**：128GB SSD
- **网口**：4个 2.5G 网口
- **上游**：直连光猫
- **底层系统**：ESXi 虚拟化平台

### ESXi 管理后台
- **地址**：10.10.10.1
- **账号**：root
- **密码**：Alfie-1210

### 虚拟机 1：iKuai（主路由 + DHCP）
- **地址**：10.10.10.2
- **账号**：Alfie（SSH）/ admin（Web）
- **密码**：alfie1210
- **功能**：DHCP 服务、路由转发
- **注意**：SSH密码可能与Web密码不同，待确认

### 虚拟机 2：iStoreOS（旁路由 + 科学上网）
- **地址**：10.10.10.3
- **账号**：root
- **密码**：alfie1210
- **功能**：科学上网、代理服务
- **SSH**：已开启，端口 22

### 虚拟机 3：飞牛 OS（NAS）
- **地址**：10.10.10.10
- **账号**：Alfie
- **密码**：alfie1210
- **功能**：NAS 存储服务
- **硬盘直通**：2TB 硬盘专供飞牛 OS 使用（其他虚拟机无法访问）
- **SSH**：已开启

### 网络拓扑
```
光猫 → ESXi小主机(10.10.10.1)
              ├── iKuai (10.10.10.2) - DHCP
              ├── iStoreOS (10.10.10.3) - 科学上网
              └── 飞牛OS (10.10.10.10) - NAS
```

---

## 用户偏好（重要 2026-04-05更新）

### 操作授权（全面开放）
- **所有操作默认允许**：调试、测试、安装、配置等操作一律无需确认
- **自主执行**：能自己做的就不让用户操作终端或点允许
- **SSH连接失败时**：可通过HTTP API直接操作PC上的ComfyUI

### 对话记录规则（重要）
每次对话结束后，必须：
1. 将当次讨论核心内容整理为结构化总结笔记
2. 调用 IMA API（ima.qq.com）新建一篇笔记，标题格式：`[YYYY-MM-DD] 对话主题`
3. 同时 append 一条记录到本地 `/Users/alfie/WorkBuddy/Claw/.workbuddy/memory/YYYY-MM-DD.md`
IMA 凭证存储于 `~/.config/ima/`（client_id + api_key），已验证有效。

## 已安装技能

- **ima-skill v1.1.2**（2026-03-30 安装）：笔记管理 + 知识库管理，路径 `~/.workbuddy/skills/ima-skill/`，凭证已配置并验证通过。
- **地产广告专家 Skill**：推广策略/品牌定位/广告语/创意文案四大模块，路径 `~/.workbuddy/skills/地产广告专家/`。
- **minimax-docx**（2026-03-31 安装）：Word 文档生成与编辑，从本地市场安装。
- **minimax-pdf**（2026-03-31 安装）：高质量 PDF 文档生成，从本地市场安装。
- **minimax-xlsx**（2026-03-31 安装）：Excel 文件创建与分析，从本地市场安装。
- **minimax-media**（2026-03-31 自建）：MiniMax AI 生图 + 生视频。脚本路径 `~/.workbuddy/skills/minimax-media/scripts/`。生图：`image_gen.py`（文生图/图生图）；生视频：`video_gen.py`（文生视频/图生视频/首尾帧）。需要环境变量 `MINIMAX_API_KEY`。

## 已安装技能

- **ima-skill v1.1.2**（2026-03-30 安装）：笔记管理 + 知识库管理，路径 `~/.workbuddy/skills/ima-skill/`，凭证已配置并验证通过。
- **地产广告专家 Skill**：推广策略/品牌定位/广告语/创意文案四大模块，路径 `~/.workbuddy/skills/地产广告专家/`。
- **minimax-docx**（2026-03-31 安装）：Word 文档生成与编辑，从本地市场安装。
- **minimax-pdf**（2026-03-31 安装）：高质量 PDF 文档生成，从本地市场安装。
- **minimax-xlsx**（2026-03-31 安装）：Excel 文件创建与分析，从本地市场安装。
- **minimax-media**（2026-03-31 自建）：MiniMax AI 生图 + 生视频。脚本路径 `~/.workbuddy/skills/minimax-media/scripts/`。生图：`image_gen.py`（文生图/图生图）；生视频：`video_gen.py`（文生视频/图生视频/首尾帧）。需要环境变量 `MINIMAX_API_KEY`。
- **shell-executor**（2026-04-03 创建）：解决WorkBuddy中execute_command工具不稳定的替代方案，允许AI执行shell命令，路径 `~/.workbuddy/skills/shell-executor/`。

## 用户背景

地产广告公司策略+创意双线负责人，高频工作：品牌定位、阶段推广策略、广告语创作、创意文案（楼书/海报/视频脚本/软文）、策略提案PPT。
文案风格：有力量感、有画面感，避免平淡套话。策略输出：结论先行，逻辑链清晰。

## 自动化任务

- **WorkBuddy 配置每周备份**（2026-03-31 创建）：每周日 20:00 自动备份 `~/.workbuddy/` 核心配置和技能到 SMB 服务器 `smb://10.10.10.10/临时中转/wordbuddy备份/`，按日期命名。备份内容：SOUL.md、IDENTITY.md、USER.md、mcp.json、settings.json、skills/ 目录。


## 2026-04-03：自动化探索与限制

### 核心进展
- **创建shell-executor技能**：路径 
- **功能**：执行命令、写入文件、追加内容（ v2.0）
- **验证**：所有基础功能测试通过，代码可靠

### 实际限制
- ❌ **非100%自动化**：AI无法直接调用技能，仍需用户复制粘贴命令
- ❌ **依赖用户操作**：工作流程为
- ❌ **受限于WorkBuddy**：因工具缺失/不稳定

### 正确认识
当前方案是**更好的手动方案**，不是**完全自动化方案**：
- 之前：用户需要自己思考命令语法
- 现在：AI提供完整命令，用户只需复制粘贴
- 本质：从用户操作到AI指导下的用户操作

### 等待修复
真正的100%自动化需要：
1. **WorkBuddy修复工具**
2. **或提供其他直接执行命令的机制**
3. **只有当AI能直接调用shell-executor时，才是真正的自动化**

### 实用价值
- **当前**：作为过渡方案，减少用户操作复杂度
- **未来**：可作为修复后的备用方案
- **记录**：本次探索过程和限制已如实记录在2026-04-03.md

**实事求是，不夸大成果。耐心等待工具修复。** 🎯

## 问题解决优先级规则

### 优先级1：先查官方文档
遇到开源项目问题，必须按以下顺序：
1. **查官方文档/GitHub README** - 找FAQ和配置示例
2. **查GitHub Issues** - 看有没有类似问题
3. **搜索社区解决方案** - 看别人的解决方法
4. **最后才分析代码** - 只有在官方文档不足时才用

### 优先级2：控制分析深度
- 简单配置问题 → 直接给官方解决方案
- 复杂问题 → 先问用户要深入还是简单解决
- 避免无节制代码分析，先看现成方案

### 优先级3：成本意识
- 用最少的工具调用解决问题
- web搜索比代码分析更高效
- 用户分数宝贵，必须珍惜使用

### 实战经验：TuriX-CUA问题解决总结
**问题**：Ollama连接失败，HTTP 503错误，JSON解析失败
**根本原因**：代理/VPN干扰 + 模型输出格式不符合TuriX要求
**解决方案**：
1. ✅ **关闭Shadowrocket**（关键步骤）
2. ✅ **切换模型**从qwen3-vl:4b到gemma4:e4b
3. ✅ **简化任务描述**从复杂英文到简单中文
4. ✅ **确保虚拟环境激活** source turix_env/bin/activate
**教训**：半小时代码分析 → 10分钟官方文档搜索解决

---

## PC生图服务器方案（2026-04-04完成✅）

### 核心思路
- PC作为本地AI生图服务器，Mac通过EasyTier网络远程调用
- 零成本，无限生图

### 网络架构
```
Mac → EasyTier → PC(10.10.10.20:8188)
```

### PC配置（必须）
1. **启动命令**：`python main.py --listen 0.0.0.0 --port 8188`
2. **防火墙规则**：开放TCP 8188入站（Windows Defender）
3. **⚠️ CMD窗口不能关闭**（关闭=服务停止）

### 模型文件（已就位）
| 文件 | 目录 |
|------|------|
| flux1-schnell-fp8.safetensors (11GB) | diffusion_models/ |
| ae.safetensors (320MB) | vae/ |
| t5xxl_fp8.safetensors (4.6GB) | text_encoders/ |
| clip_l.safetensors (235MB) | clip/ |

### Mac端生图脚本
- 路径：`~/.workbuddy/skills/comfyui-client/flux_schnell.py`
- 使用方法：`cd ~/.workbuddy/skills/comfyui-client && source .venv/bin/activate && python3 flux_schnell.py "提示词"`
- 输出目录：`~/Desktop/AI生图/`（无下划线）
- 参数：`-w` 宽度 `-t` 高度 `-s` 步数 `-c` 中文提示词

### Flux Schnell 工作流参数
- steps: 4（快速）
- cfg: 1.0
- sampler: euler
- 尺寸: 512x512 或 1024x1024
- 生图速度: ~15秒/张（1024x1024）

### Z-Image-Turbo 工作流（已验证可用，2026-04-05）

**实际使用配置（BF16原版，非Nunchaku）：**
- **模型**: `z_image_turbo_bf16.safetensors` (11.5GB) - diffusion_models/
- **文本编码器**: `qwen_3_4b.safetensors` (7.5GB) - 主模型目录
- **VAE**: `ae.safetensors` - vae/
- **CLIP类型**: qwen_image（不是 lumina2）
- **shift**: 3.0
- **步数**: 8步
- **negative**: 复用positive节点 ['5', 0]

**工作流节点链（已实测正确）：**
```
UNETLoader → CLIPLoader(type=qwen_image) → VAELoader → EmptyLatentImage
        ↓
CLIPTextEncode（不是 TextEncodeZImageOmni）
        ↓
ModelSamplingAuraFlow (shift=3)
        ↓
KSampler (euler, 8步, cfg=1, scheduler=sgm_uniform)
        ↓
VAEDecode → SaveImage
```

⚠️ scheduler 必须设为 sgm_uniform，不是 normal。

**Mac端脚本：** `~/.workbuddy/skills/comfyui-client/z_turbo.py`
**备用路径：** `/Users/alfie/WorkBuddy/Claw/z_turbo.py`（项目目录）

**拓图/放大经验（重要）：**
- `ImageScale` + width/height + crop:disabled = **会变形！**
- `ImageScaleBy` + scale_by = **保持原比例** ✅
- 推荐用 scale_by 4x 放大到 4K

**Mac端图片处理脚本：** `~/.workbuddy/skills/comfyui-client/image_process.py`
```bash
python3 image_process.py <图片> -s 4    # 放大4倍
python3 image_process.py <图片> --crop 16:9   # 裁剪到16:9
```

**⚠️ Nunchaku节点问题（已放弃）：**
- CUDA DLL依赖问题，PC端加载失败
- 改用原版BF16模型，无需Nunchaku节点

### 已安装技能
- **text-to-image-prompt-optimizer**：AI生图提示词优化，路径 `~/.workbuddy/skills/text-to-image-prompt-optimizer/`
- **comfyui-client**：PC生图服务器客户端，路径 `~/.workbuddy/skills/comfyui-client/`

---

## iMessage / OpenClaw 通道配置 [All]

- **Mac iMessage**：jetdeng@126.com
- **allowFrom**：jetdeng@126.com
- **MiniMax reasoning**：false（已关闭）

---

## AI生图路径强制规则 [All]

⚠️ **必须强制走 skill 脚本**，不得直接调用 ComfyUI API：
- ComfyUI 直接 API 调用 → 图片在 PC 本地
- skill 脚本（flux_schnell.py / z_turbo.py）→ 图片在 `~/Desktop/AI生图/`
- OpenClaw 内置调用 → 图片在 `~/.openclaw/workspace/`（错误）
- 回复图片路径时，必须是 `~/Desktop/AI生图/` 格式

---

## 重要系统规则 [All]

**AI可直接操作终端**：执行命令、读写文件等常规操作均已授权，无需用户手动确认（高风险删除操作除外）。

