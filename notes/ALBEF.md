## Paper Review

By Zitao Shuai (ztshuai@umich.edu) 

### Basic Information

Title: Align before Fuse: Vision and Language Representation Learning with Momentum Distillation

Source: NIPS2021

Institute: Salesforce Research

### Overview

Clip has achieved great success and the Image-text contrastive loss has become a widely utilized loss term in the multi-modal learning domain. As a result, every time we mention multi-modal learning, we might think of this contrastive loss as well as the Clip. However, Clip only shows we can align two modalities using contrastive loss, and the pre-trained model has great generalization ability. Even though we can do zero-shot classification using Clip without fine-tuning or extra structures, for many other multi-modal tasks like generation, we might need to utilize both the text embedding and the image embeddings. Therefore, in the multi-modal domain, people may focus on how to utilize the two embeddings. A natural way is to use an extra network to learn the interaction between these two modalities, and how to fuse two modalities in a better way is a long-standing problem. This paper shows the potential of fusing multiple modalities after aligning their latent representation and proposes the method ALBEF, and gives an intuitive explanation of the fusion process. 

Note:

I don't think it is a modification of Clip, even though the design of the loss function might based on the image-text contrastive loss of the Clip. From the conclusions they want to draw, we can see that Clip focuses on training a generalizable model in a self-supervised way and the key point is aligning two modalities, while ALBEF focuses on fusing two modalities. The similarity might be, that ALBEF has verified that well-aligned representation will also benefit the modality-fusion process.

Besides, nowadays we believe a pre-trained model that performs well on downstream tasks should have similar optimization objects with those of the downstream tasks.  However, the loss function of ALBEF looks pretty high-level while the model has high performance on the downstream benchmarks. I think it's reasonable since their goal is to fuse two different modalities and their benchmarks are not specific like image segmentation or object detection, they are designed to test the fusion degree of the model. Hence the consensus of the design of optimization objects is still held.

### Why align before fusion

We might agree that the aligned representation will benefit downstream tasks and the fusion might be easier if we use the aligned features. However, in 2021, we haven't seen much success of the alignment-based method in the multi-modal learning domain. A common question is: if the aligning process will lead to information loss?

From the trustworthy AI and machine learning domain, when they consider generalization ability, they may talk about invariant semantics, over-pessimistic semantics, etc. An important measure is the entropy-based approach.

A popular technique of the entropy-based methods is mutual information, and this paper utilizes it for analyzing the theoretical foundation of the ALBEF.

This paper view (image, text) pairs as joint data points, and the image can be viewed as (image, 0) the text can be viewed as (0, text), and both of them can be viewed as a transformation of the raw data point. 

Hence we might like to maximize the similarity of different transformations(views) of a given data point. A simple way is to consider the mutual information and maximize the lower bound of it. Hence they consider the InfoNCE loss and MLM loss for alignment:

![image-20231030145128425](asset/image-20231030145128425.png)

![image-20231030145140315](asset/image-20231030145140315.png)

The mutual information might not be able to guarantee the integrity of the semantics of the image side and the text side, but it looks like is capable of preventing the model from distorting the semantics of the raw data point.

Note:

And it's also interesting to see the claim "B*oth ITC and MLM generate views by taking partial information from an image-text pair*" and "*momentum distillation can be considered as generating alternative views from the entire proposal distribution*".

And there is also some evidence in OOD that shows the momentum encoder will learn less spurious correlation, maybe we have more storylines to tell.

### View modality-fusion as a downstream task

![image-20231030151704548](asset/image-20231030151704548.png)

If we have a downstream task that is to use image embeddings to generate multi-modal-fused embeddings for various tasks. Then we should maximize the similarity of the input image embedding and the fused embedding. Hence the paper proposes to utilize the MLM loss for this aligning process.

Using hard negatives might increase the difficulty of the loss function, which forces the fusion module to learn the fine-grained interaction of the two modalities.
