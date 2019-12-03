---
layout: post
title: "Article Review: Encoding Time Series as Images for Visual Inspection and Classification Using Tiled Convolutional Networks"
date: 2019-12-03
---
# Bottom Line Up Front

The author tries out three new data encodings for single-channel time series data which they then feed into a tiled convolutional neural network for a classification task and conclude that this method is competitive with state of the art.

# Summary

This [conference paper](https://www.aaai.org/ocs/index.php/WS/AAAIW15/paper/viewPaper/10179) was published in Papers from the [2015 AAAI Workshop](https://www.aaai.org/ocs/index.php/WS/AAAIW15/index).

Time series data 

# Thoughts

This article is yet another reminder that I should be thinking about how to encode my data in a meaningful way. 

That said, I'm not sure about the advantages of polar coordinates. At the very least it seems like you would need to coerce the convolutional windows to account for a sudden change in value--e.g. a voltage spike when a switch is closed in an electrical circuit. This wouldn't apply to a 1-d convolutional approach. They also assume that the range of values presented is complete, since they min/max encode their values into the range \([-1, 1]\). The Gramian Annular Field is an interesting way to account for this. It looks like the inner product used to convert from polar coordinates allows for the pairwise comparison--looking at each time lag. That step might be unnecessary; you could possibly also have an autocorrelation for each time lag which would (I suspect) preserve the same information.

The second approach the author takes is more interesting to me. If the timeseries data are sampled from a markov process this seems like a good way to approximate that into an image-like input for a convolutional network. The author also claims that

    By assigning the probability from the quantile at time step \(i\) to the quantile at time step \(j\) at each pixel \(M_{ij}\), the MTF \(M\) actually encodes the multi-span transition probabilities of the time series. \(M_{i,j\vert\verti-j\vert=k}\) denotes the transition probability between the points with time interval \(k\).

# Takeaways

## References to check out
