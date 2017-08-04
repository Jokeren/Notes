## Source

Arxiv

https://arxiv.org/abs/1607.02241

## Problem

There is limited understanding from a theoretical point of view as to why low precision networks lead to training difficults.

## Motivation

The size and complexity of CNN networks hindle the pervasive deployment of deep learning applications on embedded systems. Low precision data representations, however, usually have lower accurarcy than the original model. The problem is caused by approximation of activations in the backward phase during fine-tuning or training.

## Solution

1. Using full precision activations.

2. Because activations of top layers are more reliable than bottom layers, we could just fine-tune top layers. In doing this, bottom layers could receive more accurate errors.

3. Iteratively fine-tune each layer, fixing other layers as full precision.

## Experiments

Regarding the above methods, it seems that the first one achieves the best results.
