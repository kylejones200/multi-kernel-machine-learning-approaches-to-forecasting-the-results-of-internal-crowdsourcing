# Multi-kernel machine learning approaches to forecasting the results of internal crowdsourcing... ExxonMobil uses online crowdsourcing competitions as a method of
generating ideas for new project development. Through time-boxed...

### Multi-kernel machine learning approaches to forecasting the results of internal crowdsourcing competitions at ExxonMobil
ExxonMobil uses online crowdsourcing competitions as a method of
generating ideas for new project development. Through time-boxed,
specific crowdsourcing competitions, the company leverages the
principles of open innovation to augment traditional research and
development programs.


<figcaption>Photo by Werner Du plessis on Unsplash</figcaption>


Between 2015 and 2017, ExxonMobil hosted more than 20 internal
crowdsourcing idea competitions, which generated a pool of more than
5,000 ideas cumulatively. The sponsor of each competition provided the
question statement, objectives and criteria for determining the "best"
ideas. The selected ideas entered the innovation pipeline for more
rigorous R&D evaluation. The average idea contest generated between
300-700 ideas and the sponsors typically reviewed the corpus of ideas in
the six months following the competition.

The relatively long post-competition evaluation period made many
competition participants feel as if their suggestions were not being
used, negatively affecting employee morale. The authors' posited that a
decision support system could be developed to reduce the time required
to sort through idea submissions will still leveraging the benefits of
non-traditional ideation through crowdsourcing.

The literature about open innovation, new product development and
crowdsourcing document an increasing number of companies, including my
own, are Online crowdsourcing as an open innovation paradigm and
cost-saving measure is being applied in a variety of corporations
(Brabham, 2010; Poetz & Schreier, 2012; Zuchowski, Posegga, Schlagwein,
& Fischbach, 2016).

While the volume of ideas generated through crowdsourcing is larger than
the volume of ideas from in-person based techniques, such as group
brainstorming, the number of ideas which receive management approval to
become projects is less than in-person techniques. Ideas that have been
revised, edited and enhanced during the ideation process are considered
more innovative (Kohn, Paulus, & Choi, 2011). This suggests that methods
that build upon submitted ideas will lead to higher quality ideas.

Since additional time is being spent on methods that produce fewer
management-approved ideas, the focus on crowdsourcing can lead to an
inefficient allocation of resources. A decision support system for
crowdsourcing competitions allows the engineering manager to identify an
associated between community engagement and sponsor management approval
in order to improve how projects are selected and potentially how
competitions are administered.

Crowdsourcing as a method of open innovation has been applied in
numerous fields including biology, conservation, and new product
development. Much of the literature focuses on external and customer
crowdsourcing to define and refine ideas. Internal idea generation
crowdsourcing competitions are a method of augmenting corporate research
and development for new products (Jones, 2016, 2018).

### 2. RESEARCH
The goal of this research effort was to consider a classification model
to use for evaluating submissions in idea competitions. The solution
model chosen should reduce the burden on the competition sponsor and
only require inputs revealed through the ideation process. The model
should not require knowledge of how a specific submission fits into the
overall R&D portfolio. The model should allow decision-makers to make
informed decisions when choosing specific idea submissions.

The objectives of the research were twofold: identify current applicable
classification models and methods to use in decision analysis, and
develop a model to classify idea submissions to reduce the time and
level of effort required to review and select ideas for further
evaluation. This research and proposed model is intended to provide
decision guidance for the competition sponsor.

The research applied five classification methods to a dataset of
internal crowdsourcing competitions held at ExxonMobil between
2015-2017. The classification mentions applied were:

- Logistic regression (LR): a logistic model determines the log-odds of
  the probability that an outcome is a linear combination of features.
  Logistic regression coefficients are often difficult to interpret
  (Garson, 2014; Hosmer, Lemeshow, & Sturdivant, 2013; Steyerberg,
  Borsboom, van Houwelingen, Eijkemans, & Habbema, 2004).
- Decision Tree Classifier (DT): Decision tree models determine use
  conjunction of features, i.e. branches, to derive the classification
  labels. Unlike logistic regression, decision trees can identify
  non-linear relationships between variables. Decision trees are
  commonly used because they are simple to interpret, another difference
  from logistic regression (Ali, Khan, Ahmad, & Maqsood, n.d.; Dicdican
  & Haimes, 2005; Song & Lu, 2015).
- Random Forest Classifier (RF): Random forest is an ensemble method of
  multiple decision trees. Combining multiple weak classifiers typically
  produces a stronger classifier.
- AdaBoost Classifier (AB): Like Random Forest, an Ada-boost classifier
  combines weak classifier algorithms to form a strong classifier
  (Schapire, 1999).
- Naïve Bayesian Classifier: (Koc, Mazzuchi, & Sarkani, 2012).
- Multilayer Perceptron Classifier (MLP): A multilayer perceptron is a
  method of neural network classification. The advantage of a neural
  network is leveraging "hidden layers" between the features and the
  target variable. While these hidden layers can be powerful
  classifiers, they also create a "black box" model in which the
  relative weights of the input features cannot be easily
  determined .

#### Training and Testing of the Models
For training the models this study uses three variables revealed during
the crowdsourcing event: Number of Comments, Number of Votes and Average
Crowd Score. Additional variables were tested and determined to be not
statistically significant (Jones, 2018).

75% of the values are used for training the models and remaining 25% of
values are used for testing to allow for generalization.

Before training the models the values are normalized by subtracting the
mean of the dataset from each value and then dividing it by
corresponding standard deviation, i.e. preprocessing the data with a
standard scalar.

Determining the accuracy of the models\
K-fold cross-validation subsets the test data into "folds" and tests the
models using nine folds and tests the model against the tenth holdout
sample. This simulates the randomness expected in multiple instances of
running the same experiment (Arlot, Celisse, & others, 2010; Kohavi,
1995; Picard & Cook, 1984).

Using k-fold cross-validation (k=10), the model parameters are tuned
using a grid search to optimize precision. Unlike most bioinformatics
applications, In this instance, the consequence of including some false
positives is less than excluding some true positive.\
These optimized parameters are used to train and test the final models.
The models are compared using several evaluation metrics.

As classification models, there is not a single method like R2 to
determine the goodness of fit for a model. These methods draw from the
confusion matrix produced by each model (Fawcett, 2005; Powers, 2011).

- Precision: Precision is the measure of the quality of a model. How
  useful the results are. Out of the number of things classified as
  correct, how many are actually correct? The number of true positives
  out of those things identifies as positive.
- Recall: Recall, also called sensitivity, measures how complete are
  the results. Out of all the correct answers, how many were returned?
  Optimizing for recall minimizes false negatives (Davis & Goadrich,
  2006). \
  F1-score: F1 score finds the harmonic mean between precision and
  recall. This assumes equal weight to precision and recall, which may
  not be the case (Powers, 2011).
- Selectivity. The number of true negatives. Out of those things
  identified as Not part of the class, how many were not part of the
  class?\
  Accuracy: The number of correctly classified instances divided by the
  total number of instances. Values range between 0 and 1. Higher values
  indicated greater accuracy and a perfect classification system would
  have a score of 1.
- Cohen's Kappa: Kappa is a measure of inter-rater agreement. Unlike
  accuracy, it takes in to account the possibility of the agreement due
  to random change. Values range between -1 and 1 (Cohen, 1968; McHugh,
  2012; Tang, Hu, Zhang, Wu, & He, 2015).
- Matthew's Correlation Coefficient (MCC): Matthew's correlation
  coefficient is used to compare between models. Unlike Received
  Operating Characteristics, MCC can be used when the classes are not
  evenly distributed. Values range between -1 and 1 with 1 representing
  a perfect classifier (Chicco, 2017).
- Receiver Operating Characteristics Area Under the Curve: the receiver
  operating characteristics plot measures the relationship between
  sensitivity (false positive rate) and specificity (false negative
  rate). The area under the curve provides a metric for comparing
  different models. Values range between 0 and 1, with 1 being a model
  that perfectly classifies each instance. ROC assumes the classes are
  of equal size such that there is a 50% probability that a randomly
  selected instance should be either positive or negative (Bradley & P.,
  1997; DeLong, DeLong, & Clarke-Pearson, 1988; Fawcett, 2005; Hanley &
  McNeil, 1982).

#### 3. DATA COLLECTION
Data from eight crowdsourcing competitions were collected. The data
included idea submissions and comments posted about the submissions.
Individual participation varied between contests. There is no evidence
to suggest non-random variations were heteroskedastic.

3.1. Participants \
A total of 807 employees participated and submitted 2,004 unique ideas.
Participation was voluntary and participants did not receive any
remuneration for participation.

#### 4. RESULTS
Image 1 shows the decision boundary developed for each model. Using the
same subset of successful and unsuccessful ideas, the image shows the
regions of higher confidence demonstrated by the darker colors.

#### 5. DISCUSSION
The goal of this research was to identify a method to improve sorting
and selecting ideas submitted through crowdsourced, open innovation
competitions. Random Forest was chosen for its straight-forward
interpretability and easy application for decision makers.

This is not to say that Random Forest is the only solution model that is
used for classification or for conducting selecting ideas submitted in
an idea competition. Alternative classification models are summarized in
Table I. This paper conducted a brief introduction of five
classification models: Logistic regression, decision tree, random
forest, Adaboost, and multilayer perceptron.

Although five classification models (LR, DT, RF, AB, NB, and MLP) were
briefly compared in this case study, comparisons of model performance
was not a focus of this research. One could use the model to select the
key performance features of ideas submitted in online idea competitions.
The efficacy of these models is limited by variance in how data were
collected during crowdsourcing events.

The authors recognize there are always latent and exogenous factors that
are not included in the model. For example, the relationships of the
idea generator with sponsor selection is not considered in this
research. Decisions makers continue to use classification methods as
decision support systems to augment intuition. Further research should
explore clustering techniques to help identify latent features within
the data.

#### 5.3. Summary
Online, idea submission crowdsourcing competitions at ExxonMobil, a
major oil and gas company, were evaluated using several machine learning
techniques. Crowdsourcing is a method for augmenting traditional
research and development and subject matter expert judgment. An
extension of this research could use expert inputs to contribute to a
multi-attribute decision model.

Previous studies of crowdsourcing have been limited to participant
perspectives. This research uses a data set that includes not only
participant information but the determination of the sponsor
organization. Additional should be conducted on the results to provide
the decision maker with confidence in the results.

This analysis demonstrates that using classification methods provides
the decision maker with the ability to confidently select idea
submissions quickly.

### Related Stories
- [[5 reasons efficiency matters for a big data business
  strategy](https://medium.com/@kylejones_47003/4-reasons-efficiency-matters-for-a-big-data-business-strategy-1cb45aa9dd03)]
- [[4 reasons efficiency matters for a big data business
  strategy](https://medium.com/@kylejones_47003/4-reasons-efficiency-matters-for-a-big-data-business-strategy-1cb45aa9dd03)]
- [[5 goals of a strong data management
  strategy](https://medium.com/@kylejones_47003/5-goals-of-a-strong-data-management-strategy-513fa227d26d)]
::::::::By [Kyle Jones](https://medium.com/@kyle-t-jones) on
[October 9, 2022](https://medium.com/p/b8e1170f37e8).

[Canonical
link](https://medium.com/@kyle-t-jones/multi-kernel-machine-learning-approaches-to-forecasting-the-results-of-internal-crowdsourcing-b8e1170f37e8)

Exported from [Medium](https://medium.com) on November 10, 2025.
