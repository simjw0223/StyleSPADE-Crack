## 🧩 StyleSPADE-Crack: Pretrained Model for Crack Image Synthesis

This repository provides the pretrained weights of **StyleSPADE**,  
a customized SPADE-based generative model designed for **realistic crack image synthesis**.  
It is used to augment training datasets for crack segmentation tasks.

<br>

---

<br>

## What is StyleSPADE?

StyleSPADE is an enhanced version of NVIDIA’s SPADE generator,  
modified to include a **style encoder** that injects texture and appearance information  
into each SPADE normalization layer.

### Key Features
- Generates diverse pavement/wall/ground background textures  
- Preserves fine crack structures  
- Produces more realistic images than vanilla SPADE or SemanticStyleGAN  
- Highly effective for training crack segmentation models

<br>

---

<br>

## Files in This Release

| File name | Description |
|----------|-------------|
| `latest_net_G.pth` | Pretrained Generator weights |
| `latest_net_D.pth` | Pretrained Discriminator weights |
| `loss_log.txt` | Training loss curve logs |

<br>

---

<br>

## StyleSPADE Generator Architecture

<br>

<p align="center">
  <img width="1421" height="508" src="https://github.com/user-attachments/assets/dbc4e061-f2c8-4602-864d-04ae63f78351"/>
</p>

<br>

---

<br>

## StyleSPADE vs SPADE

StyleSPADE extends the original SPADE architecture by introducing a **style encoder**  
that injects background texture information into every SPADE normalization block.  
While SPADE preserves the spatial structure of cracks well, it often produces repetitive,  
gray, and uniform backgrounds. StyleSPADE improves realism by adding diverse background styles  
while maintaining crack fidelity.

<br>

<p align="center">
  <img width="2000" height="754" alt="그림2" src="https://github.com/user-attachments/assets/3179940a-09bb-4f13-aa31-60473ca498d8" />

</p>

<br>

### Comparison Summary

- **SPADE**
  - Relies only on the segmentation mask  
  - Preserves crack geometry  
  - Background often dull, repetitive, and gray-toned  

- **StyleSPADE (Ours)**
  - Adds a style encoder → diverse realistic textures  
  - Maintains crack geometry  
  - Produces visually rich and realistic images  

<br>

---

<br>

## StyleSPADE vs SemanticStyleGAN

SemanticStyleGAN provides strong scene-level realism and style variety,  
but it lacks precise geometric control—thin crack structures often blur or disappear.  
StyleSPADE preserves fine-grained crack shapes thanks to mask-driven SPADE modulation,  
while still generating diverse textures through style injection.

<br>

<p align="center">
  <img width="1090" height="414" alt="그림3" src="https://github.com/user-attachments/assets/d0438b1c-f735-4638-a98d-f0da97e91fe6" />

</p>

<br>

### Comparison Summary

- **SemanticStyleGAN**
  - Very strong background realism  
  - Weak geometric control → cracks may blur  
  - Less suitable for thin structural patterns  

- **StyleSPADE (Ours)**
  - Strong mask-based spatial modulation  
  - Preserves thin and complex crack structures  
  - Balanced realism + structure fidelity  

<br>

---

<br>

## How to Use the Pretrained Weights

```bash
git clone https://github.com/simjw0223/StyleSPADE-Crack.git
cd StyleSPADE-Crack
