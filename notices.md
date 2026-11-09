---
title: VAANI third-party notices
---

# Third-party material

VAANI itself (all code, drawings and texts not listed below) is Copyright (c) 2026 the VAANI author
(github.com/sandeepsp121). All rights reserved. The parts below belong to their authors and are used under their
licences.

## Android libraries

Jetpack Compose, Material 3, Material Icons, AndroidX (core, activity, navigation, lifecycle, datastore, window), Media3
ExoPlayer (Google LLC / The Android Open Source Project) and Kotlin coroutines (JetBrains) are used unchanged, as
libraries from Maven, under the Apache License 2.0 (https://www.apache.org/licenses/LICENSE-2.0).

The Google Play Billing Library (Google LLC, `com.android.billingclient:billing`) is used unchanged for the one-time purchase of
VAANI Pro in the Play Store build, under the Android Software Development Kit licence terms of Google
(https://developer.android.com/studio/terms). Payment is handled by Google Play; VAANI never sees card or bank details.

## Poppins (the letters of the VAANI mark)

The word "वाणी" and "VAANI" in the mark are outlines made from the Poppins typeface (Indian Type Foundry,
Jonny Pinhorn), licensed under the SIL Open Font License 1.1 (https://openfontlicense.org). No font file is in the app.

## GTCRN (AI noise cancel)

The file `app/src/main/assets/gtcrn_weights.bin` holds the weights of the GTCRN speech-enhancement
network (Rong Xiaobin et al., ICASSP 2024, https://github.com/Xiaobin-Rong/gtcrn). They were taken from the
author's published `gtcrn_simple.onnx` with `tools/export_gtcrn_weights.py`. The network itself is
re-implemented in plain Java in `app/src/main/java/com/vaani/recorder/ai/`. GTCRN is used under the
MIT licence:

```
MIT License

Copyright (c) 2024 Rong Xiaobin

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

The author's published models were trained on the DNS3 (Deep Noise Suppression Challenge) and
VCTK-DEMAND data sets. Before the app is released outside this private project, check that the licences
of those data sets allow the use of the trained weights.

RNNoise (Xiph.Org, BSD-3) was evaluated for comparison only. It is not part of the app.

## Resemble Enhance denoiser (Studio Max, in the editor)

The file `app/src/main/assets/max/denoiser_net.onnx` is the ONNX export of the denoiser network (a UNet) of Resemble
Enhance (Resemble AI, https://github.com/resemble-ai/resemble-enhance), converted from the published weights without
changing them. The code around it (`ai/MaxDenoiser.java`, `ai/MixedFft.java`, `ai/OrtMaxNet.kt`, `edit/MaxDenoiseEffect.java`) is
VAANI's own, written from the published reference program (the spectrum, the mask and the way back to sound) and checked
against an independent numpy / onnxruntime version (`tools/maxtest`). Resemble Enhance is used under the MIT licence; the full
text, with its copyright line, is in `licenses/MIT-ResembleEnhance.txt`.

## DPDFNet 2 (live Studio voice)

The file `app/src/main/assets/dpdfnet2_48khz_hr.onnx` is the `dpdfnet2_48khz_hr` model of DPDFNet (Ceva-IP,
https://huggingface.co/Ceva-IP/DPDFNet, https://github.com/ceva-ip/DPDFNet), a small streaming noise-suppression network based
on DeepFilterNet2, taken unchanged from the model's published ONNX file (downloaded with its `dpdfnet` Python package).
It is licensed under the Apache License 2.0 (`licenses/Apache-2.0.txt`). The code around it (`ai/DpdfDenoiser.java`,
`ai/OrtDpdfNet.kt`) is VAANI's own, written from the way the package feeds the model (frame of 960 samples, step of 480, Vorbis
window, the model's state vector) and checked against an independent numpy / onnxruntime version run on a recording
(difference between the two: below -55 dB). SHA-256 of the file: 7f0575a5cec0ba4ffd8f8bd657e06d007e4ccdd955d76faab922b9d3291dc14b.

## MossFormer2 (Studio Max MossFormer2, in the editor)

The files in `app/src/main/assets/mossformer2/` (`part0.bin`, `part1.bin`, ...; put together they are one ONNX file) are the
`MossFormer2_SE_48K` speech-enhancement network of ClearerVoice-Studio (Alibaba / Speech Lab, https://github.com/modelscope/ClearerVoice-Studio),
converted to ONNX from the published weights. The calculation is not changed; only the big weight tables are stored as half-precision
numbers (half the size) and turned back into normal numbers when the model is loaded, and the file is cut in parts because a
repository does not take a file over 100 MB. The file is only used when it was checked against the original network on a recording (largest difference
of the answer below 0.02 on a scale of 0 to 1; the converted file without the half-size step differs by 0.00002). ClearerVoice-Studio is
licensed under the Apache License 2.0 (`licenses/Apache-2.0.txt`). The code around it (`ai/MossDenoiser.java`, `ai/OrtMossNet.kt`,
`edit/ModelDenoiseEffect.java`, `edit/ModelProcs.java`) is VAANI's own, written from the published program (the filter-bank features,
the spectrum, the gains and the way back to sound) and checked against it on a recording (difference of the sound: below -100 dB).

## DeepFilterNet3 (Enhance, in the editor)

The three files in `app/src/main/assets/dfn3/` (`enc.onnx`, `erb_dec.onnx`, `df_dec.onnx`) are the ONNX export of the
DeepFilterNet3 speech-enhancement network (Hendrik Schröter et al., https://github.com/Rikorose/DeepFilterNet),
taken unchanged from `models/DeepFilterNet3_onnx.tar.gz` of that repository. The code around them
(`ai/DfnChannel.java`, `ai/OrtDfnNets.kt`, `edit/DfnEffect.java`) is VAANI's own, written from the published
reference program (libDF) and checked against an independent numpy / onnxruntime implementation
(`tools/golden/dfn`). The project is licensed under either the MIT licence or the Apache-2.0 licence, at your option;
VAANI uses it under the MIT licence:

```
The MIT License (MIT)
Copyright (c) 2021 Hendrik Schröter

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
```

SHA-256 of the files: enc.onnx 7c5399d3da8a50ebef1c1a0ae421b33376aa5e45d0e92df16da7e83c9c131916,
erb_dec.onnx ab669a1d10afe20911728b33053a452071042317a90581092b325da7b2f9d895,
df_dec.onnx 23114ce3b0f6464b763ee62f7bb8aab6b2a129a21eabd5bcfe59413db05f278a.

As with GTCRN, before the app is released outside this private project, check that the licences of the data sets the
network was trained on allow the use of the trained weights.

## LAME (MP3 export)

MP3 files are made with LAME 3.100 (https://lame.sourceforge.io/), the `libmp3lame` encoder, which is
licensed under the GNU Lesser General Public License, version 2 or later (the full text is in
`app/src/main/cpp/lame/COPYING` and `LICENSE`). The unmodified C sources are in
`app/src/main/cpp/lame/` (taken from the ShiftMediaProject mirror of the LAME release; only the build
file `config.h` is our own). They are built into a separate shared library, `libvaani_lame.so`, together
with a small JNI wrapper (`app/src/main/cpp/vaani_lame.c`), and loaded by the app at run time. The app does
not use any other part of LAME. Because the encoder is a separate library that is only loaded when MP3 is
exported, it can be replaced by a rebuilt version of the same library from the sources in this repository.

## ONNX Runtime (runs the AI models of "AI tools")

The speech-to-text and music-split models are run with ONNX Runtime for Android
(`com.microsoft.onnxruntime:onnxruntime-android`, https://github.com/microsoft/onnxruntime), which is used
unchanged, as a library from Maven Central, under the MIT licence (Copyright (c) Microsoft Corporation).
It is not stored in this repository; Gradle fetches it when the app is built.

## Indic-Transcribe-Core (speech to text, "AI" quality)

**Built with Indic-Transcribe-Core from Bodhan AI / AI4Bharat.** The model is **Indic-Transcribe-Core** by Bodhan AI and AI4Bharat
(IIT Madras; https://huggingface.co/bodhan-ai/indic-transcribe-core), released under the **Indic Open Model License v1.0**. The
model is built on **Canary-1B-v2** by NVIDIA Corporation (https://huggingface.co/nvidia/canary-1b-v2), which is licensed under
Creative Commons Attribution 4.0 (CC-BY-4.0, https://creativecommons.org/licenses/by/4.0/); NVIDIA's licence applies to that base
model in addition. The app does not contain the model: the first time the person asks for it, the app downloads a copy converted to
GGUF with 5-bit weights (the file `indic_transcribe_core-q5_k_m.gguf` of the repository `adidsh/indic-transcribe-core-int8-onnx`,
one fixed commit named in `models/ModelCatalog.java`), checks its size and SHA-256, and keeps it in the app's private folder. The
model is used on the phone only, to turn a recording into text for the person who made it. It is never offered as a hosted service
to other people. The licence has acceptable-use rules (for example no child abuse material, no weapons development, no mass
surveillance, no deepfakes or voice clones of real people without their consent, no scam calls); VAANI uses the model only to
write down speech. The conversion to GGUF and the 5-bit weights were made by the publisher of that repository, not by VAANI.

## transcribe.cpp and ggml (the engine of Indic-Transcribe-Core)

The Indic-Transcribe model is run by **transcribe.cpp** (Copyright (c) 2026 The transcribe.cpp authors, MIT licence), which uses
**ggml** (Copyright (c) 2023-2026 The ggml authors, MIT licence). Both are built from the sources in
`app/src/main/cpp/transcribe_cpp/` into the library `libvaani_stt.so` (CPU only). transcribe.cpp also contains **miniz**
(Copyright 2013-2014 RAD Game Tools and Valve Software, Copyright 2010-2014 Rich Geldreich and Tenacious Software LLC, MIT licence)
and a translation of **Silero VAD** (Copyright (c) 2020-present Silero Team, MIT licence). The full licence texts are in
`licenses/MIT-transcribe-cpp.txt`, `licenses/MIT-ggml.txt`, `licenses/MIT-miniz.txt` and `licenses/MIT-SileroVAD.txt`.

## Omnilingual ASR (speech to text)

The speech-to-text models are **Omnilingual ASR** (CTC, 300M and 1B parameters) by Meta
(https://github.com/facebookresearch/omnilingual-asr), licensed under the Apache License 2.0. The app does not
contain them: it downloads the int8 ONNX exports made by the k2-fsa / sherpa-onnx project
(https://github.com/k2-fsa/sherpa-onnx/releases/tag/asr-models) the first time the person asks for them, checks the
SHA-256 of every file against the values in `models/ModelCatalog.java`, and keeps them in the app's private
folder. The licence text of the model is downloaded and kept next to it. The decoder (greedy CTC), the
phrase cutting and the text handling around the model are our own code in `speech/`. The `tools/golden/` files
hold the output of the real 300M model on a few public test sentences (English, used to check our decoder);
they are test data, not part of the app.

## Dolphin (speech to text for Asian languages)

The **Dolphin** small CTC model (DataoceanAI and Tsinghua University, https://github.com/DataoceanAI/Dolphin), Apache License 2.0
(`licenses/Apache-2.0.txt`). Like the other speech models it is not stored in this repository: the app downloads the int8 ONNX
export made by the k2-fsa / sherpa-onnx project the first time the person asks for it, and checks its SHA-256
(`models/ModelCatalog.java`). The feature extraction and decoding around it (`speech/DolphinRecognizer.kt`, `speech/Fbank.java`,
`speech/CtcDecoder.java`) are our own code.

## HT-Demucs (music split) - switched off

Music split (vocals, drums, bass, other) with **Hybrid Transformer Demucs** by Meta (https://github.com/facebookresearch/demucs,
MIT licence, Copyright (c) Meta Platforms, Inc. and affiliates) is **switched off in this version**: the model is not offered,
not downloaded and not used (`ModelCatalog.MUSIC_SPLIT_ENABLED`). The code of the cutting and joining of a song (`stems/`) is our own
and stays in the app for a later version. The licence file `licenses/MIT-HTDemucs.txt` is kept for that reason.

Before the app is released outside this private project, check again the licences and the training-data terms
of the other downloaded models (Omnilingual ASR, Dolphin, Indic-Transcribe-Core), and decide whether the downloads should come from our own storage instead of
third-party servers.

## Roboto and Noto Sans (app fonts)

The text of the app is set in Roboto (Copyright 2011 The Roboto Project Authors, https://github.com/googlefonts/roboto-3-classic,
Apache License, Version 2.0) for English and the other Latin-script languages, and in Noto Sans for the Indian scripts
(Devanagari, Bengali, Gujarati, Gurmukhi, Kannada, Malayalam, Tamil, Telugu; Copyright The Noto Project Authors,
https://github.com/notofonts, SIL Open Font License, Version 1.1, https://openfontlicense.org). The font files are in
`app/src/main/res/font/`. The fonts are used as they are; they are not sold on their own.
