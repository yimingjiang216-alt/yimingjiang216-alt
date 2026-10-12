蒋一鸣，山东农业大学遥感科学与技术在读（2027 届）。

专业是遥感，做的事慢慢往机器人和 AI Agent 这边走。下面这些是这两个月自己做的东西，代码主要靠 AI 协作写，选题、拆方案、设计怎么验证、判断结果对不对，是我自己来。每个仓库的 README 里都写了没做成的部分。

联系：yimingjiang216@gmail.com

---

## Agent

**[report](https://github.com/yimingjiang216-alt/report)**：每天早上 8:30 自动发到飞书和邮箱的科技新闻简报。从 60 多个来源抓新闻，让大模型挑 5 条，去掉重复的再发。到现在改了 105 次，大部分是线上出了问题再回头修：同一件事换个说法被当成两条、模型输出格式偶尔坏掉整期发不出去、GitHub 自带的定时任务老是晚点。

**[mini-codex](https://github.com/yimingjiang216-alt/mini-codex)**：OpenAI Codex CLI 的小版本，代码是 AI 协作写的，我负责对着源码核对它该有的行为。用 Codex 官方 25 个 apply_patch 测试场景逐个跑过，全部通过。自建了 7 个带 bug 的小仓库来比较两种改文件的方式，结果是都能修好，但文件长到三四百行时，整文件重写输出的字数是打补丁的 30 到 40 倍，小文件只差两倍多。没做沙箱、权限审批、MCP 和上下文压缩。

**[codex-cli-source-reading-notes](https://github.com/yimingjiang216-alt/codex-cli-source-reading-notes)**：Codex 源码阅读笔记，9 篇，从主循环、工具系统一路到安全和通信。和上面的 mini-codex 是同一件事的两面：一边读懂真的怎么做，一边自己搭一个小的对照。

**[tech-oracle](https://github.com/yimingjiang216-alt/tech-oracle)**：一段提示词，让 AI 别顺着你说，改成追问你：证据在哪、有没有反例、凭什么挡得住别人。简报的筛选逻辑就是从这里来的。

## 具身智能

**[mini-vla-pi0](https://github.com/yimingjiang216-alt/mini-vla-pi0)**：想弄清楚 VLA 到底怎么把一句话变成动作，就自己搭了个 π0 风格的小模型，2.38M 参数，CPU 上训 7 分钟。同一张画面，只把指令从"左转"改成"右转"，输出的转向角速度就反过来，差值约 0.96。调试时发现过一次积分方向写反，结果直接发散，README 里记了。

**[pi05-libero-sim](https://github.com/yimingjiang216-alt/pi05-libero-sim)**：在 Kaggle 免费的 T4 上，用开源的 π0.5 去控制 LIBERO 里的机械臂。三个任务各跑了一次，都完成了。每个任务只跑一次，说明不了成功率。

**[vision-worldmodel-projects](https://github.com/yimingjiang216-alt/vision-worldmodel-projects)**：给定一串动作，生成第一视角的后续画面。画面质量还行，但动作对画面的控制没有达标，README 里写了评估怎么做的、哪里没过。

**[action-tokenizer-bench](https://github.com/yimingjiang216-alt/action-tokenizer-bench)**：把一段轨迹编成离散 token 有好几种做法，在真实的 TUM 位姿数据上比了四种。在约 1.2 cm 的同一精度档上，残差量化只要 3 个 token，逐维分档要 30 个。

## 视觉几何

**[rgbd-slam](https://github.com/yimingjiang216-alt/rgbd-slam)**：不用 g2o、Ceres 这些现成的优化库，自己写 RGB-D 里程计、局部光束法平差、回环检测和位姿图优化，在 TUM 数据集上测。回环一开始没帮上忙：在 fr1/xyz 上加了回环，轨迹误差从 4.5 cm 涨到 19.8 cm。查下来是这个序列里相机基本在原地转，回环两端只隔十几厘米，算出来的旋转不准。后来加了一道基线门控，把基线太短的回环整条拒掉：xyz 上回环全被拒，误差回到和不加回环一样；换到有真实重访的 fr1/room 序列，误差降了 10.4%。

**[sfm-3dgs-pipeline](https://github.com/yimingjiang216-alt/sfm-3dgs-pipeline)**：用手机绕着一个东西拍了 130 多张，取连续的 40 张，走完 COLMAP 重建再到 3D Gaussian Splatting 生成新视角，40 张全部注册成功。COLMAP 和 3DGS 都是别人的开源项目，我做的是把它们接起来，解决相机模型、CUDA 版本这些衔接问题。留出的 5 个视角上 PSNR 是 16.76 dB，训练视角是 29.78 dB，训练步数加多了留出视角也不涨，我判断瓶颈更可能在相机位姿精度和拍摄角度太单一，README 里写了排查过程。

---

## 一个习惯

没做成的就写没做成：世界模型的动作控制没达标，SLAM 回环一度让精度变差，3DGS 在留出视角上过拟合。先在有真值的地方确认评估方法本身可靠，再下结论。




