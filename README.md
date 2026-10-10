
## 🤖 具身智能线 —— 决策 ⇄ 想象 闭环

| 仓库 | 一句话 | 关键数字 |
|---|---|---|
| [mini-vla-pi0](https://github.com/yimingjiang216-alt/mini-vla-pi0) | π0 风格迷你 VLA（手写 ViT + Flow Matching），语言指令真实参与决策；含演示视频与一键复现脚本 | 2.38M 参数 / 语意响应 gap ≈0.96 / CPU 7 分钟训完 |
| [pi05-libero-sim](https://github.com/yimingjiang216-alt/pi05-libero-sim) | 开源 π0.5（LIBERO 微调权重，3B）在 Kaggle 免费 T4 上驱动 LIBERO/robosuite 机械臂完成取物任务；完整实验记录（原理 / 预处理管线对齐 / 离线校验 / 评测协议） | 成功率 3/3 / 87–90 步 / 单卡 T4 |
| [vision-worldmodel-projects](https://github.com/yimingjiang216-alt/vision-worldmodel-projects) | 动作条件视频世界模型（DiT + adaLN-zero + CFG），ONNX 浏览器实时推理；诚实报告「动作可控性未通过」的完整评估 | 生成 MAE 0.125 / 响应比 1.67x @CFG=16 |

🔗 **闭环**：VLA 出动作 → 世界模型视角渲染"想象未来"（两仓库共享同一套 3D 导航数据管线）；从 2.38M 迷你自训（mini-vla）到 3B 开源微调权重驱动真机械臂基准（pi05-libero-sim），同一套 π0 范式在两种尺度上验证。

## 🗺️ 视觉几何线 —— 离线重建 ⇄ 在线定位 闭环

| 仓库 | 一句话 | 关键数字 |
|---|---|---|
| [sfm-3dgs-pipeline](https://github.com/yimingjiang216-alt/sfm-3dgs-pipeline) | 手机环绕实拍 130 余张走通 COLMAP → 3DGS 新视角合成（定性验证，如实注明 PSNR 未记录） | 130+ 拍 / 120 用 / T4 7000 步 |
| [rgbd-slam](https://github.com/yimingjiang216-alt/rgbd-slam) | 手写 RGB-D SLAM（VO / 局部 BA / 回环 / SE(3) 位姿图）；回环失效的跨序列归因与修复全程留档 | ATE 4.49cm / 回环修复：xyz 零回退、room −10.4% |

🔗 **闭环**：同一几何内核（特征匹配 / PnP / BA / 回环）的离线与在线两种用法，共用 TUM 基准——27 帧照片集考重建、798 帧视频流考定位。

## 🧠 Agent 线 —— 读源码 → 复刻 → 方法论 → 生产运转

| 仓库 | 一句话 |
|---|---|
| [codex-cli-source-reading-notes](https://github.com/yimingjiang216-alt/codex-cli-source-reading-notes) | OpenAI Codex CLI 源码逐段精读笔记（主循环 / 工具系统 / 安全 / 通信） |
| [mini-codex](https://github.com/yimingjiang216-alt/mini-codex) | ~400 行迷你编程 Agent 复刻，归纳 Agent 成立的硬约束 |
| [tech-oracle](https://github.com/yimingjiang216-alt/tech-oracle) | 苏格拉底式技术信息质检：穿透 PR 热度 / 追问护城河 / 判断时间尺度 |
| [report](https://github.com/yimingjiang216-alt/report) | 「科技前沿简报」生产系统：60+ 信息源、每日 300+ 篇、GitHub Actions 全自动运行中（看提交记录即知还活着） |

🔗 **闭环**：精读 → 复刻验证 → 方法论沉淀 → 每日在真实管线中运转。

## 📚 学习输入（2026-09 调研期）

[DrClaw](https://github.com/yimingjiang216-alt/DrClaw) · [NanoResearch](https://github.com/yimingjiang216-alt/NanoResearch) · [P1-VL](https://github.com/yimingjiang216-alt/P1-VL) · [ToolUniverse](https://github.com/yimingjiang216-alt/ToolUniverse) · [hypit](https://github.com/yimingjiang216-alt/hypit) · [wechat](https://github.com/yimingjiang216-alt/wechat)

动手之前广泛调研他人 AI / Agent 项目的痕迹——上面的输出线从这里开始。

## 🧭 横贯所有仓库的原则

**如实报告阴性结果与局限**：世界模型「动作可控性未通过」（附完整评估方法）、SLAM 回环「曾致 ATE 恶化 340% → 归因 → 跨序列修复验证」、3DGS「PSNR 未记录，不做数值结论」、mini-vla README 记录 ODE 方向写反的调试复盘。量化结论必须有真值或先在真值上校准；定性定量分开说。
