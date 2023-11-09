## Paper Review

By Zitao Shuai (ztshuai@umich.edu) 

### Basic Information

Title: BLIP: Bootstrapping Language-Image Pre-training for Unified Vision-Language Understanding and Generation

Source: ICML2022

Institute: Salesforce Research

### Overview

I have heard a trick that we can throw away some samples that have large losses. The logic based on it is that we think the samples with large losses are not good ones, and their mapping from input to label is somehow noisy. 

This paper introduces a novel Vision-Language Pre-training (VLP) framework designed to address existing limitations in the field named BLIP. While previous VLP models excel in either understanding-based or generation-based tasks, BLIP is proposed as a flexible solution capable of performing well in both areas. It achieves this by removing some undesired noisy web data through a well-designed bootstrapping process. Specifically, a captioner generates synthetic captions, while a filter removes the noisy ones. Besides the efficiency in benefiting the pre-training process,  this might be able to help us generate high-quality/clean samples for other tasks. 

Note:

By the way, I think there might exist a trade-off as well. Some samples might contain diverse semantics and they might be incorrectly viewed as bad samples, so we might like to train the model with the whole dataset and remove some undesired samples after several epochs. But in this way, the model might be biased due to fitting some potentially bad samples in the early stage.

Salesforce has done many interesting work, and we have seen BLIP, and ALBEF this week. I think both methods treat the noisy paired data as an essential issue and try to address this problem in different ways. 

For further improvement, we might like to enhance the adversarial process, since the current strategy is quite naive.

### Details of the framework

Shared structures and less data flows

The overview of the network structure:

![image-20231031102828425](asset/image-20231031102828425.png)



I think there might be two important things in the paper we might like to focus on:

1. the image encoder is large and computation-heavy.
2. there are many components of the multi-modal tasks, thus we might have a large number of parameters

Through the design of the model of this paper, we might be able to get some insight on the solutions to these problems:

1. firstly, we need to reduce the data flow through the image encoder. In this paper, the image encoder only be used once, while the text encoder has three data flows.
2. second, some parameters can be shared, this conclusion has also been illustrated in the VLMO. In BLIP, three data flows share the same self-attention module, and they use different tokens and some small modifications to achieve different goals.

![image-20231031105654396](asset/image-20231031105654396.png)

It looks like an inverse problem, if we focus on the point that "generate high-quality sample". And it also looks like a min-max or adversarial problem, if we consider the removing operation of the filter.

We can look into the details of the captioner and the filter: the filter utilizes the image-grounded text encoder while the captioner utilizes the image-grounded text decoder. They are both used in the main data flow, which means these designs are not consuming.

#### De-noise: self-supervision from pseudo samples

I think the most significant difference between ALBEF and BLIP is that BLIP uses the caption-filter process to replace the momentum distillation process.

ALBEF distills the knowledge from the momentum-updated encoder, and we can interpret this process as using the supervision from pseudo embeddings. This can be viewed as data augmentation or generating different transformations/views of the raw data.

This paper also considers using pseudo samples, the captioner of the BLIP synthesizes the caption T_S, and the filter will distinguish if this synthesized sample and its corresponding image should be removed, this process uses the learned ITM head which contains information of human-annotated data. 

