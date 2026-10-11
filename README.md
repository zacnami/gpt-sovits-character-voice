# GPT-SoVITS 角色语音 Skill

面向支持 `SKILL.md` 的 AI 编程助手的中文工作流，协助使用官方 GPT-SoVITS 完成角色语音素材制作、校对、特征同步、微调和推理试听。

本仓库提供工作流说明，不包含 GPT-SoVITS 程序、模型权重、训练音频或游戏资源。运行语音任务前，需要准备所选 GPT-SoVITS 版本及其运行环境。

## 能做什么

- 将原音、台词、训练输入和导出权重对应起来，保留来源与恢复记录。
- 在官方素材审核页校对音文，确认采用的素材版本后再训练。
- 根据音频或文字的实际变化同步特征，检查训练真正消费的数据。
- 记录训练配置、保存点、失败与恢复情况，核对实际加载的模型。
- 交付官方推理 WebUI、参考音频或已授权的试听对照，将技术检查与用户听评分别记录。

游戏资源解包不在本 Skill 范围内。请仅使用有权处理的声音、文本和模型。

## 安装与使用

将本仓库下载或克隆为名为 `gpt-sovits-character-voice` 的目录，放入所用助手的 Skill 目录。保留 `SKILL.md`、`references/` 和 `agents/` 的相对结构，并按助手的说明加载 Skill。

调用示例：

```text
使用 $gpt-sovits-character-voice，检查当前角色语音项目的素材和运行环境，
给出缺失项与下一步方案。本次只检查，不启动训练。
```

实际制作或训练时，说明项目位置、目标角色、本次授权阶段和已有配方。Skill 会按任务读取相关参考文件；训练、自动合成和现场服务变更遵循当前任务的授权。

## 文件说明

| 文件 | 内容 |
| --- | --- |
| [SKILL.md](SKILL.md) | 入口、工作范围与各阶段完成条件 |
| [references/materials.md](references/materials.md) | 素材制作、校对、格式与推理参考 |
| [references/features-training.md](references/features-training.md) | 特征同步、训练配方、恢复与权重选择 |
| [references/inference-diagnostics.md](references/inference-diagnostics.md) | 推理、听评、手动 WebUI 与故障排查 |
| [agents/openai.yaml](agents/openai.yaml) | 助手界面元数据与默认调用提示 |

## 适用边界

参数、文件格式和启动入口应以实际使用的 GPT-SoVITS 版本为准。本 Skill 不承诺固定参数适用于所有角色或设备，也不把训练成功、文件完整或 ASR 一致当作音质验收。

## 许可证

本仓库的 Skill 文档和配置采用 [MIT License](LICENSE)。GPT-SoVITS 及使用者另外取得的代码、模型、声音和文本遵循各自的许可与授权。本项目是独立的工作流 Skill，不代表 GPT-SoVITS 官方项目。
