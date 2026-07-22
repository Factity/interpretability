


“The mind, once stretched by a new idea, never returns to its original dimensions.” — Ralph Waldo Emerson

So I had this conversation about ai once, A strange but small encounter I was asked to explain to me simply How ai works ? I was overwhelmed, possibly so that I have spent the last couple of years studying it. There is simply way too much and I could not get myself to a point where I could start. I do selective speak which I often consider one of my traits whether it is positive or negative. I am really not sure I talk with my audience in mind. I simply was so overwhelmed that I simply said well well “AI just works ”. I did not give a good impression for sure with some awkward stares we moved on. Long long time ago I read some of the feyman’s work whenever I encounter the problem of breaking down a subject and doing selective speak. I often found myself going back to his work and try to understand how would he have explained it. Now I am not no feyman nothing but an average joe. I did what I can to breakdown everything I learnt about “How AI works the question of why although what is another behemoth on its own in this chapter we will stick with why”


I started digging curious as I was there are simply way too many fields, way too much stuff condensing it all is simply not possible and the best part about this is the people who are actually building this technology have very little grasp on the field themselves. With the ever increasing size of the models use cases the sheer scale alone should make it almost impossible to study these. Humans as we are with the indefinite amount of grit we started chipping away at these with our chisel.

In the spirit of (link to the lecture https://calteches.library.caltech.edu/51/2/CargoCult.htm ). In feyman words 

“When you study only what results you get, you never build a deeper understanding. When you study why something happens, you can refine your methods, discard dead ends, and make genuine progress.” 


Any rigorous scientific study or a method should have a clear, reproducible basis. Fundamental axiom will be that ML models are no different than classical models, except in size

Certainly, classical models like Newton’s Laws, the Standard Model , or General Relativity feel different than ML models, owing to the fact that these models are determined by physical principles, even though they may still contain parameters that. By “classical”, we mean models created by scientists without using ML techniques. Related terms that are often used are intelligibility and understandability.

 we will consider interpretability and explainability to be the primary axes of interest. In understanding the why of the model. Interpretability concerns the ability to understand, or approximate, the inner workings of a model and how it reaches its output. Explainability concerns the ability to map the model onto existing knowledge in the relevant scientific domain.
The key difference is how we classify it. Are we able to explain the model ? What is happening in the model ? Interpretability is the degree to which a human can understand the cause of a decision.”A method is interpretable if a user can correctly and efficiently predict the method’s results” The more interpretable a machine learning model, the easier it is for someone to understand why certain decisions or predictions were made.A particular model is more interpretable than another model if its decisions are easier to understand than the other model 
. Knowing the ‘why’ can help you learn more about the problem, the data, and the reason why a model might fail. Imagine the following case if any of the terms does not make sense: have a brief of the appendix sections of the box but it should be relatively fine. Imagine a scenario the ai is extremely intelligent and derived a novel proof when we tried to understand the internals of the model we found a particular x (x being the internal element of the model) is responsible for it. Now we know that to solve the proof the model should have developed its own forms of lets say y laws. Here y laws are the explanation and the element which caused it is x. Y is for explainability and x is for interpretability 





### 1. When Explanations Seem Unnecessary

The text begins by acknowledging that not every machine learning model demands explanations. Two scenarios are given:

- **Low-risk environments:** If a mistake has no serious consequences, the need for an explanation is diminished. A movie recommender system is the classic example – a poor recommendation may annoy a user, but it does not endanger lives, finances, or rights.
- **Extensively studied methods:** When a technique has been researched and validated over decades, its behaviour is considered well understood. Optical character recognition (OCR) is cited; we generally do not require an explanation for why a scanned “A” was recognised as an “A”, because the method’s reliability is established through long-term empirical validation.

In such cases, the model is often treated as a tool whose output is sufficient.

---

### 2. The Core Motivation: Incompleteness in Problem Formalization

The central argument, referenced from Doshi-Velez and Kim (2017), is that **the need for interpretability and explainability arises from an incompleteness in problem formalization**. This means that for many real-world tasks, the formal objective function we optimise (e.g., classification accuracy) does not capture everything that matters.

- A single metric like classification accuracy gives us the **“what”** – the prediction.
- But it does not tell us the **“why”** – how the model arrived at that prediction.

When a problem is fully formalised, the metric alone might suffice. However, most real-world tasks are incompletely formalised; there are unspoken constraints, ethical considerations, and contextual factors that the loss function never sees. In these cases, we must open the black box to understand the reasoning, to ensure the model is not exploiting spurious patterns or violating unstated requirements.

---

### 3. Managing Social Interactions

Machine learning models are deployed into social contexts. They affect people, and people interact with them. Interpretability helps **manage social interactions** by:

- Allowing users to understand why a decision was made about them.
- Enabling developers to explain system behaviour to stakeholders, regulators, or the public.
- Providing a basis for contesting or correcting unfair decisions.

A model that only gives a prediction without a reason disrupts the normal human expectation of accountability, making social integration difficult.

---

### 4. Debugging and Auditing

Interpretability is not only for end-users; it is a critical engineering tool. Models can be **debugged and audited when they can be interpreted**. This applies even in “low-risk” settings like movie recommendations during the research and development phase. A data scientist might find that the model is recommending horror movies to children – interpreting why allows a quick fix. After deployment, interpretability helps audit for concept drift, data bugs, or unexpected biases.

---

### 5. Specific Reasons for Requiring Interpretability

The text enumerates five key dimensions where interpretation is essential:

- **Fairness:** Ensuring predictions do not implicitly or explicitly discriminate against underrepresented groups. Without interpretability, detecting and correcting bias is nearly impossible.
- **Privacy:** Verifying that sensitive information in the training data is not being inadvertently memorised and leaked through predictions.
- **Reliability / Robustness:** Confirming that the model does not produce drastically different outputs for minimally perturbed inputs (a phenomenon adversarial examples exploit). Interpretability can reveal whether the model relies on brittle features.
- **Causality:** Ensuring the model picks up only genuine causal relationships, not mere correlations that might fail under distribution shift. A model relying on non-causal features is likely to fail in the real world.
- **Trust:** Humans find it easier to trust a system that can explain its decisions. Trust is built when an explanation aligns with or respectfully challenges a user’s prior knowledge, rather than being an opaque oracle.

---

### 6. The Nature of Human Explanations (and Their Design Implications)

The text draws heavily on findings from cognitive science and philosophy, particularly Lipton (1990), to describe what makes explanations satisfying to humans. These properties should guide the design of machine learning explanations.

#### 6.1 Explanations Are Contrastive

Humans rarely ask “Why prediction *P*?” in isolation. They ask “Why *P* instead of *Q*?”. We think in counterfactual terms: *How would the prediction have changed if input X had been different?*

- **Application-dependence:** Crafting a contrastive explanation requires a meaningful reference point for comparison. That reference point might depend on the specific data point being explained, or on the user receiving the explanation. There is no universal “one size fits all” contrast.

#### 6.2 Explanations Are Short

Even if the world is complex, humans want only **1 to 3 reasons**. A concise explanation that captures the most influential factors is far more effective than an exhaustive list of all contributing variables. This puts pressure on interpretability methods to select the most important features.

#### 6.3 Explanations Focus on the Abnormal

If an input feature has an abnormal value (e.g., a rare category, an unusual spike) and that feature influenced the prediction, it should be included in the explanation. This holds even if other, “normal” features had a quantitatively similar influence – the abnormal one is more informative because it explains why *this specific instance* is different.

#### 6.4 Explanations Are Truthful (Fidelity)

An explanation should truthfully represent the model’s reasoning, a property often called **fidelity**. If we say, “the second balcony increases the house price,” then that effect should generalise to other houses (or at least to similar houses). Explanations must not be just plausible stories that misrepresent what the model actually does.

#### 6.5 Explanations Are Consistent with Prior Beliefs

Good explanations resonate with what the explainee already believes. This is challenging for machine learning because a high-fidelity model might learn patterns that violate domain knowledge (e.g., a negative effect of house size on price for a few outliers, due to complex interactions). While such a pattern might improve predictive performance, it clashes with our prior belief. Possible resolutions include enforcing monotonicity constraints or using inherently interpretable models (like linear models) that guard against such contradictions.

#### 6.6 Explanations Are General and Probable

A good explanation should not be an isolated, ad‑hoc statement. Its supporting cause should hold across many instances. **Generality** can be quantified by *support*: the proportion of all instances to which that explanation applies. A cause with high support is a “probable” explanation, lending it more credibility.

---

### 7. What We Hope to Achieve with Interpretability

Interpretability is not an end in itself; **we justify the means**. It allows us to:

- Validate that the model is solving the problem in a reasonable way.
- Detect when the model relies on **non-causal features** for prediction, which can lead to catastrophic failures under distribution shift.
- Find **wrong encodings or sub‑par feature engineering** that degrade performance or introduce bias.
- In a specific case, understand **why this particular prediction was made**; if the explanation conflicts with domain knowledge, the decision-maker might question the forecast and initiate an investigation, potentially averting a harmful decision.

---

### 8. Taxonomies of Interpretability Methods

The text introduces several orthogonal dimensions for categorising interpretability approaches:

- **Interpretability by design vs. post‑hoc interpretability:**
    - *Interpretability by design* means building a model that is inherently transparent (e.g., linear regression, shallow decision trees, rule lists).
    - *Post‑hoc interpretability* refers to methods applied after a model is trained, to explain its behaviour (e.g., LIME, SHAP, saliency maps).

- **Model‑agnostic vs. model‑specific:**
    - *Model‑agnostic* methods can be applied to any model type, treating it as a black box. An example is permutation feature importance.
    - *Model‑specific* methods exploit the internal structure of a particular class of models (e.g., coefficient inspection in linear models, integrated gradients for neural networks).

- **Local vs. global:**
    - *Local* explanations account for a single prediction (why this instance got this outcome).
    - *Global* explanations describe the entire model behaviour across the whole dataset.

---

### 9. Interpretability by Design

The closing phrase, “Interpretability by design,” serves as a section heading, emphasising a proactive philosophy. Instead of retrofitting explanations onto a complex black‑box model, we can choose an inherently transparent model class from the outset. This approach guarantees fidelity (the explanation is the model) and often satisfies many of the desirable properties of human explanations (contrastive, short, truthful, consistent with prior beliefs) more naturally. The trade‑off, of course, lies in predictive performance, but in many high‑stakes or incompletely formalised problems, that trade‑off is a deliberate, justified choice.


linear regression model, you are using an algorithm that will produce find models that are linear in the input features. Models that are interpretable by design are also called intrinsically or inherently interpretable models,


Linear regression: Fit a linear model by minimizing the sum of squared errors.
Logistic regression: Extend linear regression for classification using a nonlinear transformation.
Linear model extensions: Add penalties, interactions, and nonlinear terms for more flexibility.
Decision trees: Recursively split data to create tree-based models.
Decision rules: Extract if-then rules from data.
RuleFit: Combine tree-based rules with Lasso regression to learn sparse rule-based models.

This is called the Rashomon effect. The problem with this model multiplicity is that it makes it very unclear which model to interpret.

Model-agnostic: We ignore what’s inside the model and only analyze how the model output changes with respect to changes in the feature inputs. For example, permuting a feature and measuring how much the model error increases.
Model-specific: We analyze parts of the model to better understand it. This can be analyzing which types of images a neuron in a neural network responds to the most, or the Gini importance in random forests.


Model-agnostic methods work by the SIPA principle: sample from the data, perform an intervention on the data, get the predictions for the manipulated data, and aggregate the results

Separating the explanations from the machine learning model (= model-agnostic interpretation methods) has some advantages (Ribeiro, Singh, and Guestrin 2016). The biggest strength is flexibility in both the choice of model and the choice of interpretation method. For example, if you’re visualizing feature effects of an XGBoost model with the partial dependence plot (PDP), you can even change the underlying model and still use the same type of interpretation. Or, if you no longer like the PDP, you can use accumulated local effects (ALE) without having to change the underlying XGBoost model. But if you are using a linear regression model and interpret the coefficients, switching to a rule-based classifier will also change the means of interpretation. Some model-agnostic methods even give you flexibility in the feature representation used to create the explanations: For example, you can create explanations based on image patches instead of pixels when explaining image classifier outputs.

Local model-agnostic post hoc methods
Local interpretation methods explain individual predictions. Approaches in this category are quite diverse:

Ceteris paribus plots show how changing a feature changes a prediction.
Individual conditional expectation curves show how changing one feature changes the prediction of multiple data points.
Local surrogate models (LIME) explain a prediction by replacing the complex model with a locally interpretable model.
Scoped rules (anchors) are rules that describe which feature values “anchor” a prediction, meaning that no matter how many of the other features you change, the prediction remains fixed.
Counterfactual explanations explain a prediction by examining which features would need to be changed to achieve a desired prediction.
Shapley values fairly assign the prediction to individual features.
SHAP is a computation method for Shapley values but also suggests global interpretation methods based on combinations of Shapley values across the data.
LIME and Shapley values (and SHAP) are attribution methods that explain a data point’s prediction as the sum of feature effects. Other methods, such as ceteris paribus and ICE, focus on individual features and how sensitive the prediction function is to those features. Methods such as counterfactual explanations and anchors fall somewhere in the middle, relying on a subset of the features to explain a prediction.

Global model-agnostic post-hoc methods
Global methods describe the average behavior of a machine learning model across a dataset. In this book, you will learn about the following model-agnostic global interpretation techniques:

The partial dependence plot is a feature effect method.
Accumulated local effect plots also visualize feature effects, designed also for correlated features.
Feature interaction (H-statistic) quantifies the extent to which the prediction is the result of joint effects of the features.
Functional decomposition is a central idea of interpretability and a technique for decomposing prediction functions into smaller parts.
Permutation feature importance measures the importance of a feature as an increase in loss when the feature is permuted.
Leave one feature out (LOFO) removes a feature and measures the increase in loss after retraining the model without that feature.
Surrogate models replace the original model with a simpler model for interpretation.
Prototypes and criticisms are representative data points of a distribution and can be used to improve interpretability.

Two broad categories within global model-agnostic methods are feature effects and feature importance. Feature effects (PDP, ALE, H-statistic, decomposition) are about showing the relationship between inputs and outputs. Feature importance (PFI, LOFO, SHAP importance, …) is about ranking the features by importance, where importance is defined differently by each of the methods.






Learned Features: What features did the neural network learn?
Saliency Maps: How did each pixel contribute to a particular prediction?
Concepts: Which concepts did the neural network learn?
Adversarial Examples: How can we fool the neural network?
Influential Instances: How influential was a training data point for a given prediction?


Linear regression 

A linear regression model predicts the target as a weighted sum of the feature inputs 

Linear regression models have long been used by statisticians, computer scientists, and other people who tackle quantitative problems.

Linear models can be used to model the dependence of a regression target y on features 
. The learned relationships can be written for a single instance i as follows:

Estimated weights come with confidence intervals. A confidence interval is a range for the weight estimate that covers the “true” weight with a certain confidence. For example, a 95% confidence interval for a weight of 2 could range from 1 to 3. The interpretation of this interval would be: If we repeated the estimation 100 times with newly sampled data, the confidence interval would include the true weight in 95 out of 100 cases, given that the linear regression model is the correct model for the data.

which are linearity, normality, homoscedasticity, independence, fixed features, and absence of multicollinearity.



Linearity
The linear regression model forces the prediction to be a linear combination of features, which is both its greatest strength and its greatest limitation. Linearity leads to interpretable models. Linear effects are easy to quantify and describe. They are additive, so it’s easy to separate the effects. If you suspect feature interactions or a nonlinear association of a feature with the target value, you can add interaction terms or use regression splines.

1. Linearity
Assumption: The relationship between each predictor and the response is linear (or the model is correctly specified, e.g., includes necessary polynomial or interaction terms).
Why it matters: Non‑linearity biases coefficient estimates and predictions.
Diagnostics:
Scatterplots of residuals vs. each predictor (or vs. fitted values). A random scatter around zero suggests linearity; a curved pattern (e.g., U‑shape) indicates non‑linearity.
Partial residual (component+residual) plots for each predictor: plot 
e+β^jXj
e+
β
^
​
j
​
X
j
​
 vs. 
Xj
X
j
​
. A straight line supports linearity.
Added‑variable plots (partial regression plots): show the relationship between the response and a predictor after adjusting for others.


Formal tests:
RESET test (Ramsey): Regress 
Y
Y on 
X
X and squared/cubed fitted values; test if the added terms are significant. Significant result ⇒ misspecification.
Harvey‑Collier test (t‑test on recursive residuals) for linearity against a smooth alternative.
Remedy: Transform predictors (log, square‑root, polynomials) or use generalized additive models (GAMs).



Normality
It’s assumed that the target outcome given the features follows a normal distribution. If this assumption is violated, the estimated confidence intervals of the feature weights are invalid.



2. Normality of Residuals
Assumption: The errors 
εi
ε
i
​
 are normally distributed (required for valid t‑tests, F‑tests, and confidence intervals in small samples; with large samples, CLT helps, but extreme non‑normality still affects efficiency).
Diagnostics:
Q‑Q plot (quantile‑quantile) of residuals vs. theoretical normal quantiles: points should fall roughly along the diagonal.
Histogram / density plot of residuals with a normal curve overlay.
Formal tests:
Shapiro‑Wilk test (most powerful for small to medium samples).
Kolmogorov‑Smirnov test, Anderson‑Darling test.
Jarque‑Bera test (based on skewness and kurtosis).
Be cautious: In large samples, these tests often reject even tiny, practically unimportant deviations.
Remedy: If heavy‑tailed, consider robust standard errors; for severe skew, transform 
Y
Y (e.g., log, Box‑Cox) or use a generalized linear model.








Homoscedasticity (constant variance)
The variance of the error terms is assumed to be constant over the entire feature space. Suppose you want to predict the value of a house given the living area in square meters. You estimate a linear model that assumes that, regardless of the size of the house, the error around the predicted response has the same variance. This assumption is often violated in reality. In the house example, it’s plausible that the variance of error terms around the predicted price is higher for larger houses since with higher prices there is more room for price fluctuations. Suppose the average error (difference between predicted and actual price) in your linear regression model is 50,000 Euros. If you assume homoscedasticity, you assume that the average error of 50,000 is the same for houses that cost 1 million and for houses that cost only 40,000. This is unreasonable because it would mean that we can expect negative house prices.


Independence
It’s assumed that each instance is independent of any other instance.
If you perform repeated measurements, such as multiple blood tests per patient, the data points are not independent. For dependent data, you need special linear regression models, such as mixed effect models or GEEs.
If you use the “normal” linear regression model, you might draw wrong conclusions from the model.


Fixed features
The input features are considered “fixed”. Fixed means that they are treated as “given constants” and not as statistical variables. This implies that they are free of measurement errors. This is a rather unrealistic assumption. Without that assumption, however, you would have to fit very complex measurement error models that account for the measurement errors of your input features. And usually you don’t want to do that.

Absence of multicollinearity
You do not want strongly correlated features because this messes up the estimation of the weights. In a situation where two features are strongly correlated, it becomes problematic to estimate the weights because the feature effects are additive and it becomes indeterminable to which of the correlated features to attribute the effects.
Feature Importance

The importance of a feature in a linear regression model can be measured by the absolute value of its t-statistic. The t-statistic is the estimated weight scaled with its standard error.

 

Let’s examine what this formula tells us: The importance of a feature increases with increasing weight. This makes sense. The more variance the estimated weight has (= the less certain we are about the correct value), the less important the feature is. This also makes sense.






Explain individual predictions with effect plots



Effect plot does it for you 
The weights of the linear regression model can be more meaningfully analyzed when they are multiplied by the actual feature values. The weights depend on the scale of the features and will be different if you have a feature that measures, e.g., a person’s height and you switch from meter to centimeter. The weight will change, but the actual effects in your data will not. It’s also important to know the distribution of your feature in the data because if you have a very low variance, it means that almost all instances have similar contributions from this feature.








Treatment coding


Effect coding






The good news is that there are ways to introduce sparsity (= few features) into linear models.


Lasso is an automatic and convenient way to introduce sparsity into the linear regression model. Lasso stands for “least absolute shrinkage and selection operator” and, when applied in a linear regression model, performs feature selection and regularization of the selected feature weights. Let’s consider the minimization problem that the weights optimize:

 
 
 

Lasso adds a term to this optimization problem.

 
 
 

The term 
, the L1-norm of the feature vector, leads to a penalization of large weights. Since the L1-norm is used, many of the weights receive an estimate of 0, and the others are shrunk. The parameter 
 controls the strength of the regularizing effect and is usually tuned by cross-validation. Especially when 
 is large, many weights become 0. The feature weights can be visualized as a function of the penalty term 
. Each feature weight is represented by a curve in Figure 6.4. With increasing penalty of the weights, fewer and fewer features receive a non-zero weight estimate. These curves are also called regularization paths.




ther methods for sparsity in linear models

A wide spectrum of methods can be used to reduce the number of features in a linear model.

Pre-processing methods:

Manually selected features: You can always use expert knowledge to select or discard some features. The big drawback is that it cannot be automated, and you need to have access to someone who understands the data.
Univariate selection: An example is the correlation coefficient. You only consider features that exceed a certain threshold of correlation between the feature and the target. The disadvantage is that it only considers the features individually. Some features might not show a correlation until the linear model has accounted for some other features. Those ones you will miss with univariate selection methods.
Step-wise methods:

Forward selection: Fit the linear model with one feature. Do this with each feature. Select the model that works best (e.g., highest R-squared). Now again, for the remaining features, fit different versions of your model by adding each feature to your current best model. Select the one that performs best. Continue until some criterion is reached, such as the maximum number of features in the model.
Backward selection: Similar to forward selection. But instead of adding features, start with the model that contains all features and try out which feature you have to remove to get the highest performance increase. Repeat this until some stopping criterion is reached.
I recommend using Lasso because it can be automated, considers all features simultaneously, and can be controlled via 
. It also works for logistic regression for classification.


Linear regression models can only represent linear relationships, i.e., a weighted sum of the input features. Each nonlinearity or interaction has to be hand-crafted and explicitly given to the model as an input feature.

Linear models are also often not that good regarding predictive performance because the relationships that can be learned are so restricted and usually oversimplify how complex reality is.

The interpretation of a weight can be unintuitive because it depends on all other features




Logistic Regression
Logistic regression models the probabilities for classification problems with two possible outcomes. It’s an extension of the linear regression model for class outcomes.1

Tip





The linear regression model can work well for regression, but fails for classification. Why is that? In the case of two classes, you could label one of the classes with 0 and the other with 1 and use linear regression. Technically, it works, and most linear model programs will spit out weights for you. But there are a few problems with this approach: A linear model does not output probabilities, but it treats the classes as numbers (0 and 1) and fits the best hyperplane (for a single feature, it’s a line) that minimizes the distances between the points and the hyperplane. So it simply interpolates between the points, and you cannot interpret it as probabilities.

A linear model also extrapolates and gives you values below zero and above one. This is a good sign that there might be a smarter approach to classification.



These are the interpretations for the logistic regression model with different feature types:

Numerical feature: If you increase the value of 
 by one unit, the estimated odds change by a factor of 
.
Binary categorical feature: One of the two values of the feature is the reference category (in some languages, the one encoded in 0). Changing 
 from the reference category to the other category changes the estimated odds by a factor of 
.
Categorical feature with more than two categories: One solution to deal with multiple categories is one-hot-encoding, meaning that each category has its own column. You only need L-1 columns for a categorical feature with L categories, otherwise it is over-parameterized. The L-th category is then the reference category. You can use any other encoding that can be used in linear regression. The interpretation for each category then is equivalent to the interpretation of binary features.
Intercept 
: When all numerical features are zero and the categorical features are at the reference category, the estimated odds are 
. The interpretation of the intercept weight is usually not relevant.



GLM, GAM and more 

all those assumptions are often violated in reality: The outcome given the features might have a non-Gaussian distribution,

The features might interact, and the relationship between the features and the outcome might be nonlinear. The good news is that the statistics community has developed a variety of modifications that transform the linear regression model from a simple blade into a Swiss knife.

Y = dist(x)
lso, if I would predict probabilities with a linear model, I can get probabilities that are negative or greater than 1.


Problem: The target outcome y given the features does not follow a Gaussian distribution.

Problem: The features interact.


Problem: The true relationship between the features and y is not linear.


The input features follow a gaussian distribution. he linear regression model can be extended to model all these types of outcomes. This extension is called Generalized Linear Models or GLMs for short.

The core concept of any GLM is: Keep the weighted sum of the features, but allow non-Gaussian outcome distributions and connect the expected mean of this distribution and the weighted sum through a nonlinear function.

GLMs consist of three components: The link function 
, the weighted sum 
 (sometimes called linear predictor) and a probability distribution from the exponential family that defines EY

Generalized Linear Models or GLMs for short. Throughout this chapter, I’ll use the name GLM for both the general framework and for particular models from that framework. The core concept of any GLM is: Keep the weighted sum of the features, but allow non-Gaussian outcome distributions and connect the expected mean of this distribution and the weighted sum through a nonlinear function.


Let’s consider the classic linear model as a special case of a GLM. The link function for the Gaussian distribution in the classic linear model is simply the identity function. The Gaussian distribution is parameterized by the mean and the variance parameters.


account knowledge about the distribution of your target, but also theoretical considerations and how well the model fits your actual data. For some distributions, the canonical link function can lead to values that are invalid for that distribution. In the case of the exponential distribution, the canonical link function is the negative inverse, which can lead to negative predictions that are outside the domain of the exponential distribution.

Interpreting the coefficients 

Generalized additive models 

The world is rarely linear  and the standard linear models assumption of a constant unit effect is often too rigid we replace the linear sum with smooth functions 

→ Linearity is too restrictive 

Feature → 1 unit changes the outcome by fixed amount differing amounts of values across ranges is non reflective in the final output 

Feature transformation 
Categorization 
Generalized additive models 


Moving onto the different model 

We will be looking at decision trees in this section they work on the principle of cut off 


—> so pass a data point 

You make a hierarchy of features and then split to that it reaches to the section where it belongs 


There are various algorithms that can grow a tree. They differ in the possible structure of the tree (e.g., number of splits per node), the criteria for how to find the splits, when to stop splitting, and how to estimate the simple models within the leaf nodes.


Interpreting the decision trees

Root node 

Follow the binary splits “feature x <+ threshold ”
and the path is a chain of conditions joined by ‘AND’. Once you land in a leaf node, the prediction is simply the mean (for regression) or the most frequent class (for classification) of the training instances in that leaf.

Feature importance in a single tree 
How much is the contribution in reducing the impurity 

Each split impurity reduction 
Each feature separately 
Scale the sum    gives the relative importance of the feature 

Natural capture of interactions: the tree structure itself models complex interactions.

Clear grouping: data ends up in distinct, understandable subsets rather than a multidimensional hyperplane.

Visualisation: the tree’s nodes and edges provide a direct, appealing picture.

Good explanations:

Automatically invite counterfactual reasoning: “If feature X had been above the threshold, the prediction would be y₂ instead of y₁.”

Explanations are contrastive (you can compare with sibling leaves).

For shallow trees, the explanation is selective (requires only a few features) and simple (binary decisions).

No feature transformation needed: monotonic transformations (like taking a log) do not affect the tree’s structure.

Scale invariance: the tree is unaffected by scaling (e.g., converting kg to g only changes the split thresholds, not the tree’s shape).



Decision rules 


For decision rules they are most interpretable when 
The features are understandable 
The condition is short 
The number of rules overall is small

Combining multiple rules 

Overlapping rules →  Several rules may apply to the same instance and give contradictory predictions.

No rule applies: an instance may not satisfy any rule’s condition.



We also look for rule lists 

a) Decision list (ordered rules)
The rules are arranged in a priority order.

For a new instance, go down the list and apply the first rule whose condition is true.

This naturally resolves overlaps: only the highest‑priority matching rule fires.

No conflict resolution is needed, but order matters a lot.





These are the rule sets

OneR: learns rules using only a single feature – extremely simple, used as a baseline.

Sequential covering: iteratively learns one rule, removes the data points it covers, and repeats. This is a common strategy for many rule learners.

Bayesian Rule Lists: pre‑mine frequent patterns (itemsets) from the data and then build an ordered decision list using Bayesian statistics.












Cite all the authors names at the end of the book 

One of the key values of interpretability tools is they aid in human oversight by enabling open ended evaluations. When treating the models as black boxes it becomes increasingly difficult to attribute different aspects of biases, deception and overfitting that the model experiences. In an era where agentic systems will be doing most of the tasks the surface area grows exponentially for deceptive behaviour to emerge as agents get more smarter so does there ability to display increased level of threat. 

Little development history of interpretability

 Distill in 2017,
2022 surge in interpretability tools 
STARTING OF ARC
Redwood research and its remix programme
5199 papers on interpretability 

It is important to have theoretical frameworks as works as well as actionable tools that help to deploy these research solutions into business environments 


Introduction to interpretability 

Any method of evaluating a model is only a proxy for its actual performance. The most common way most of these ai systems are being tested is by using the evaluation frame works which is very important by they make us incentivize and move us in the direction of creating correlations and hypothesis that are deceptive, biased and have potential to reach conclusion which are subpar. 

When should we use interpretability ?

The right tool in the wrong hands can be nothing but dead weight. Especially when it comes to the case of interpretability it is important to be particularly careful about this. If you look at interpretability from an end use perspective the amount of resources spent to the change that you witness can be further deceiving and push you more towards being more skeptical about interpretability. Yet so it is most forms of science it important to be much more critical about ideas but also we should not be dismissive of ideas. In the far future when we are close something of a super intelligence it is absolutely important to grasp every aspect of its memory trace even a tiny hint of bias, values that are antithesis to human moral can be detrimental and can compound in every iteration of model generations so diverting resources which is our most probable bet of probing inside the minds of ai should not be ignored. 


If you look at interpretability from an engineers lens it would a slight be impractical atleast for now but given enough time and iterations of models I believe it is worth spending time  and resources on.

Interpretability refers to the line of methods that attempts to interpret or simply reverse  engineer the underlying architectural patterns, activations connections in a human understandable mechanisms is called interpretability. These techniques can help us probe change and mitigate risks due to these internals. Although there are several techniques for supervised models which we will cover in (write the section number and link) we are exclusively focused on generative models here for now. Here i tried to put together all the diverse techniques, explanations for ml techniques and future research directions for references as this work is open draft I am looking to add more content along the way. 

We cover various topics like feature study, circuit study, university of them, work each category of the actionable task workflows. I intend to also include techniques for engineers like knowledge editing lm steering etc. 



Point to the appendix sections with the following 


Different promising and used architectures of the various models and stuff about them like attention mechanism, weights, etc etc 

Hard code a small model using karpathys gpt2 or similar from scratch for programming people 

Point to resources from 3 b1b about transformers 

Make animations about the architecture // 
 



Mechanistic interpretability if a field of interpretability which primarily focuses on reverse engineering the model internals. 

Features 
A feature is a human interperetable input property 

Feature dog -> animal, pet four legs, loyal etc and other features learned during the pretraining embedding these features into the lm 

Circuits 

features helps us understand what information is being encoded in models activations. It does not helps us understand how these are extracted from the inputs. Circuits helps us understand these by connecting features with specific lm behaviours. 

Features -> nodes and weighted connections between them as edges as circuits 

Where interpreting individual transformers components becomes part of circuit interpretation. 



Circuit definition both normal and format and animations would be added here 

Universality 
The concept of universality is central to the mechanistic interpretability when we are comparing across different language models if a particular set of features or circuits form an internal structure and if these structures are transferable to different models then implications are huge. We can painstakingly probe a neural architecture which is small and transfer it to much larger models where studying these can be challenging. If there are no guarantee of universality it becomes very hard to study the effects even when the task at hand is changed, dealing with an inter connected task or even same architectural model with a different training run. 



Feature study can be done via two different methods 

What information is encoded in the model internals 

Look for something
→ make a hypothesis 
→ very a hypothesis 
Open ended feature discovery  
→ observe 
→ explain 


Moving onto the circuit study 

→ trace the flow of information through the ,model components 

How do we compute a specific behaviour ? 

Flow of information through the model components 

→ starting with a behavior 
Step 1 choose a behaviour 
Step 2 define the computational graph 
Step 3 localization 
Step 4 Explaining the circuit analysis 

→ starting with an component 
Step 1 choose a component 
Step 2 explain circuit analysis 
Step 3 identify patterns 
Step 4 study the emergent behaviour 

Universality study 

Are the features and behaviours transferable 

Step 1 define the scope of the study 
→ Universality of features
→ universality of circuits
Step 2 Dimensions of variations 
→ across different lm 
→ across different tasks 
Step 3 Feature or circuit study 

Different interpretability techniques that does not require looking inside the black box models include lime, shap, integrated gradients, 

These can help you identify relations between the input and the outputs like which pixel can help you get the results that you are looking for they do not provide insight into what might have caused it 


Other probing techniques in mechanistic interpretability that also probes the internals 

Probing classifiers and attention weight analysis 

Mechanistic interpretability can be classified into two different approaches 

Top down and bottom up approaches 


Bottom up approach 
Breaking down all the model elements into small components and gradually piece them together to produce complex model behaviour 

Top down approach 

Top down approach looks and identifies units of layers or modules and move down from it trying to piece together how the smaller components works 


→ github committed 

—----------------------------------------------------------------------------------------------------------------------------


Locating important neurons or understanding attention patterns 

The following survey adopts broadest technical definition 

Mechanistic interpretability is any work that seeks to describe the internals of a model 
studies that probe for linguistic features in activations, analyse attention patterns, or reconstruct computational circuits all count as MI


Projection methods 

Vocabulary projection methods try to decode the inside of a language model representations by projecting these directly onto the models internal representations. If the model had to guess the next token based only on this intermediate representation what would it say ?

Normally during the language model inference only the final layers output take at i th token position in the last layer is multiplied by the unembedding matrix WU. this multiplication produces the scores that determine the probability distribution over the vocabulary. All the earlier layer outputs are not used for the final step. 

The vocabulary projection methods takes a hidden layer hil at layer l and multiply with wu 

This technique is tied to iterative inference perspective each transformer is not just retrieving abstract features but progressively refining the latent predictions of the next layer 

L contains some information it is sub sequently refined over the next few layers . 



Logit lens 
The first technique to employ this idea was the logit lens introduced and applied to gpt 2 

logitlens(hli) = LayerNorm(hli)WU

The resulting vector logits can be turned into probability distributions using softmax functions extending the logit lens to sub layer outputs 

Composition of the transformer => two main sub layers multi head attention and a feed forward network 



Generate animations related to the transformer methods animations about how transformers work 

Vocabulary projection methods 


Text (INPUT)- > 

| -> word1   word2 word3 ………

         E1        E2        E3…………

ATTENTION BETWEEN E1 ……………
\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
ATTENTION BETWEEN BLOCKS 


       MLP (WITH BACK PROP 
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||



REPEAT 

UNEMBEDDING -> OUTPUTS -> 








Intervention based methods 


DECODE FEATURES FROM ACTIVATIONS BY PROJECTING THEM INTO THE VOCABULARY SPACE WHICH IS TYPICALLY SPACE, WHICH IS TYPICALLY ACHIEVED BY MULTIPLYING UNEMBEEDING MATRIX YIELDING LOGIT DISTRIBUTIONS OVER VOCABULARY.

Infer encoded features by inspecting top/bottom tokens in the projected logit distribution (e.g., a majority of top-k tokens relate to “breakfast” implies a “breakfast” feature).

1) Reliability: improve faithfulness of projections, (2) Decoding positions: enable decoding from activations, weights, and gradients, and (3) Expressivity: decode features beyond next-token predictions.


Intervention-based  Methods

Investigate LM behavior causally by intervening on intermediate activations during the forward pass and comparing outputs before and after the intervention to infer their role. There are two types: noising-based and denoising-based interventions.

Evaluate intervention effects by measuring changes in target token logit, target token probabilities, or the full logit distribution before and after intervention. If an activation is critical,
intervening in its value should yield substantial performance changes.

(1) Reliability of corruption: improve reliability by ensuring interventions do not take the model out of distribution, (2) Intervention for localization: adapting intervention to discover all behavior-related components, (3) Scaling up and automation: automate the localization technique to alleviate human effort, (4) Intervention for validating hypotheses, and (5) Integrate with vocabulary projection for richer activation decoding.


Sparse autoencoders methods 

Map activations to a more interpretable but higher-dimensional sparse activations by training SAEs; one can then conduct feature studies in the sparse activations instead of original LM activations.

Fidelity of the sparse activations is measured by the reconstruction loss and the interpretability of SAE features is evaluated manually by looking at the activation pattern of the feature or by automated interpretability score.

(1) Balancing reconstruction fidelity with sparsity for interpretability, and (2) Discovering features that are functionally useful for downstream LM tasks.

Probing 

Test whether predefined features are present in LM activations by training a shallow classifier (i.e., probe) on them.

High probe accuracy on a held-out test set indicates feature presence on activations.

(Not a focus in this survey; we refer readers to (Belinkov, 2022) for more details.)

Visualization 


Prepare visualization (e.g., attention maps, neuron activation plots) to investigate model behavior.

Human examines visual information to form or refine hypotheses about the roles of components and activations.






TECHNIQUES NOTE FOR INTERPRETATION 

it is important to note that the explanation generated by vocabulary projection methods is only
correlational rather than causal in nature

(1) Reliability: improving the faithfulness of the technique’s output and enabling more reliable vocabulary projection (2) Decoding position: adapting and applying the technique to decode features from various intermediate representations and model weights; and (3) Decoding expressivity: enhancing the degree to which the technique decodes features beyond immediate next-token predictions. We highlight representative approaches discussed in the technical advancements in Table 3


.logit lens may produce unreliable projection for certain LMs (e.g., BLOOM, OPT 125M), particularly in the earlier layers. For example, the top-1 projected token for BLOOM (Scao et al., 2022) in more than half of the earlier layers is often the input token, rather than a plausible continuation towards the final output token. The authors posit that the logit lens makes an oversimplified assumption that all layers operate in the same embedding space, which may not be true. Consequently, WU , which is only pre-trained to project an LM’s final-layer activation, cannot reliably project all the intermediate activations to the vocabulary space. This observation inspired Belrose et al. (2023, i.e., tuned lens) and Din et al. (2023) to train translators that transform the intermediate activations to an output representation that better aligns with the representation space of the final layer before the logit lens is applied. Specifically, both approaches linearly transformed the intermediate activation (e.g., h l i ) to an activation that matches more closely with the basis of the final layer activation (h L i ). However, Din et al. (2023) achieved it by directly minimizing the difference between the transformed activation and the final-layer activation, while Belrose et al. (2023) designed the loss function to encourage the matching between the logit distributions of the transformed activation and the final-layer activation




Spooky phenomenon in higher dimensions 

Understanding and modeling the transformer. Once the models scale to a certain level their open endedness and high capacity creates and increasing scope and unexpected and sometimes harmful behaviour. 

Mechanistic interpretability attempting to reverse engineer complicated binaries in human readable format., simple algorithmic motifs and patterns that can subsequently be applied to large and more complex models.

There have been lot of work for vision models but for language models it is yet to be developed 

As the deeper we go inside a network the neurons try to develop more nuanced concepts by combining the features from the previous layers 















Write a brief notes about the topic at hand : 

The author talks of zooming in in a sense microscopic world of phenomenon and moves onto studying the neural networks and the internals of the neural networks. Instead of looking at it as a unified phenomenon lets study careful all the neurons present, all the weights present and understand the circuits of connections // finding circuits implementation logic cases where the network implementation simple logic: cases were the network implementation and, o, xor over high level visual features. 



Different speculative claims 

The author moves to biology trying to understand parallels between cells and organs i presume 
He presents SCHWANN claims about cells 

Claim 1 \

The cell is the unit of structure, physiology and organization in living things 

Claim 2 \

The cell retains a dual existence as a distinct entity and a building block in the construction of organisms 

Claim 3 \
Cells formed by free cell formation , similar to the formation of crystals 

THree speculative claims about neural networks 

Claim features \

Features are the fundamental units of neural networks 

Claim 2 Circuits \

Features are connected by weights forming circuits 

Claim 3 universality \

Analogous features and circus form across models and tasks 



Arguments for generalization tool kit 
Argument 1 -> feature visualization 

→ optimising the input to cause curve detectors to fire reliably produces curves. 

→ Argument 2 -> data set examples 
Perfect curves make it glow 

→ Argument 3 -> Synthetic examples 
Depends on the curvature 

→ Argument 4 -> joint tuning 
Two or more neurons working tandem 

→ Argument 5 -> feature implementation 

Circuit based arguments Understanding how the features are implemented to circuits 

→ Arguments 6 -> feature use 

The down stream clients of curves 

→ Argument 7 -> hand written circuits  



Curve detectors fire for a different kinds of stimulus. although there might be some interference the in the curve detectors due to external stimulus. 

Curves causes the neurons to fire 
Curves respond to different angular orientation 
Weakness of the external stimulus 

intuitive type of feature   |||    oriented edges, corners, junctions



Now that we have looked at curve detectors lets lok at the high low frequency detectors 

High low frequency detectors are less intuitive type of features 


early layers of convolutional vision networks,   one characterizes their selectivity, their behaviour becomes quite simple.   A high‑low frequency detector looks for a spatial frequency contrast: low-frequency patterns on one side of its receptive field and high-frequency patterns on the other side. a smooth, slowly varying luminance gradient abuts a region of fine texture or rapid intensity changes

Rigorous definition 

detector’s receptive field as a two‑dimensional spatial weighting function   



They look for low-frequency patterns on one side of their receptive field, and high-frequency patterns on the other side. Like curve detectors, high-low frequency detectors are found in families of features that look for the same thing in different orientations.Why are high-low frequency detectors useful to the network? They seem to be one of several heuristics for detecting the boundaries of objects, especially when the background is out of focus. In a later article, we’ll explore how they’re used in the construction of sophisticated boundary detectors.

Feature visualization by optimization
Instead of optimizing for curves, one maximizes the neuron’s activation under a parametric stimulus model that allows independent control of the spatial frequency content on each side of a boundary. The result is a synthetic image that cleanly exhibits low‑frequency smooth gradients on one side and high‑frequency noise or fine gratings on the other.

Dataset examples and counterexamples
Searching large natural image corpora for the highest‑activating patches reveals photographs in which a blurred background (low frequency) meets a sharply focused, textured foreground (high frequency), or conversely a textured surface next to a smooth, defocused region. Counterexamples—patches that contain high contrast across the boundary but without a frequency change—elicit low activation, ruling out simple edge or brightness‑contrast explanations.

Synthetic rendering with a physically based blur model
Because defocus blur is naturally modelled as a low‑pass filter that attenuates higher spatial frequencies in a depth‑dependent manner, one can render artificial scenes with a given depth‑of‑field. By varying the blur radius on opposite sides of a depth edge, one generates stimuli where the luminance profile is similar but the spatial frequency content differs—exactly the condition the detector prefers. The detector’s response tracks the blur difference, not the sharpness of the edge itself.

Ablation of spatial frequency components
Starting from a natural activating image, one can apply band‑pass or band‑stop filters independently to each half of the receptive field. Removing high frequencies from the high‑frequency side collapses the response; adding high‑frequency texture to the low‑frequency side does the same, confirming the role of frequency contrast.

Selective knockout via hidden‑unit clamping
In the spirit of causal tracing, one can freeze the neuron’s value to its mean and observe the impact on downstream boundary‑detection performance. When natural images contain frequency‑contrast boundaries, the knock‑out degrades the network’s ability to localize object edges, especially in regions with out‑of‑focus backgrounds. This ties the neuron’s computed feature to a functional role.

Adversarial perturbations that target frequency contrast
Minimally perturbing an image to suppress the neuron often leaves the sharpness of the luminance edge intact but equalizes the spatial frequency content on both sides—e.g., by adding fine texture to the blurred side or by smoothing the textured side. The perturbation is imperceptibly small in pixel space yet destroys the frequency dichotomy.

Rotation and reflection equivariance
The network naturally develops a whole family of such detectors at many orientations. Rotating an activating image by 
30
∘
30 
∘
  shifts the highest response to the neuron tuned for that orientation. This regular structure is a strong signature of a genuine feature that the network treats as a fundamental primitive.
heuristic for boundary detection under defocus and depth variation


Increasing the complexity and moving into the further layers complexity emerges into the models with higher level features being displayed 

Pose-Invariant Dog Head Detector

pose-invariant dog detector. As with any neuron, we can create a feature visualization and collect dataset examples. If you look at the feature visualization, the geometry is… not possible, but very informative about what it’s looking for and the dataset examples validate it.
Feature visualization establishes a causal link, while dataset examples test the neuron’s use in practice and whether there are a second type of stimuli that it reacts to. 


Polysemantic neurons 

overly rosy picture: perhaps every neuron yields a nice, human-understandable concept if one seriously investigates it?

The ability of a neuron to respond to multiple different kinds of stimulus like cat faces, fronts of cars and cat legs etc study such features, characterizing each different case they fire, and reason about their circuits to some extent.


A graph network of weights and features form a circuit. 

linear combinations of neurons in the previous layer, followed by ReLU.

Circuit 1: Curve Detectors
family of units that detect curves at different angular orientations.
curve detectors are assembled from earlier, less sophisticated curve detectors and from line detectors. In the next layer, these curve detectors participate in the formation of 3D geometry detectors and complex shape detectors.early curve detector (a simpler unit) and a full curve detector (a more tuned unit) that share the same angular preference.

how the weights rotate with the orientation of the curve detector. The symmetry of the problem is reflected as a symmetry in the weights. We call circuits with exhibiting this phenomenon an “equivariant circuit”,


Oriented dog head detection 

a collection of neurons that handle dog heads facing to the left and dog heads facing to the right. Over three layers, the network maintains two mirrored pathways, detecting analogous units facing to the left and to the right. At each step, these pathways try to inhibit each other, sharpening the contrast. Finally, it creates invariant neurons which respond to both pathways.this pattern “unioning over cases”. The network separately detects two cases (left and right) and then takes a union over them to create invariant “multifaceted

Circuit 3: Cars in Superposition
In mixed4c, a mid-late layer of InceptionV1, there is a car detecting neuron. Using features from the previous layers, it looks for wheels at the bottom of its convolutional window, and windows at the top.


circuit suggests that polysemantic neurons are, in some sense, deliberate. That is, you could imagine a world where the process of detecting cars and dogs was deeply intertwined in the model for some reason, and as a result polysemantic neurons were difficult to avoid. But what we’re seeing here is that the model had a “pure neuron” and then mixed it up with other features.





circuit motif 

 is a recurring pattern in complex graphs like transcription networks or biological neural networks. Motifs are helpful because understanding one motif can give researchers leverage on all graphs where it occurs.

Claim 3: Universality


The first layer of vision models trained on natural images will learn Gabor filters. Once you accept that there are meaningful features in later layers, would it really be surprising for the same features to also form in layers beyond the first one?


These results have led us to suspect that the universality hypothesis is likely true, but further work will be needed to understand if the apparent universality of some low-level vision features is the exception or the rule.


Interpretability as a Natural Science

One particularly challenging aspect of being in a pre-paradigmatic field is that there isn’t a shared sense of how to evaluate work in interpretability. There are two common proposals for dealing with this, drawing on the standards of adjacent fields. Some researchers, especially those with a deep learning background, want an “interpretability benchmark” which can evaluate how effective an interpretability method is. Other researchers with an HCI background may wish to evaluate interpretability methods through user studies.

Circuits sidestep these challenges by focusing on tiny subgraphs of a neural network for which rigorous empirical investigation is tractable. T


Breaking mechanistic interpretability for large language models 

Taking higher dimensionality break them understood semi independently it cannot all be kept in the limited context of brain. What is principles what is mess upped 

The author puts more weights on attention there are several heads 

How should think about transformers 

→ transformers are weirdly linear computational efficiency it might not be the case that human interpretability computationally efficient 

Models (takes sequences) move information between sequences they are auto regressive input based on previous inputs decoder only we only look forwards 
The model takes in sequence of tokens 

50000 tokens – encoding ///////

Look up table we represent positions we add a position vector for each position 







Newer work from anthropic on interpretability 


within LLMs’ repertoire of vector representations, is there a privileged subset that plays a computational role analogous to the global workspace?


What should the llm scape have that would make it the work space 

Verbal report 

→ the capital of france is paris 
→ the capital of germany is berlin 

France for germany 

Directed modulation 

Who is the most famous roman emperor
→ module → roman empire 
Internal reasoning 

After remapping from embeddings 

The amount of written work about caesar  vector c [...........}
The amount of written work about nero      vector  n [.............]

The amount oi people caesar ruled  vector c_number [.........]
The amount of people nero ruled    vector p_number [...........]

Flexible generalization 

There are x percent of warriors of the total Vector p_number [.......]  under nero command 

Selectivity 

The amount of populus which were unhappy of the total p_number [.......] who were unhappy 

Hmmm is it x% or y% …… Scholars debate 

Source 1 says this || Source 2 says this ||

User: what is the final answer 

……   processing 



Jacobian lens 

Our results make use of a new interpretability technique called the Jacobian lens (J-lens), which is designed to identify internal representations that are readily available for verbal report. For each token in the model’s vocabulary, the Jacobian lens identifies a vector representation that encodes the potential for the model to verbalize that token in the future




 

