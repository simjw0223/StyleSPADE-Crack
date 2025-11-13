## 🧩 StyleSPADE-Crack: Pretrained Model for Crack Image Synthesis

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







---
## StyleSPADE Generator Architecture

<img width="1421" height="508" alt="그림1" src="https://github.com/user-attachments/assets/dbc4e061-f2c8-4602-864d-04ae63f78351" />


