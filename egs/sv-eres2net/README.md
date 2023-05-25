# ERes2Net

## Training config
- Feature: 80-dim fbank, mean normalization, speed perturb
- Training: lr [0.00005, 0.2], batch_size 512, 8 gpu(Tesla V100), additive angular margin
- Metrics: EER(%), MinDCF(p-target=0.01)

## Voxceleb Results
- Train set: Voxceleb2-dev, 5994 speakers
- Test set: Voxceleb-O

| Model | EER(%) | MinDCF |
|:-----:|:------:|:------:|
| ERes2Net |  0.97  |  0.090 |

## pretrained model
Pretrained models are accessible on [ModelScope](https://www.modelscope.cn/models).

- Voxceleb: [speech_eres2net_sv_en_voxceleb_16k](https://modelscope.cn/models/damo/speech_eres2net_sv_en_voxceleb_16k/summary)

Here is a simple example for directly extracting embeddings. It downloads the pretrained model from [ModelScope](https://www.modelscope.cn/models) and extracts embeddings.
``` sh
# Install modelscope
pip install modelscope
# CAM++ trained on VoxCeleb
model_id=damo/speech_eres2net_sv_en_voxceleb_16k
# Run inference
python speakerlab/bin/infer_sv.py --model_id $model_id --wavs $wav_path
```