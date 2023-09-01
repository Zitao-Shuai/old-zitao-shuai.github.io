## Introduction for CS229

**Source**: [Stanford CS229M - Lecture 1: Overview, supervised learning, empirical risk minimization - YouTube](https://www.youtube.com/watch?v=I-tmjGFaaBg&list=PLoROMvodv4rP8nAmISxFINlGKSK4rbLKh&index=1)

**Motivation**: To learn more about machine learning theory and receive more illustrations on formulating problems, proposing theories, and proving theorems.

**Studying pipeline for each chapter**:

1. read the notes: [tengyuma/cs229m_notes (github.com)](https://github.com/tengyuma/cs229m_notes) for an overview of the techniques we might use.
2. watching the videos to get the illustration for each statement and theorem and the tricks of proofs.
3. summarize the useful techniques and important insights for your own domains then generate notes.

## Basic formulations

Supervised learning: learning a mapping from X to Y / $h:X\to Y$

loss function: $l:Y\times Y\to R$

distribution P over $X\times Y$

The expected loss: $E_{(x,y)\sim p}[l(h(x),y)] $

For each model: $\theta\in R^d$

For the class of the model (hypothesis class): $H=\{h:h_{\theta}(x)=\theta^Tx,\theta\in R\}$
