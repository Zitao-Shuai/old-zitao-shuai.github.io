## Paper Review

By Zitao Shuai (ztshuai@umich.edu) 

### Basic Information

Title: GLoRIA: A Multimodal Global-Local Representation Learning Framework for Label-efficient Medical Image Recognition

Source: ICCV2021

Institute: Stanford University

### Overview

This paper is an outstanding paper and it's one of the selected papers of our professor. I think this paper illustrates the efficiency of local contrastive loss in the biomedical domain. In the biomedical vision-language pretraining scenes, the spatial relationship and temporal relationship between images and texts are really important, and this work focuses on the spatial information implicitly and proposes a local contrastive loss to better align fine-grained representations.

Note:

In 2021, the topic of contrastive learning is quite heated, but before 2021, many of us hadn't realized the potential of multi-modal pre-training. This work is concurrent with CLIP, so I think the idea is to use text to instruct the training process of the image encoder (instead of focusing on both sides). Nevertheless, the method proposed in this paper is verified in many papers in the biomedical vision-language pretraining domain. 

This paper is well-organized and has delivered a good story, so I will summarize something about the writing of the introduction of this paper.

### Analysis on introduction

#### Point & background: efficient

How to define efficient:

labeled data is not sufficient + we have plenty of unlabeled data-> how to utilize unlabeled data

Note:

In the first paragraph, the authors throw the main point they focus on and why this point needs to be handled. 

#### Motivation & challenge: pathology usually occupies small proportions of the medical image

small portion -> should be aligned accurately and achieve fine-grained representation

Note:

Then in the second paragraph, they introduce the technical approach they consider while avoiding mentioning other irrelevant approaches. Then they introduce their technical motivation and how their consider the proposed problem.

#### Method

In the third paragraph, the authors propose their method directly. I think the format can be simplified as "motivation + technical design", which is commonly used.

I think this paragraph has a clear structure:

part1: summary of high-level technical approach

part2: technical component 1: motivation+techniques

part3: technical component 2: motivation+techniques

part4: technical component 3: motivation+techniques

#### Contribution

Different from typical CS-style papers, in this section, the authors use "contribution + benefit/analysis" format to deliver their contribution. I think this might make this section a little bit messy, while quite insightful. And they summarize the contribution briefly in the final paragraph. The writing style of the contribution section would highlight the motivation of this paper, and make it more interesting.
