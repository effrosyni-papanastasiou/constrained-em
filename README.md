# Constrained-EM

This work is part of the conference paper "Bayesian Inference of a Social Graph with Trace Feasibility Guarantees" that has been submitted to the **[ASONAM 21](http://asonam.cpsc.ucalgary.ca/2021/)**. The link for the work can be found **[here](https://hal.archives-ouvertes.fr/hal-03247163)**.

**Constrained-EM** is a non-trivial modification of the Expectation-Maximization algorithm by **Newman [1]** which incorporates a set of feasibility constraints and a set of auxiliary variables into a graph inference process to guide it towards the feasibility of the trace. 

For the solution of the optimization problem, we use **[PuLP](https://pypi.org/project/PuLP/)**, an open-source linear programming library for Python.

## Prerequisites

To run the files you must first create a 'datasets' directory that includes the dataset you want to investigate. Our work focuses the analysis on data from Twitter but we could apply the algorithm on other domains as well. Online social media datasets must have the form *(pid, t, uid, rid)* to include four types of information: 
1. The unique post id *pid*. The post could either be an original post (i.e., a tweet) or a repost of an original post (i.e., a retweet).
2. The timestamp of the post's creation *t*.
3. The *uid* of the user who posted it.
4. The repost id *rid* that is either equal to -1 if the post is an original post, or equal to the *pid* of the original post if it is a repost. 

For this work we used a real-world Twitter dataset coming from Kaggle, referred to as **[Russian](https://www.kaggle.com/borisch/russian-election-2018-twitter)**. It is not added in this repository due to size constraints.

## Files

This repository includes five Jupyter notebooks (found in the 'jupyter-notebooks' directory) that make use of the dataset added inside the 'datasets' directory. The notebooks must be executed in the following order:
- **0-trace-preprocessing.ipynb**
Our method relies on rich information extracted from a social media trace during the pre-processing phase. This notebook extracts necessary quantities that will be used in the next steps. All new information is extracted in an 'extracted' directory that must be created inside the 'jupyter-notebooks' directory.
- **1-constrained-em.ipynb**
This notebook contains the main algorithm of **Constrained-EM**. Results are extracted inside the 'extracted' directory.
- **2-newman.ipynb**
The application of **Newman's [1]** algorithm on our trace. We run it to compare it with our method. Results are extracted inside the 'extracted' directory.
- **3-saito.ipynb**
The application of the algorithm by **Saito et al. [2]** on our trace. We run it to compare it with our method. Results are extracted inside the 'extracted' directory.
- **4-evaluation.ipynb**
Evaluates the above methods, along with baseline inference methods **Star** and **Chain** and compares them with our method. It uses the results inside the 'extracted' directory as input.

## References
[1] M. E. J. Newman, 'Network structure from rich but noisy data', *Nature Physics*, vol. 14, 2018, pp. 67-75.  
[2] K. Saito, R. Nakano, and M. Kimura, 'Prediction of Information Diffusion Probabilities for Independent Cascade Model', in *International Conference on Knowledge-Based and Intelligent Information and Engineering Systems*, vol. 5179, 2008, pp. 67-75.

## Citation

To use this repository in your work please cite the following: 

E. Papanastasiou, A. Giovanidis, 'Bayesian Inference of a Social Graph with Trace Feasibility Guarantees', 2021. **[⟨hal-03247163⟩](https://hal.archives-ouvertes.fr/hal-03247163)**

## License

MIT

