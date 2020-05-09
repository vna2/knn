# knn
python knn algorithm

#What is the “Curse of Dimensionality”?

The “Curse of Dimensionality” is a tongue in cheek way of stating that there’s a ton of space in high-dimensional data sets. The size of the data space grows exponentially with the number of dimensions. This means that the size of your data set must also grow exponentially in order to keep the same density. If you don’t, then data points start getting farther and farther apart.

#Why is this especially problematic for k-nearest neighbors?

At face value it doesn’t seem that k-nearest neighbors would be especially sensitive to this problem. Every machine learning algorithm needs a dense data set in order to accurately predict over the entire data space. Errors arise in all algorithms if there are gaps between the data. So what makes k-nearest neighbors special?

The special challenge with k-nearest neighbors is that it requires a point to be close in every single dimension. Some algorithms can create regressions based on single dimensions, and only need points to be close together along that axis. k-nearest neighbors doesn’t work that way. It needs all points to be close along every axis in the data space. And each new axis added, by adding a new dimension, makes it harder and harder for two specific points to be close to each other in every axis.

Joel Grus does a good job of describing this issue in Data Science from Scratch. In that book he calculates the average and minimum distances between two points in a dimension space as the number of dimensions increases. He calculated 10,000 distances between points, with the number of dimensions ranging from 0 to 100. He then proceeds to plot the average and minimum distance between two points, as well as the ratio of the closest distance to the average distance (Distance_Closest / Distance_Average).

In those plots, Joel showed that the ratio of the closest distance to the average distance increased from 0 at 0 dimensions, up to ~0.8 at 100 dimensions. And this shows the fundamental challenge of dimensionality when using the k-nearest neighbors algorithm; as the number of dimensions increases and the ratio of closest distance to average distance approaches 1 the predictive power of the algorithm decreases. If the nearest point is almost as far away as the average point, then it has only slightly more predictive power than the average point.

Think of how this problems applies to our apple example from above. It’s a bit counter-intuitive, since the apple example is inherently in 3 dimensions, but imagine that the distance to the next closest item in the produce section is about the same as the average distance. Suddenly you can’t be sure if the nearest item is another gala apple, or a fuji apple, or an orange, or a bunch of parsley. As far as the k-nearest neighbors algorithm would be concerned, the entire produce section would be jumbled together.
