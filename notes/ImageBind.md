## Paper Review

By Zitao Shuai (ztshuai@umich.edu) 

### Basic Information

Title: IMAGEBIND: One Embedding Space To Bind Them All

Source: CVPR2023

Institute: FAIR

### Overview

Multi-modal learning never only focuses on image and text modalities. **However, there might be a dimensional catastrophe problem: given N modalities, we have $O(N^2)$ multi-modal tasks and each task needs corresponding paired data.** This would raise two essential problems: the paired data of some modality pairs is not sufficient; we might need much computation for the different tasks. Based on these practical problems, current works aim to find a unified solution for training multi-modal models with various modalities. However, these works often only consider 2 or 3 modalities in their experiments, and if there exists a unified model that can ensemble a wider range of modalities remains an unknown question. And how can we ensemble different modalities in the same framework?

This paper tries to answer these questions. It presents a new approach to learning a joint embedding across six different modalities - images, text, audio, depth, thermal, and IMU data. And their method is to bind each modality to the image modality, high-levelly speaking. In the following parts, we will look into their intuition and motivation, and how they propose their method based on these.

There might be two questions:

1. why different modalities which have different types of data containing different semantics can be aligned
2. why the joint latent space can contain information from different modalities

### Towards unified multimodal learning

Current work has verified that some parameters can be should be different modalities [1] [3]in the multi-modal learning domain. Using the shared model might enhance the fusion process of different modalities, and avoid using more parameters.

![image-20231027074102800](asset/image-20231027074102800.png)

[1] Bao H, Wang W, Dong L, et al. Vlmo: Unified vision-language pre-training with mixture-of-modality-experts[J]. Advances in Neural Information Processing Systems, 2022, 35: 32897-32912.

We have also seen some works that aim to unify different multi-modal tasks [2] with the diffusion model.

[2] Xu X, Wang Z, Zhang G, et al. Versatile diffusion: Text, images, and variations all in one diffusion model[C]//Proceedings of the IEEE/CVF International Conference on Computer Vision. 2023: 7754-7765.

[3] Huang Y, Xue H, Liu B, et al. Unifying multimodal transformer for bi-directional image and text generation[C]//Proceedings of the 29th ACM International Conference on Multimedia. 2021: 1138-1147.

And in the related work section of this paper, the authors also mention some related conclusion from the NLP domain, that is:

> if languages are trained in the same latent space through learned implicit bridging, translation can be done between language pairs on which no paired data is provided.

Note:

Even though they mention the evidence from the text side, they bind different modalities to the image instead of the text, which is quite interesting.

And can text modality be bonded with other modalities? A recent work seems to have answered the question [4]. In this work, 11 modalities are bonded with the text side. 

We might ask the question: how to determine if a modality could be used as the anchor?

[4]Zhu B, Lin B, Ning M, et al. LanguageBind: Extending Video-Language Pretraining to N-modality by Language-based Semantic Alignment[J]. arXiv preprint arXiv:2310.01852, 2023.

### Make different modalities aligned

**Something still remains unsolved:**

•Parameter sharing is a good way to fusion modalities but we still need O(N^2) contrastive losses.

•Multi-flow network might reduce the size of model but it requires O(N^2) data-flows and feed-forwards

•Current solutions still need paired data or context models pre-trained with the pairs

**To unify different modalities, we might expect:**

•Each modality is aligned with other modalities

•O(N) Contrastive losses

•Each modality could only appear in one combination of paired modalities

**Insight: connected graph**

If two modalities are aligned with a loss term, we add an edge between them.

The min number of edges could be N-1.

![image-20231101235759603](asset/image-20231101235759603.png)

![image-20231101235810273](asset/image-20231101235810273.png)

**Remaining question: how to choose the anchor**

There should exist correlations between the anchor and other modalities:

•Paired data

•Connection of semantics of different modalities

**In this paper, image is used as anchor**

•Each considered modality is closely related to the image(video) modality

•Each modality has paired data with images
