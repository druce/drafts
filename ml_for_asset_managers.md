Marcos López de Prado is one of the most prolific and [most-read](https://papers.ssrn.com/sol3/cf_dev/AbsByAuth.cfm?per_id=434076) teachers and writers on machine learning in finance: formerly head of ML at AQR, head of quant strategies at Guggenheim, professor at Cornell, author of [Advances in Financial Machine Learning](https://www.amazon.com/Advances-Financial-Machine-Learning-Marcos/dp/1119482089/) which is probably the most popular book on the subject. So when he publishes a book on [Machine Learning for Asset Managers](https://www.amazon.com/Machine-Learning-Managers-Elements-Quantitative) it's a big deal.

- To get the most out of the book, should have some stats / ML at the level of eg Andrew Ng and Hastie/Tibshirani. you don't need grad level math, stochastic calculus. 
- This is not a cookbook or a book about the philosophy of cooking. It's, here's is the basic chemistry you should know to boil an egg.

- short monograph, appendices & footnotes start on p. 125 on the most important parts of machine learning to know, can digest chapters in chunks. could certainly be expanded into a 500-page textbook for a full course

- what did I like

- constructive criticism
  - pretty short, dense, monograph, would be nice to have a course that was the equivalent of Andrew Ng for investing with machine learning.
- summary (below)
- maybe we should do an official book group with monthly meeting, on Zoom, each time 2-3 people present a paper/chapter

# Chapter 1. Intro

ML is modern statistics

Most econometric models were devised for estimation by hand and are a product of their time.

- the key insight of machine learning is that if the founders of statistics had access to computers and big data, they might have done things very differently.

"two words explain the classic preference for parametric models: mathema- tical tractability. In a world of sliderules and slow mechanical arithmetic, mathematical formulation, by necessity, becomes the computational tool of choice. Our new computation-rich environment has unplugged the mathe- matical bottleneck, giving us a more realistic, flexible, and far-reaching body of statistical techniques."

- when you have big data that doesn't match simplifying assumptions, machine learning yields demonstrably better results

"Without a testable theory that explains your edge, the odds are that you do not have an edge at all. A historical simulation of an investment strategy’s performance (backtest) is not a theory; it is a (likely unrealistic) simulation of a past that never happened (you did not deploy that strategy years ago; that is why you are backtesting it!)."

"Contrary to popular belief, backtesting is not a research tool."

"ML plays the key role of decoupling the search for variables from the search for specification."


Imagine if physicists had to produce theories in a universe where the fundamental laws of nature are in a constant flux; where publications have an impact on the very phenomenon under study; where experimen- tation is virtually impossible; where data are costly, the signal is dim, and the system under study is incredibly complex . . . I feel utmost admiration for how much financial academics have achieved in the face of paramount adversity.

# chapter 2 benefits of denoising and detoning

- suppose you estimate a covariance matrix for set of assets from eg 2010-2018
- construct a minimum variance portfolio and hold that portfolio for 2019
- if you construct your portfolio on a denoised and detoned covariance matrix, you may expect this to work better empirically out of sample, i.e. be lower variance
- denoising it's a little like the IMDB Bayesian ranking. If a movie has few reviews and a very high rating, it's likely going to revert to the mean. Based on a model of the how the noise impacts the rating, you can adjust for the noise.
- detoning seems like taking out the main factor like the market factor, not sure you want to do this for some purposes

# chapter 3 distance metrics

- suppose you want to group stocks by similarity. correlation is not necesarily an ideal metric
  - suppose you have 2 factors and 3 stocks
  - stock 1 is 50% factor 1, 0 factor 2
  - stock 2 is 50% factor 2, 0 factor 1
  - stock 3 50/50 factor 1 and 2
  - stocks 1 and 2 are completely uncorrelated, even though they might be up to 50% correlated with stock 3.
  - this is a bad property for a similarity metric when you want to do clustering.

- 1 approach is modified correlation to create a distance metric: 0 if 100% correlated, 1 if negatively correlated, 0.707 if 0 correlation
  $$
  \sqrt{\frac{1}{2}(1-\rho_{i,j}})
  $$
  

- another approach is an information theory - based mutual information approach.

# chapter 4 clustering

- given a distance or similarity metric, we want to group objects into sets that minimize within-group similarity while maximizing between-group similari
- Partition-based methods like k-means say, given k, how can I divide into k groups in top-down manner
- Agglomerative methods cluster in a bottom-up manner , eg start with each object in its own cluster, iteratively pair up an object with its most similar neighbor or cluster to reduce number of clusters
- k-means has some issues, need to specify k number of clusters,  if you place initial centroids randomly it's not deterministic. ONC (optimal number of clusters) algorithm uses silhouette metric to pick optimal number of clusters, uses initialization that maximizes the metric.

# chapter 5 labeling

- fixed horizon, eg, daily, hourly, monthly return

  - need to deal with seasonality, known time patterns
  - Unless you always trade on the close, doesn't line up with trading
  - 

- triple barrier, corresponding to initiating a trade with stop-loss level and a profit-taking level

- Trend-scanning method: assign each observation to a trend based on continuation and reversal rules

- Meta-labeling, use a separate model for labeling and eg sizing or risk

  

# chapter 6 feature importance

- MDA
- MDI
- Cluster importance

# chapter 7 portfolio construction

- NCO portfolio construction

# chapter 8 Test Set overfittingg

- deflated Sharpe ratio accounting for multiple trials, selection bias under multiple testing

  