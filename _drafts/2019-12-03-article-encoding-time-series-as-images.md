---
layout: post
title: "Article Review: Encoding Time Series as Images for Visual Inspection and Classification Using Tiled Convolutional Networks"
date: 2019-12-03
---
# Bottom Line Up Front

The author tries out three new data encodings for single-channel time series data which they then feed into a tiled convolutional neural network for a classification task and conclude that this method is competitive with state of the art.

# Summary

This [conference paper](https://www.aaai.org/ocs/index.php/WS/AAAIW15/paper/viewPaper/10179) was published in Papers from the [2015 AAAI Workshop](https://www.aaai.org/ocs/index.php/WS/AAAIW15/index).

Time series data is really common in the real world, but most machine learning treatments I have seen focus on speech (which benefits from FFT) and 1-d convolutions. This is a shame as it means that neural networks can't take advantage of the immense amount of work that has gone into 2d convolutional neural networks. It is beneficial 

# Thoughts

This article is yet another reminder that I should be thinking about how to encode my data in a meaningful way. 

That said, I'm not sure about the advantages of polar coordinates. At the very least it seems like you would need to coerce the convolutional windows to account for a sudden change in value--e.g. a voltage spike when a switch is closed in an electrical circuit. This wouldn't apply to a 1-d convolutional approach. They also assume that the range of values presented is complete, since they min/max encode their values into the range \([-1, 1]\). The Gramian Annular Field is an interesting way to account for this. It looks like the inner product used to convert from polar coordinates allows for the pairwise comparison--looking at each time lag. That step might be unnecessary; you could possibly also have an autocorrelation for each time lag which would (I suspect) preserve the same information.

The second approach the author takes is more interesting to me (and I suspect is related to the autocorrelation I describe above). If the timeseries data are sampled from a markov process this seems like a good way to approximate that into an image-like input for a convolutional network. The author also claims that

> By assigning the probability from the quantile at time step \(i\) to the quantile at time step \(j\) at each pixel \(M_{ij}\), the MTF \(M\) actually encodes the multi-span transition probabilities of the time series. \(M_{i,j\vert\verti-j\vert=k}\) denotes the transition probability between the points with time interval \(k\).

If that is so, it seems like this method includes the transition probability from state \(q_i\) to state \(q_j\) for each time lag between \(i\) and \(j\). This should allow for identification of single events that produce multiple signals separated by a span of time, even if there are other processes that create noise in the intervening period. This in itself seems like it takes the place of a convolution where each entry in the matrix is the coincidence at some time lag.

I'm not familiar with the tiled convolutional networks used here. They seem like they are worth more reading. I will say that I wish that neural network architectures bore more relationship to their names. I find myself getting lost in a maze of hastily assigned proper nouns. I'm a nuclear engineer--where are my backronyms?!

# Takeaways

I had planned to throw convolutional networks at my dissertation problem by converting my (digital time-series) data into pixelated images just to see if it sticks, but now I see that I need to think more deeply about how to encode my data. Tiled convolution windows seem interesting as well. Since I think I understand the physics of my data (mostly), pre-hinting my network in that direction might accelerate my training loops. Certainly the idea of unsupervised pre-training is attractive, even though I still don't understand it. Guess that'll be the next paper I review!

## References to check out

1. [Tiled convolutional networks](https://papers.nips.cc/paper/4136-tiled-convolutional-neural-networks.pdf)
2. [Why Does Unsupervised Pre-training Help Deep Learning?](http://www.jmlr.org/papers/volume11/erhan10a/erhan10a.pdf)

Bengio citation count: 3/29
Hinton citation count: 5/29
