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

That said, I'm not sure about the advantages of polar coordinates. At the very least it seems like you would need to coerce the convolutional windows to account for a sudden change in value--e.g. a voltage spike when a switch is closed in an electrical circuit. This wouldn't apply to a 1-d convolutional approach. They also assume that the range of values presented is complete, since they min/max encode their values into the range \([-1, 1]\). 

# Takeaways

## References to check out
