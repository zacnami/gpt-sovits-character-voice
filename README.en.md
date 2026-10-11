# GPT-SoVITS character voice training skill

[中文](README.md) | English

An agent skill for the complete character voice training workflow with official GPT-SoVITS tools. It covers audio segmentation, background music (BGM) removal and denoising, transcription and review, dataset preparation, feature extraction, GPT and SoVITS training, and inference through the official WebUI.

By default, the workflow uses the pretrained weights and training parameters supplied by the selected official release. If you already have an approved training recipe, it follows that recipe and explains any proposed changes.

The workflow is not restricted to a particular language. Language support and training options depend on the GPT-SoVITS version in use. The maintainer's two trained weight files were both trained on Japanese material; results in other languages still require training and listening tests.

## Workflow

1. **Prepare the environment and source material.** Check the official GPT-SoVITS version, runtime, pretrained weights, source recordings, and dialogue. Preserve the original material.
2. **Segment the audio.** Organize long recordings or existing clips, check boundaries for clipped speech and adjacent speakers, and assign stable clip IDs.
3. **Process BGM and noise.** You manually identify clips containing BGM or requiring denoising and send their IDs to the agent. The agent locates and processes those clips, preserves the relationship between original and processed versions, and returns them for listening and approval.
4. **Transcribe and review.** Check recordings against existing dialogue or ASR drafts, make corrections in the official annotation WebUI, and confirm the dataset version to use.
5. **Prepare training data and extract features.** Create the audio and annotation formats required by the selected version, extract or update the required text, audio, and semantic features, and verify which data the training loader actually reads.
6. **Train GPT and SoVITS.** Start with the official pretrained weights and default parameters unless an approved recipe is provided. Record configuration, progress, and saved outputs. Diagnose failures and plan recovery using available artifacts.
7. **Deliver weights and an inference interface.** Organize clearly named weights and reference audio, provide the official inference WebUI, and support manual listening and authorized comparison runs.

BGM removal and denoising require you to provide the IDs of the clips to process. The workflow does not automatically detect and process every clip. You approve the dataset and assess the resulting voice; technical checks verify data preparation, training, and model loading.

## Installation and use

Download or clone this repository into a directory named `gpt-sovits-character-voice` inside your assistant's skills directory. Keep the relative layout of `SKILL.md`, `references/`, and `agents/`, then load the skill according to your assistant's instructions.

Invoke `$gpt-sovits-character-voice` and specify the location of your material and what you want to accomplish.

Example for selected clips:

```text
I manually reviewed the clips. IDs 0012, 0037, and 0085 contain BGM.
Please process those clips, keep the originals, and return the results for me to listen to.
```

You can resume an existing project at any stage or request only material preparation, training, or inference. The agent acts within the scope authorized for the current task.

## Files

| File | Contents |
| --- | --- |
| [SKILL.md](SKILL.md) | Workflow entry point, scope, and completion criteria |
| [references/materials.md](references/materials.md) | Material preparation, review, audio processing, formats, and inference references |
| [references/features-training.md](references/features-training.md) | Feature updates, training recipes, recovery, and weight selection |
| [references/inference-diagnostics.md](references/inference-diagnostics.md) | Inference, listening assessment, the manual WebUI, and troubleshooting |
| [agents/openai.yaml](agents/openai.yaml) | Assistant interface metadata and default invocation prompt |

## Requirements and scope

This repository contains instructions for an agent workflow. You need a separate installation of official GPT-SoVITS, its runtime and models, and any audio processing tools required for your task. Programs, weights, and training material are not bundled.

Parameters, file formats, and launch commands depend on the GPT-SoVITS version in use. Material quality, language, model version, and training conditions can affect results. Completing training does not establish voice quality without listening. Game asset extraction requires separate tools. Only use audio, text, and models you have permission to process.

## License

The skill documentation and configuration in this repository are available under the [MIT License](LICENSE). GPT-SoVITS and any separately obtained code, models, audio, and text remain subject to their own licenses and permissions. This is an independent workflow skill and does not represent the official GPT-SoVITS project.
