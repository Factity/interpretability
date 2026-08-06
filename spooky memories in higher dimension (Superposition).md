---
jotbird_link: https://share.jotbird.com/breezy-mighty-whiptail
jotbird_expires: 2026-08-26
---
# spooky memories in higher dimension (Superposition)


The following section is replication to the [Toy models of superposition](https://transformer-circuits.pub/2022/toy_model/index.html)
Clean interpretation can give us a sense of security. If you have worked with any of the use case where you have to deploy the model in a mission critical scenario you cant help but be frustrated. when things doesn't fall into the human understandable realm. 
The ideal scenario would be individual neuron activations with features. 

There have been several works in quantifying this phenomenon. we have observed that there are several neurons that map cleanly to features. the same could not be said for features it is much rarer and cumbersome. 

There is a particularly useful analogy that neural networks represent features in activation space as directions. when we state things like this we are making a much stronger claim about their representations. There is significant empirical evidence and arguments supporting this. To make this the properties of Decomposability and linearity should hold true. 

If the features correspond to neuron activations identifying them becomes a lot easier but if not i.e, superposition it would be a lot harder to grasp. This push and pull can be decomposed into 2 distinct forces **Privileged basis** (clean neuron activations features align to basis)and **superposition** (trying to simulate a larger network).

Embedding arithmetic was observed and does seem to hold true further cementing the above analogy. If we consider the concept of gender as a  direction in the embedding space then  v(KING) - v(man)+ v(woman} = v(queen ). Interpretable directions have also been found for several different types of architectures. Phenomenon like Universality and polysemanticity have also been observed in language models much of the phenomenon we have observed for the vision models transfer here. 

How do we define a feature if they indeed represent tokens then every new operation does indeed should open up a newer representation. if we say in the above arithmetic terms king -  man we can indeed think of them as operations of individual features. This is the functional representation. we can also think of them as properties which are human understandable but novel things could not be represented this way. One of the analogy is to think about when representing the features is to consider a list of rules like activation in neuron number 1 connected to neuron number 7 in layer 2 etc 
![[Pasted image 20260723172617.png]]        


| rule number | rule code | explanation                                                                     |
| ----------- | --------- | ------------------------------------------------------------------------------- |
| rule 1      | h1        | the neuron activation value for the l11 will be set to (intensity of the color) |
| rule 2      | h2        | the neuron activation value for the l12 will be set to (intensity of the color) |
| rule 3      | h3        | the neuron activation value for the l13 will be set to (intensity of the color) |
| rule 4      | h4        | the neuron activation value for the l14 will be set to (intensity of the color) |
the hope with this approach is that if a sufficiently large neural network will dedicate a neuron for a concept l11 represent being a man etc.

In  linear representation presence of multiple features is represented as $x_{f_{1}}W_{f_{1}} + x_{f_{2}}W_{f_{2}} + x_{f_{3}}W_{f_{3}} \dots$ where the W represent the representation direction and $x_{f}$ represent the activation of our x in that particular direction   

![[Pasted image 20260725153628.png]]

here $x_{f_i}$  can be of any magnitude how happy he was or did he win with a first place etc. 

So why should the model align with these specific directions to represent concepts. If there is an incentive for features to align with these basis dimensions we call it a privileged basis and if not we call it a non privileged basis. (In some sense after training these emerge like king, man, boy, father, uncle, prince etc. it is much easier if gender is a direction ).  

Even with the privileged basis the neurons sometimes are poly semantic.  Activating even for unreal ted features we call this superposition. 

> **Superposition** -when model represent more features than they have dimensions. 

when trying to represent more features than it has neurons polysemanticity emerges. These concepts are mathematically plausible  some of the ways is by having almost orthogonal vectors (exp(n) almost orthogonal vectors) or compressed sensing (recovering from lower dimensions when sparse ). These can interfere but since the sparsity is so high in larger and larger dimensions the cost may outweigh the benefit

![[Pasted image 20260725165107.png]]

![[Pasted image 20260725165346.png]]

Yellower they are the higher the importance of the feature and most important features are projected onto the orthogonal and antipodal pairs 

we pick a total of 5 features with importance and feature probability calculated as

$$

\text{importance}_{i} = (0.9)^{i}, \qquad i = 0, 1, \dots, n_{\text{features}}-1


$$
$$

\text{feature\_probability}_{j} = 20^{-t_j}, \qquad 
t_j = \frac{j}{n_{\text{instances}}-1}, \;\; j = 0, 1, \dots, n_{\text{instances}}-1

$$
and project them onto 2 dimensions with increasing levels of sparsity



A simple but powerful analogy to understand what goes on here is to pick a much smaller less complex model and understand what goes on in them. We have seen in the induction heads section more layers does indeed generalize. 
To visualize what is being done we use a small ReLU Network trained on synthetic data 
with sparse input features to demonstrate superposition. 
#### ReLU Network 

The sparse vectors are generated from a Bernoulli distribution.  

![[Pasted image 20260725064818.png]]

The model is a ReLU encoder with a bottleneck of d< D
$$
h=ReLU(Wx)=ReLU\left( \sum_{i-1}^D ​x_{i}w_{i}​ \right)\in R^d.
$$
Here $w_{i}, w_{2}\dots w_{D}  \in R^d$ are the embedding vectors for each of the feature

![[Pasted image 20260725071532.png]]


when features are sparse, superposition allows compression beyond what a linear model would do, at the cost of interference that requires nonlinear filtering. In the following sparse vector generation process we use a slight variation of the Bernoulli distribution instead of picking values from just $\{ 0,1 \}$ we pick the values from inflated uniform distribution. Here the presence of a feature is determined by the a Bernoulli trail with the probability being the feature probability. 


$$
x_i = 
\begin{cases} 
U_i \sim \mathcal{U}(0,1), & \text{with probability } p_i^{(k)} \\
0, & \text{with probability } 1-p_i^{(k)}
\end{cases}

$$

we observe that superposition emerges only in models with non linearity ReLU and for the linear models there is simply no interference 

$$
\begin{aligned}
&\textbf{Linear Model} \\
&\mathbf{h} = \mathbf{x} \mathbf{W} \qquad (\mathbf{x}\in\mathbb{R}^{1\times d},\; \mathbf{W}\in\mathbb{R}^{d\times h},\; \mathbf{h}\in\mathbb{R}^{1\times h}) \\
&\hat{\mathbf{x}} = \mathbf{h} \mathbf{W}^{\!\top} + \mathbf{b} = \mathbf{x} \mathbf{W} \mathbf{W}^{\!\top} + \mathbf{b}
\end{aligned}
$$

for linear models there is almost no superposition and no interference but as soon as non linearity is introduced took a total of 100 different features with 20 hidden features and 20 instances for the below plot the yellow portion represent superposition. we represented $W^TW$ with the blue dots representing the superposition in the right side plots as we can see with the increasing sparsity the observed superposition increases 

$$

\begin{aligned}
&\textbf{ReLU Output Model} \\
&\mathbf{h} = \mathbf{x} \mathbf{W} \\
&\hat{\mathbf{x}} = \operatorname{ReLU}\!\big(\mathbf{h} \mathbf{W}^{\!\top} + \mathbf{b}\big) = \operatorname{ReLU}\!\big(\mathbf{x} \mathbf{W} \mathbf{W}^{\!\top} + \mathbf{b}\big)
\end{aligned}
$$
we took a total of 



![[newplot.png]]

 the linear model always learns the top-m most important features, analogous to learning the top principal components. The ReLU output model behaves the same on dense features, but as sparsity increases, we see superposition emerge

$$

\begin{aligned}
&\textbf{Loss (both models)} \\
&\mathcal{L} = \sum_{\mathbf{x}} \sum_{i=1}^{d} I_i\,(x_i - \hat{x}_i)^2, \quad I_i \ge 0 \text{ (feature importance)}
\end{aligned}
$$

The learning dynamics is a tug of war between two different phenomenon feature benefit and interference.  The decrease in loss by representing the feature and potential interference for non orthogonal ones affecting each other predictions    

$$
% Equation 1:
L_1 = \sum_i \int_{0 \le x_i \le 1} I_i \left(x_i - \text{ReLU}(\|W_i\|^2 x_i + b_i)\right)^2 + \sum_{i \neq j} \int_{0 \le x_i \le 1} I_j \text{ReLU}(W_j \cdot W_i x_i + b_j)^2

$$


$$

% Equation 2:
L_1 = \sum_i I_i \left(1 - \text{ReLU}(\|W_i\|^2 + b_i)\right)^2 + \sum_{i \neq j} I_j \text{ReLU}(W_j \cdot W_i + b_j)^2


$$
the equations primarily consists of 2 different terms as explained earlier the feature benefit term that penalize the model if it failed to reconstruct a target feature. 
the 2nd term penalize the model if activating feature i accidentally activates another feature j. it measures the overlap

the following 3 things can happen to a feature

1.  feature is learned with a dedicated dimension
2. feature in superposition
3.  feature simply not learned

### phase diagram

One of the better way to understand in which of the categories the features might fall into is by using phase diagram. We have established earlier based on the importance and the sparsity levels features can be any of the presented states. we called each of the above states as dropped, superposed and dedicated as we have represented the phase diagram one of the striking things we have noticed is the abrupt change when training conditions are varied. the boundary between the three looked more sharp than gradual same way water doesn't gradually "soften" into steam but flips abruptly at 100°C.  when observing this phenomenon in large models the effects seems to be much more tangled. To strip away the complexity we looked at four different smaller models a mapping from 3d to 2d and picked 2 features $x_{1}$ and $x_{2}$ as and generated them using the above presented uniform inflated distribution. We also assigned relative importance r to a feature because some features are much more important than the others . we picked anywhere from 0.1 to 10 for r while simultaneously fixing the value for the other feature. we have also varied s(sparsity)from in the range 1 to 0.01.  The loss goes like this 
	$$
	loss = (x₁-y₁)² + (x₂-y₂)² + ... + (x_{n-1}-y_{n-1})² + r·(x_n-y_n)²
	$$
	**r** signifying some are important than the other 

the four models we pick are simple  each of the form $y = \text{ReLU}(W^tWx + b)$, where $\text{ker}(W)$ has dimension 1. To map into lower dimensions we either ignored coordinates or superimposed them 

For generating the above 3 cases we used the following procedure
- **Discard-and-guess.** Zero out a coordinate, but add back its *unconditional mean*
  (`s/2`, since it's `0` with probability `1-s` and averages `0.5` when active) as a
  constant bias. This is the best *constant* guess for a coordinate you've thrown away.
- **Superposition.** Apply the 2×2 matrix
- $$
  P_2=\begin{pmatrix}
1 & -1\\
-1 & 1
\end{pmatrix}
$$
  to a *pair* of coordinates, then ReLU. Geometrically this is a projection orthogonal to
  `(1,1)`. If only one of the two coordinates is active, it comes back out perfectly
  (e.g. `(x, 0) → (x, -x) → ReLU → (x, 0)`). If **both** are active at once, they
  interfere — only the *difference* survives — and that mismatch is the cost of
  superposition.

The four models:

| Name        | What it does                                                    | Bottleneck direction thrown away    |
| ----------- | --------------------------------------------------------------- | ----------------------------------- |
| **f**       | discard the **first** coordinate (weight 1), add back its mean  | 1st coordinate                      |
| **g**       | discard the **last** coordinate (weight `r`), add back its mean | last coordinate                     |
| **h_first** | **superpose** the first two coordinates                         | interference between coords 1 & 2   |
| **h_last**  | **superpose** the last two coordinates (one has weight `r`)     | interference between coords n-1 & n |

`f` and `g` are mirror images of each other, as are `h_first` and `h_last` — the only
difference is *which* coordinate carries the special weight `r`.



For a given sparsity parameter $s$, we will consider four tiny "neural networks." The first two include small bias terms that reflect the expected value of the coordinate being discarded. (Here $e_1$ and $e_n$ are the first and last basis vectors.)

$f_s(x) = \text{ReLU}(D_{first}x  + \frac{\displaystyle s}{\displaystyle 2}e_1)$

$g_s(x) = \text{ReLU}(D_{last}x  + \frac{\displaystyle s}{\displaystyle 2}e_n)$

$h_{first}(x) = \text{ReLU}(S_{first}x)$

$h_{last}(x) = \text{ReLU}(S_{last}x)$

To better understand the relationship between the loss and activity we manually picked particular x values and studied various cases to grasp where the point fall we fixed (s = 0.3, r = 2.0) to be displayed in the phase diagram
### Case A — only the (unweighted) middle coordinate is active: `x = (0, 0.55, 0)`

| model                   | output y          | loss       |
| ----------------------- | ----------------- | ---------- |
| f (discard first)       | `(0.15, 0.55, 0)` | 0.0225     |
| g (discard last)        | `(0, 0.55, 0.15)` | 0.0450     |
| h_first (superpose 1,2) | `(0, 0.55, 0)`    | **0.0000** |
| h_last (superpose 2,3)  | `(0, 0.55, 0)`    | **0.0000** |

Nothing collides here, so both superposition models reconstruct perfectly, while `f`
and `g` still pay a small penalty for guessing at a coordinate that happens to be zero
(they don't know that in advance).

### Case B — only the first coordinate is active: `x = (0.72, 0.10, 0)`

| model                   | output y             | loss       |
| ----------------------- | -------------------- | ---------- |
| f (discard first)       | `(0.15, 0.10, 0)`    | 0.3249     |
| g (discard last)        | `(0.72, 0.10, 0.15)` | 0.0450     |
| h_first (superpose 1,2) | `(0.62, 0, 0)`       | 0.0200     |
| h_last (superpose 2,3)  | `(0.72, 0.10, 0)`    | **0.0000** |

`f` pays heavily here — it threw away exactly the coordinate that was active.
`h_first` collides `x₁` with the (small) `x₂`, but the damage is small since `x₂` is
small. `h_last` is untouched since it only entangles coordinates 2 and 3.

### Case C — only the last (weighted) coordinate is active: `x = (0, 0.10, 0.85)`

| model | output y | loss |
|---|---|---|
| f (discard first) | `(0.15, 0.10, 0.85)` | 0.0225 |
| g (discard last) | `(0, 0.10, 0.15)` | **0.9800** |
| h_first (superpose 1,2) | `(0, 0.10, 0.85)` | **0.0000** |
| h_last (superpose 2,3) | `(0, 0, 0.75)` | 0.0300 |

`g` is disastrous — it discarded the coordinate that matters twice as much, *and* it was
active. This is the key asymmetry that makes `r` matter.

### Case D — both special coordinates active (a "collision"): `x = (0.72, 0.10, 0.85)`

| model                   | output y             | loss   |
| ----------------------- | -------------------- | ------ |
| f (discard first)       | `(0.15, 0.10, 0.85)` | 0.3249 |
| g (discard last)        | `(0.72, 0.10, 0.15)` | 0.9800 |
| h_first (superpose 1,2) | `(0.62, 0, 0.85)`    | 0.0200 |
| h_last (superpose 2,3)  | `(0.72, 0, 0.75)`    | 0.0300 |

Here `h_first` is cheapest: it's better to let the two *unweighted* coordinates
interfere a little than to mishandle the weighted one at all.

The below plot shows the phase digaram and the x represent (s = 0.3, r = 2.0)
![[newplot (1).png]]



log loss surface as the loss due to sparsity and relative weight is captured below

![[newplot (3).png]]


The below diagram shows log loss of the 4 selected models 

![[newplot (4).png]]




uniform and nonuniform superposition 

uniforms is where all the features are equally sparse and equally independent and there is no interference. 

since we are considering equally important features i.e, (I = 1) and equal sparsity an interesting thing to look at is not  the number of features n or the number of hidden features m it is the ratio between them. So how do we even  measure how many features are actually learned to do this we pick Frobenius norm for the $||W_{I}||^2$  for any represented it would be one and for any non represented ones it will be 0. it is basis independent and is valid even in dense regime. 

The weight matrix of the model is of shape (m,n) which are defined above if n >> m then lower dimension the model cannot give the orthogonal directions. It must superpose multiple features. 

So a measure needs to be defined to say how many dimensions a feature will capture as we have seen orthogonality is not always possible and the metric we have defined earlier  
 $||W||_{F}^2$  = 1 when each dedicated feature gets a orthogonal dimension. Using these we arrive at a summary static called $D^*$  which is the average number of dimensions devoted to one learned feature 
$$
D^* = m / ||W||_F^2
$$
**`D* = 1` — every feature gets its own dedicated dimension** (no superposition)

With `n = 3` features and `m = 3` hidden dimensions, each feature mapped to its own orthogonal direction:

```
                hidden1  hidden2  hidden3
   feature 1  [    1        0        0   ]
   feature 2  [    0        1        0   ]
   feature 3  [    0        0        1   ]
```
$$
||W_{dedicated}||_{F}^2 = 1² × 3 = 3 
$$
$$D^* = m / ||W||_F² = 3 / 3 = 1
$$
**Case -  2:   D* = 1/2  antipodal pairs**

With `n = 6` features sharing only `m = 3` hidden dimensions, two features per dimension pointing in opposite directions (`+1` / `-1`):

```
                hidden1  hidden2  hidden3
   feature 1  [    1        0        0   ]
   feature 2  [   -1        0        0   ]
   feature 3  [    0        1        0   ]
   feature 4  [    0       -1        0   ]
   feature 5  [    0        0        1   ]
   feature 6  [    0        0       -1   ]
```

$$||W_{antipodal}||_{F}^2 = 1² × 6 = 6$$
$$D^* = m / ||W||_{F}^3 = 3 / 6 = 1/2$$
This phenomenon we have observed is similar to fractional quantum hall effect. I have plotted the 2 curves so that you can grasp the parallels. The quantum Hall effect occurs when a 2D electron gas at low temperature and high magnetic field shows Hall conductance that is quantized into exact integer or fractional multiples of e²/h. These plateaus arise from topological properties of the electron wavefunctions, which form Landau levels, and the fractional version stems from strong electron correlations creating quasiparticles with fractional charge. It is a very interesting phenomenon and looking for a slight detour would be a great afternoon read. 



![[newplot (5).png]]

In the fractional $D^*$  half in the above case the features comes in antipodal pairs $W_{k}$ = -$W_{j}$ exact negatives. 

This antipodal pairs raises an interesting question. how much can the per feature dimensionality distribute. To answer this we define ith feature $D_{i}$ as 


$$D_i = \frac{\|W_i\|^2}{\sum_j (\hat{W}_i \cdot W_j)^2}$$

numerator represent to what extent the feature is represented and the denominator represent how many features share the dimension it is  embedded in.

in the antipodal pairs case we get a nice 1/2 the graph is sticky (in mathematical terms stickiness refers to this - If a feature is “sticky,” the network keeps using it even after transformations or layer changes. If features are not sticky, the representation changes more freely and the model becomes less dependent on any single dimension. )
![[newplot (7).png]]
we were to take these generated superposition models and try to vary the sparsity levels all while we observe some features getting absolutely no representation to a dedicated dimension. if we to see how these phase changes occurs it makes quite an interesting plot similar to the Electron phase diagrams akin to landau levels. we can see int resting geometric patterns emerge a digon, triangle and tetrahedron kind of structure which minimizes the most amount of energy like we see in the chemistry. 

<iframe src="https://factity.github.io/interpretability/plotsiframe/phase.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>

Telling us that the fractional dimensionality we have observed is indeed the super position.  when our model chooses to represent a feature it is representing it in an m - dimensional sphere. since we are using uniform importance these are trying to be symmetric. 




The core mathematical phenomenon happening here is the equivalence between point configurations and gram matrices. Given n features represented in m dimensions 

Any set of \(n\) points in $(\mathbb{R}^m$) gives a rank-\(m\), \(n* n\) positive semi definite matrix whose entries are the dot products between points.

If we were to represent how much of these features interfere the formed matrix $W^TW$ captures how much of these features interfere. all the diagonal entries of the formed matrix represent the individual features and rest of them represent the features that were experiencing interference in the representational space.  

The below diagram shows how features are arranged into 2d space 
<iframe src="https://factity.github.io/interpretability/plotsiframe/2d.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>
The below diagram shows how features are arranged into 3d space 
<iframe src="https://factity.github.io/interpretability/plotsiframe/3d.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>
Nonuniform superposition 


In most of the real world networks uniform superposition is rarely observed. 
when there is non- uniform superposition there is a smooth deformation of the polytopes we have talked about earlier. Akin to the energy molecules as more and more imbalance builds up they break into small polytopes. Correlated features were also observed to fall into orthogonal directions essentially forming a local basis. anti correlated features form interference and fall almost in the same direction. 

![[newplot (6).png]]


If two features a and b that always fire together or both zero you give it only one dimension to represent them. The model maps a and b into a single number z. 

- **PCA solution** – finds the direction of maximum variance.  
    For two perfectly co‑activating features, the first principal component is $\frac{a+b}{\sqrt{ 2 }}$  and the second, which captures their differences, is a−b22​a−b​.  
    With only one dimension, PCA keeps the **sum** and throws away the **difference**. So the model represents the shared component and ignores what makes them distinct. This is the **collapse**: two features merge into their principal component.
    
- **Superposition solution** – exploits _sparsity_ (features are rarely active).  
    If a and b are active only very rarely, the model can represent both in the same dimension by assigning them **almost orthogonal directions** in the high‑dimensional neuron space—here, just opposite signs (e.g., a→+1a→+1, b→−1b→−1). Because they rarely fire together, their interference is minimal, so the model can recover each one individually despite the bottleneck.
as the levels of sparsity gets decreased the superposition gradually decreases and the representation becomes equivalent to pca. 

If we were to plot with the similar toy models from the above but now with correlation included and gradually increase the sparsity 
The following structural collapse happens 
I have made visualizations for this phenomenon in 2d, 3d 
focus specifically on the dotted lines in the below plot 

<iframe src="https://factity.github.io/interpretability/plotsiframe/2dcollapse.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>


<iframe src="https://factity.github.io/interpretability/plotsiframe/3dcollapse.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>



<iframe src="https://factity.github.io/interpretability/plotsiframe/featurecollapse.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>
you can control manually using the below slider there are 2 different varaiables at change here 

<iframe src="https://factity.github.io/interpretability/plotsiframe/tegumcollapse.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>

Unlike most neural networks, a fully trained neural network the fully trained  converge to a simple but nontrivial structure that rhymes with the geometric structure rather than simple weight sequences like we have presented earlier.  The nature how this property emerges is more discrete than it is continues. As seen from the phase plot. 

If we were to plot the learning dynamics of the model with dimensionality we observe several jumps in the loss curve. This is explained using the phenomenon of grokking. where there is a abrupt jump. One of the cool analogies we can think of the state of water and gas molecules when we heat the water it doesnt just turn into gas it gain energy until a particular temperature reaches and suddenly starts turning to gas. The continuity in most regions of the curve is due to similar phenomenon 






learning as a geometric transformation 
We can see in the below plot how the correlated features occupy the orthogonal pairs and the anti correlated ones moves to the opposite direction. With the moving towards increasing training steps we can see how the features move towards geometrically stable positions 


<iframe src="https://factity.github.io/interpretability/plotsiframe/geometrictransformation.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>



As the sparsity increases more and more features get intertwined with the superposition. If you want to grasp how the activations are effected and how a feature contributes towards the activation. I took a sample of 5 neurons and 7 features to show how they are mapped and how the representations in the superposition would 
change over time. what started out as fairly good separation moves towards a spectrum. 

<iframe src="https://factity.github.io/interpretability/plotsiframe/neuronlevelview.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>

Relationship to adversarial robustness 
So the actual question arises, how can we ensure that the model is robust. How do we make sure that the model does not hide harmful thoughts and features in the super position ? 

<iframe src="https://factity.github.io/interpretability/plotsiframe/reconstructattack.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>

In a model without superposition the end to end weights for the feature are 

$(W^TW)  =  (1, 0, 0, 0, ...)$  and the model with superposition is $(W^TW)  =  (1, \epsilon, -\epsilon, \epsilon, \dots)$
These open up an whole knew avenue of attack surface.  The network is fairly robust with training it only break when attacks were specifically targeted at a particular feature by using optimal L2 attacks for each feature $(λ(W^TW)_{i}/∣∣(W^TW)_{i}∣∣​)$
Although this one of the ways perpetrator could hide harmful features. This is not the only way but superposition could be used to explain a lot of the reasons for the storage. I mean if we look at the superposition we can say the harmful phenomenon resided in the superposition. To understand how the attack matters and at which stage of training I have plotted target feature under attack vs sparsity level 


<iframe src="https://factity.github.io/interpretability/plotsiframe/sparsitysweepattack.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>
we have also plotted the target under attack and the training stages and overlapped the training loss on the curve. as we can see in the below plot attack at the input stages allows for the model to hide the attack surface well and cause much severe consequences 

<iframe src="https://factity.github.io/interpretability/plotsiframe/trainingsweep.html" width="100%" height="600" style="border:0;" loading="lazy"></iframe>

As we have observed earlier the attack surface becomes large it network not just represent the features it also perform computation in the superposition.   I have plotted computation between 2 features and how it is represented in the neurons 

/// generate the plot for this 


what it means for ai safety ? At the end we want to have grasp over all the features that are being represented we want to detect if there is any form of deceptive tendencies happening inside the model. we want to have universal quantifiers over the model. we want to decompose the activation space and tune have a basis which we can rely on, describe activations in terms of features, able to explain any form of phenomenon we observe. understand and map out the weights. Although we attribute tremendous performance gains towards polysemanticity. we attribute strong unfamiliarity towards in large models. we can avoid this either by removing super position entirely. having a over complete basis or mix of the above, but once we scale the models even slightly it becomes surprising hard to grasp what goes on. 

If we do indeed remove all the form of superposition we end up with much cleaner models but with significant performance cost only of way to implement this in a higher level is to use the mixture of expert models. we can assign block to features and certain regions of the model activate only when performing certain tasks. Although this is a good alternative at the models of the present scale we cannot particularly endorse and rid of any model with super position. 

we can also look at using an over complete basis but training a sparse auto encode like model on top these become almost impossible for a billion layer we need thousand times the number of neurons to represent them and even the interference pushes against this. In the below section we will be covering monosemanticity to see which of the concepts appear and perform some experiments on them 


Things that we hope to grasp from the following post 
- [ ] Superposition is real and an observed phenomenon 
- [ ] Neurons can be of both polysemantic and monosemantic 
- [ ] some form of computation can be performed in superposition 
- [ ] phase change dictates if features are stored in superposition 
- [ ] we can represent features into geometric structures 



## Monosemanticity 

In the previous sections we have seen the phenomenon of superposition.  We have seen both the positive and negative effects of the superposition.

As the dimensions of the features grows larger sparsity grows rapidly, distances become less informative. 

![[Excalidraw/Pasted image 20260722143150.png]]

the volume of the latent space grows larger exponentially. The internal states cannot be understood unless they are decomposed into independent components. 
![[Excalidraw/Pasted image 20260722151016.png]]


The meaning of the concept of local neighborhood $\epsilon$ becomes less informative. It becomes a lot more interpretable when it is just one layer attention only models but as the size grows and MLP block is added it becomes almost impossible  to break it down into interpretable features. 


![[Excalidraw/Pasted image 20260722164401.png]]




So the natural question arises. How do we approach breaking down the MLP block into to understand what goes inside the model. 

In the previous sections we have covered simpler architectures with one or 2 layers and looked at induction heads inside the [transformers](https://factity.github.io/safe-ai/interp_test) .  we have exclusively focused on the attention blocks we broke them down into one layer attention blocks, two layer attention blocks and looked at how bigram statistics emerged. When it comes to MLP block it becomes impossible to break them down in this structure because the MLP is an actual traditional neural net. All parts of the layers matter to put this simply if we just took one layer depth the model will not predict well. we need all the different layers to get the needed performance to make a more accurate prediction. Fortunately traditional neural nets have established frameworks for interpretability and large body of work for all types like CNN's, RNN's, GAN's etc. 

Our objective is to break down the MLP block and understand which of the following concepts will be associated with neurons. so we map $\mathbf{x}^j$ with different activation's in the layer. 

$$
\mathbf{x}^j \approx \mathbf{b} + \sum_i f_i(\mathbf{x}^j) \mathbf{d}_i
$$

![[Pasted image 20260723073804.png|510]]

Here $d_{i}$ is a unique term which is associated with a direction in the feature space. This process is called linear vector factorization. Each direction is associated with a concept.  To understand the activation we train a sparse autoencoder on the activation layer 

$$
f_i(x) = \text{ReLU}( W_e (\mathbf{x} - \mathbf{b}_d) + \mathbf{b}_e )_i,
$$

where $W_e$is the weight matrix of the encoder and $\mathbf{b}_d, \mathbf{b}_e$ are a pre-encoder and an encoder bias. The feature directions are the columns of the decoder weight matrix $W_d$  . 

![[Excalidraw/Pasted image 20260722181138.png]]

From the above section on superposition we have seen that neurons try to represent more features essentially forming an over complete basis. To decompose the activation layer using the sparse encoder and to interpret the results. we need to make sure the following are satisfied. 

1.  We should have a clear understanding of which of the following inputs leads to the activations that is required. This property is related with the Causality, generality, and purity and help us grasp which property activate a specific instance 

2. The down stream layers pass down the effects of perturbations made. Suppose we make a simple change in the upper layer the changes will be reflected in the sub subsequent layers.

3. features explain significant portion of the functionality of the MLP 

If we were able to satisfy the following criteria then we can:

-  Determine how much of the feature changes the output and the next layer activations. 
- Monitor the network for the activations of a specific layer 
- Trickle down effect is observed i.e, changing the upper layers changes the downstream layers 
- The network actually works i.e, that is the network is able to approximate the data 
- The data is actually influencing the output 
- Design inputs that will trigger an activation [^1]

	Even if we were able to remove the superposition completely we still observe superposition any amount of architectural changes does not guarantee the complete removal. Let us suppose we took a single neuron with 4 different mutually exclusive features and one hot encoded them to eliminate any form of overlap A/B/C/D we still observe superposition from just the inherent nature of mutual exclusivity. The preference score incentivize  the model to acquire superposition  thereby reducing the loss.

![[Pasted image 20260723090450.png]]

superposition shows that large set of sparse features could be represented in the lower dimensional space.  Natural latent variables are sparse and we are trying to map higher dimensional vector from a lower dimensional projection. Although greedy methods can be approximated well but sparse auto encoders works well just because of the scalability.  sparse auto encoders can be grown to approximate any large data sets. 

![[Pasted image 20260723105729.png]]

The sparse encoder we have designed has a linear layer attached to the encoder block with ReLU activation function and a decoder block with another linear layer and a decoder block.   
The best factorization is the one that minimizes the total information of autoencoder  and the data 


importance of the scale . training models on larger amounts of data has shown to form more sharper boundaries and increase the expressivety 

Some of the neurons while training does not activate and appear to be dead by resampling we can rejuvenate the dead neuron. After these are done the most subsequent logical step is to 
measuring the performance of the autoencoder. we can understand how these work either by manually check to look for patterns, by analyzing  feature density finding on which of the following tokens the model fires, by looking at the MSE loss on how accurately these map the MlP etc. 

advantages of using a one layer model 

-  Fewer features to represent i.e, have the ability to cover all the features using the dictionary we are using.
- we have the ability to train the models quite cheaply. higher number of training tokens will allow models cleaner representations 
- Because of the linearity. we can easily analyze the logit outputs and we have also shown that the properties generalize in multilayer models. We would have the opportunity to analyze not just the data distribution but also the functionality of the model. 


///////////////////////////////////////////////////////////////////////////////////////////////////////////////////

rough draft of what will be happening we will be changing it in the subsequent sections the numbering scheme based on the experiments we will be carrying out 

what are the parameters we will be keeping in mind 

--> find the model from which the features have originated 
--> learned factors and L1 coefficients  used 
--> final correspond to the final feature in the run 

![[Pasted image 20260723160055.png]]


interface for explaining the features 

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

investigation of the individual features and some of the findings 

text written in Arabic | DNA sequences | base 64 strings | text written in Hebrew

the following will be established for the learned features 

-  the leaned feature activates with high specificity for the hypothesized context 
- the learned feature activates with high sensitivity for the hypothesized context
- the learned feature causes appropriate downstream behavior  
- the learned feature does not correspond to a neuron 
- the learned feature is universal 




![[Pasted image 20260723164424.png|697]]


after the experiments are done list the ones that you have observed about which of the activations caused what explore the following

select a bunch of characteristics and do the following each for the selected characteristic
1. Activation specificity 
2. Activation sensitivity 
3. downstream effects 
4. feature is not a neuron 
5. universality 

//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

### Global analysis 

In the above section we have associated particular features with the associated activations in this section we will be looking at the overall picture. 

//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
note the number of features the selected model with the fixed L1 will display 
find how many of them are dead or ultra low dense and display atypical properties 

Looking at the typical feature and how interpretable it is 

human analysis and two automated methods of interpretability 


### feature types 

After modeling we found context features and token in context features. 

theoretical outlook of the transformer takes two inputs and produces a output 

n token conjugations in the MLP blocks 

token in context feature the word  **the** has been activated in 100 different features in different contexts 



|                   | Transformer | sparse autoencoder |
| ----------------- | ----------- | ------------------ |
| layers            |             |                    |
| neurons           |             |                    |
| dataset           |             |                    |
| loss              |             |                    |
| number of weights |             |                    |
| algorithm         |             |                    |



#### key takeaways 


-  Sparse autoencoders extract relatively mono semantic features. 
- Spare autoencoders produce features that are not readily associated with the neuron basis 
- When the patterns are associated with the autoencoders we can trigger it to generate specific generations 
- The features found with the auto encoders are universal 
- The wider the size of the auto encoder the more our ability to capture more concepts more fine grained structure 
- relatively small number of neurons can represent complex concepts 
- generate finite state automata diagrams for what is happening 




















