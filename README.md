# Los Alamos Authentication Classification

The following solution is a meta analysis of classifiers available in [`scikit-learn`](http://scikit-learn.org/stable/index.html) partially based on the following examples:

* [http://scikit-learn.org/stable/auto_examples/classification/plot_classifier_comparison.html#sphx-glr-auto-examples-classification-plot-classifier-comparison-py](http://scikit-learn.org/stable/auto_examples/classification/plot_classifier_comparison.html#sphx-glr-auto-examples-classification-plot-classifier-comparison-py)
* [http://scikit-learn.org/stable/auto_examples/model_selection/plot_randomized_search.html#sphx-glr-auto-examples-model-selection-plot-randomized-search-py](http://scikit-learn.org/stable/auto_examples/model_selection/plot_randomized_search.html#sphx-glr-auto-examples-model-selection-plot-randomized-search-py)
---
To avoid memory limitations within Python, native commands are used via the `subprocess.Popen` class to download and decompress the archived auth.txt.gz file if necessary and find the population size and probability of successful authentication for sampling. Through manual examination of the dataset the high success rate of authentication became apparent so with prior knowledge of the statistically correct technique to determine sample size (formula here) given a confidence level and interval a relatively small number of elements was needed. The original number of records exceed one billion but given the `p * (1 - p)` terms in the formula the samples required for a 99.5% confidence level with a ±0.5% interval are 3202 elements, only about 0.0003% of the total data and much more practical to train the classifiers with.

Given the scope of hyperparameters for most of the classifiers an exhaustive grid search was not within reason so a randomized search over predefined ranges of paramters was chosen for training and validation.  Throughdevelopment of this notebook two of the classifiers, `SCV` and `GaussianProcessClassifier`, were significantly more resource intensive without being more accurate so their options are commented out and the results not included in the analysis.

The timestamps included in the output provide an estimate for how long the commands run on the following system:

* i7-3632QM CPU at 2.20 GHz
* 16 GB of memory
* 512 GB solid state drive
* 200 MB internet connection over 5 GHz wireless router

Please review the documentation and timestamps before running the notebook (especially the note pertaining to downloading and decompressing the auth.txt.gz file).

---
* System Requirements
  * Operating System = Linux based with "gunzip", "wc", "grep", and "shuf" commands available
  * Python version = 2.7.5
  * Internet connection with access to [https://csr.lanl.gov/data/cyber1/auth.txt.gz](https://csr.lanl.gov/data/cyber1/auth.txt.gz) if archive not available locally
  * ~80 GB free space on partition of local directory notebook is executed in (if auth.txt.gz and auth_decompressed.txt files are not available locally)
* Version numbers of included third party packages:
  * jupyter - 1.0.0
  * numpy - 1.14.5
  * pandas - 0.23.3
  * requests - 2.6.0
  * scikit-learn - 0.20.0
  * scipy - 1.1.0
