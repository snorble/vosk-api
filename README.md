# Vosk Speech Recognition Toolkit

Vosk is an offline open source speech recognition toolkit. It enables
speech recognition for 20+ languages and dialects - English, Indian
English, German, French, Spanish, Portuguese, Chinese, Russian, Turkish,
Vietnamese, Italian, Dutch, Catalan, Arabic, Greek, Farsi, Filipino,
Ukrainian, Kazakh, Swedish, Japanese, Esperanto, Hindi, Czech, Polish.
More to come.

Vosk models are small (50 Mb) but provide continuous large vocabulary
transcription, zero-latency response with streaming API, reconfigurable
vocabulary and speaker identification.

Speech recognition bindings implemented for various programming languages
like Python, Java, Node.JS, C#, C++, Rust, Go and others.

Vosk supplies speech recognition for chatbots, smart home appliances,
virtual assistants. It can also create subtitles for movies,
transcription for lectures and interviews.

Vosk scales from small devices like Raspberry Pi or Android smartphone to
big clusters.

# Documentation

For installation instructions, examples and documentation visit [Vosk
Website](https://alphacephei.com/vosk).

# Compilation

To compile vosk library you need to have special Kaldi compiled and configured from alphacephei repo:

```bash
git clone -b vosk --single-branch --depth=1 https://github.com/alphacep/kaldi <KALDI_ROOT>
cd <KALDI_ROOT>/tools
make -j 10 openfst cub
./extras/install_openblas_clapack.sh
cd ../src
./configure --mathlib=OPENBLAS_CLAPACK --shared --use-cuda=no
make -j 10 online2 lm rnnlm
```

Once you have Kaldi compiled, then use it to compile **libvosk.so** from this folder:

```bash
cd vosk-api/src
KALDI_ROOT=<KALDI_ROOT> make -j 10
```
