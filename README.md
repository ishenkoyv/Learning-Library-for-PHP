# Learning Library for PHP 
Some machine learning/artificial intelligence/natural language processing algorithms implemented in PHP

Copyright (C) 2011, 2012, 2013 Giuseppe Burtini <joe@truephp.com>

## Instructions

In general, you'll want to grab just the "required" features from this repository for your project -- a lot of the individual methods are standalone (or only dependent on the accessory directory). Browse the lib/ directory and decide which techniques you are interested in.

## Available Algorithms

### Unsupervised
* **DBScan** (dbscan.php) - Density Based Clustering [1][2] - a clustering/unsupervised classification algorithm based on the idea of "density reachability." This algorithm is a win over the others because one does not need to specify the number of clusters _a priori_. The parameters are $e(psilon), the size of a neighborhood to visit (a noise threshold) and $minimumPoints, the minimum number of points to form a cluster.
* **K Means** (kmeans.php) - the standard clustering algorithm which breaks data in to k "most different" groups. The technique is simply to reposition the "centroid" to the average of all points until it doesn't move any longer.
* **K Nearest Neighbors** (knn.php) - similar to K Means, except "flipped on its head" - a clustering algorithm which builds the best clusters that are of size k (rather than building k clusters). ([Wikipedia](http://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm))
* **Markov Chain** (markovchain.php) - a n-order Markov Chain implementation - takes in a list of values to train and computes probabilities simply from observations.

### Parametric
* **Anomaly Detection** (anomaly\_detection.php) - assume a normal distribution, train data (n-dimensional) and then test to see if a given record is an "outlier" (less likely than a given percent, given the distribution). Assumes semi-stationarity (training can happen online with testing if you wish). 
* **Naive Bayes** (naivebayes.php)
* **Regression** (regression.php) including optimization implementations for gradient descent ("take a step in the right direction"), stochastic gradient descent, normal equations and a logistic regression implementation.

## References
* [1] Domenica Arlia, Massimo Coppola. "Experiments in Parallel Clustering with DBSCAN". Euro-Par 2001: Parallel Processing: 7th International Euro-Par Conference Manchester, UK August 28–31, 2001, Proceedings. Springer Berlin.
* [2] Hans-Peter Kriegel, Peer Kröger, Jörg Sander, Arthur Zimek (2011). "Density-based Clustering". WIREs Data Mining and Knowledge Discovery 1 (3): 231–240. doi:10.1002/widm.30.

## To-Do

* Update to PHP 5.x, change to use namespaces instead of messy function names.
* Lots of missing documentation - most public facing methods are currently undocumented; bad.
* Build TF-IDF class / simple vector search space class.
* Build MonteCarlo class (with callbacks)
* OOize all appropriate algorithms (use "train" and "test" when possible).
* Complete tests for algorithms that do not have them.
* Consider adding a pathfinding/graph search algorithm set.
* Ensemble and boosting learning methods like random forests / CART / BART
* Neural networks and HMMs.
* NLP work, specifically a class for using WordNet and the Stanford Core NLP library; eventually, NLP work should probably be forked as its own project.

## Notes for Use

For effective use, a lot of this library will have to be customized. This is a largely academic project. In many cases I've opted to write clearer code in favor of faster code, and in other cases, I've excluded useful features for "real world" applications (like training, saving the trained data to a file, and then running the actual "estimates" after in a separate location). 

If you would like to deploy this in a real world application, I would be happy to discuss work on any machine learning problems you do have: contact me at joe@truephp.com.

Most of the code in this library is designed such that the rest of the library can just be thrown away if you would like to use it. In parametric/ and unsupervised/ each "type" of learning is implemented in a file of its own (though, regression stuff gets a whole directory!) so as to be useful without loading the rest of the library.

There are many things that can be improved and there are many known properties (and optimization techniques) that can be used to improve the performance of these algorithms that have not been implemented here. This is very much a "first run" at implementing a lot of these algorithms in PHP and should be looked at as a possible starting point for learning algorithms in PHP, not necessarily a deployable library.

In many cases, the right answer will be to implement the learning algorithms in a faster language and use PHP only to evaluate their probabilities / compute results from the existing estimates. 

## License

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details. 

You should have received a copy of the GNU General Public License along with this program; if not, write to the Free Software Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

If you need to work with the Learning Library in an environment that is not conducive to the GPL, please contact me at <joe@truephp.com> and we can discuss alternative licensing terms.

