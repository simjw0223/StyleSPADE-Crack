# 🧩 StyleSPADE-Crack: Pretrained Model for Crack Image Synthesis

This repository provides the pretrained weights of **StyleSPADE**,  
a customized SPADE-based generative model designed for **realistic crack image synthesis**.  
It is used to augment training datasets for crack segmentation tasks.

---

##  What is StyleSPADE?

StyleSPADE is an enhanced version of NVIDIA’s SPADE generator,  
modified to include a *style encoder* that injects texture/style information  
into each SPADE normalization layer.

Key Features
- Generates diverse pavement/wall/ground background textures  
- Preserves fine crack structures  
- More realistic images than vanilla SPADE or SemanticStyleGAN  
- Highly effective for training crack segmentation models

---

## Files in This Release

| File name | Description |
|----------|-------------|
| `latest_net_G.pth` | Pretrained Generator weights |
| `latest_net_D.pth` | Pretrained Discriminator weights |
| `loss_log.txt` | Training loss curve logs |

## 🧱 SPADE Generator vs StyleSPADE (Architecture)

> 아래 그림은 SPADE 기반 generator와 StyleSPADE generator의 구조 차이를 보여주는 예시입니다.  
> 이미지 파일을 `assets/spade_vs_stylespade_arch.png` 같은 이름으로 업로드한 뒤, src 경로를 바꿔 주세요.

<p align="center">
  <img src="assets/spade_vs_stylespade_arch.png" width="80%">
</p>

**Architectural Differences**

- **SPADE**
  - Segmentation mask만을 이용해 각 normalization layer를 spatially-adaptive하게 조절
  - 구조(geometry)는 잘 보존되지만, 배경 텍스처가 단조롭고 회색톤에 가까운 경우가 많음

- **StyleSPADE (Ours)**
  - SPADE 구조를 유지하면서, 별도의 **style encoder**로부터 추출한 style vector를 각 SPADE block에 주입
  - 동일한 mask에 대해서도 다양한 배경 텍스처와 색감을 표현 가능
  - Crack geometry는 SPADE의 장점을 그대로 유지

---

## 🎨 Visual Comparison: SPADE vs StyleSPADE

> 아래 이미지는 동일한 crack segmentation mask에 대해  
> SPADE와 StyleSPADE가 생성한 결과를 비교한 예시입니다.  
> 예: `assets/spade_vs_stylespade.png`

<p align="center">
  <img src="assets/spade_vs_stylespade.png" width="90%">
</p>

**Qualitative Comparison**

| Method             | Background Diversity | Crack Shape Preservation | Visual Realism | Notes |
|--------------------|----------------------|--------------------------|----------------|-------|
| **SPADE**          | ❌ Low (often gray & repetitive) | ✅ Good | ⚪ Moderate | Tends to generate uniform, over-smoothed backgrounds |
| **StyleSPADE**     | ✅ High              | ✅ Good                  | 🟢 High        | Keeps crack geometry while varying background style |

> In practice, StyleSPADE generates more realistic crack scenes  
> without losing the fine structure of the cracks.

---

## 🎨 Visual Comparison: StyleSPADE vs SemanticStyleGAN

> 아래 이미지는 StyleSPADE와 SemanticStyleGAN 결과를 비교한 예시입니다.  
> 예: `assets/stylespade_vs_semanticstylegan.png`

<p align="center">
  <img src="assets/stylespade_vs_semanticstylegan.png" width="90%">
</p>

**Qualitative Comparison**

| Model                | Background Realism | Crack Fidelity | Mask Control | Notes |
|----------------------|-------------------|----------------|-------------|-------|
| **SemanticStyleGAN** | 🟢 Very High      | ❌ Often blurred / missing | ❌ Weak | Great for diverse scenes, but thin cracks are easily distorted |
| **StyleSPADE**       | 🟢 High           | ✅ Sharp cracks | ✅ Strong   | Best trade-off between realism and structure preservation |

> SemanticStyleGAN is powerful for general style transfer,  
> but for **thin, sparse crack patterns**, StyleSPADE provides more reliable control.
