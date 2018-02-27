## dimensions

let input be C x Hi x Wi

kernel : N x C x Hk x Wk
- N : number of kernel features
- C : number of input channels
- Hi, Wi : height, width of input
- Hk, Wk : height, width of kernel

bias will be scalar N

output = N x Ho x Wo
- N : number of output channels
- Ho, Wo : height, width of output

## forward and backward

middle of https://cs231n.github.io/convolutional-networks/ page, you can find
[this animation](https://cs231n.github.io/assets/conv-demo/index.html)
that shows how convolution is done.

another site,
[Back Propagation in Convolutional Neural Networks — Intuition and Code](https://becominghuman.ai/back-propagation-in-convolutional-neural-networks-intuition-and-code-714ef1c38199)
that shows how forward and backward works.