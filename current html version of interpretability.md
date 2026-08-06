

<div>
<div>Chapter 5 Interpretability and Explainability</div>
<h1>
Understanding the Internals of the
<em>
</h1>
<div>
<div>
<div>Author</div>
<div>Research Notes</div>
</div>
<div>
<div>Topic</div>
<div>Interpretability · ViT · CNNs</div>
</div>
</div>
<blockquote>
“The mind, once stretched by a new idea, never returns to its original dimensions.” — Ralph Waldo Emerson
</blockquote>
<p>
So I had this conversation about AI once, a strange but small encounter. I was asked to explain  simply: <strong>“How does AI work?”</strong> I was overwhelmed, possibly so that I have spent the last couple of years studying it. There is simply way too much and I could not get myself to a point where I could start.
I do <em>, which I often consider to be  one of my traits — whether it is positive or negative, I am really not sure. I talk with my audience in mind. I simply was so overwhelmed that I simply said, “<strong>.” I did not give a good impression for sure; with some awkward stares we moved on.
A long, long time ago I read some of <strong> work. Whenever I encounter the problem of breaking down a subject and doing selective speak, I often find myself going back to his work and try to understand how would he have explained it. Now, I am not no Feynman, nothing but an <em>. I did what I can to break down everything I learnt about <em> — the question of <strong>, although <strong> is another behemoth on its own. In this chapter we will stick with why.
</p>
<p>
I started digging, curious as I was. There are simply way too many fields, way too much stuff; condensing it all is simply not possible. And the best part about this is the people who are actually building this technology have very little grasp on the field themselves. With the ever-increasing size of the models, the use cases, the sheer scale alone should make it almost impossible to study these. Humans as we are, with the indefinite amount of grit, we started chipping away at these with our chisel.
</p>
<p>
In the spirit of
<strong><u><a href="https://calteches.library.caltech.edu/51/2/CargoCult.htm">Feynman’s Cargo Cult Science lecture</a></u></strong>, in his words:
</p>
<blockquote>
“When you study only what results you get, you never build a deeper understanding. When you study <strong>why</strong> something happens, you can refine your methods, discard dead ends, and make genuine progress.”
</blockquote>
<p>
Any rigorous scientific study or a method should have a clear, reproducible basis. A fundamental axiom will be that <strong>ML models are no different than classical models, except in size</strong>.
</p>
<p>
Certainly, classical models like Newton’s Laws, the Standard Model, or General Relativity feel different than ML models, owing to the fact that these models are determined by physical principles, even though they may still contain parameters that need to be calibrated from data. By “<strong>classical</strong>”, we mean models created by scientists without using ML techniques. Related terms that are often used are <em>intelligibility</em> and <em>understandability</em>.
</p>
<p>
We will consider <strong>interpretability</strong> and <strong>explainability</strong> to be the primary axes of interest in understanding the <em>why</em> of the model. <strong>Interpretability</strong> concerns the ability to understand, or approximate, the inner workings of a model and how it reaches its output. <strong>Explainability</strong> concerns the ability to map the model onto existing knowledge in the relevant scientific domain.
</p>
<p>
The key difference is how we classify it. Are we able to <em>explain</em> the model? What is <em>happening</em> inside it? <strong>Interpretability</strong> is the degree to which a human can understand the cause of a decision.
</p>
<blockquote>
“A method is interpretable if a user can correctly and efficiently predict the method’s results.”
</blockquote>
<p>
The more interpretable a machine learning model, the easier it is for someone to understand why certain decisions or predictions were made. A particular model is <em>more interpretable</em> than another model if its decisions are easier to understand than the other model’s. Knowing the ‘why’ can help you learn more about the problem, the data, and the reason why a model might fail.
</p>
<p>
In some of the cases we might not just need interpretability. In cases like reccomendation systems for movies. well researched technqiuies like ocr does not warrant the use of interpretability techniques. As you will see in the below section explaining a model is often a very compute intensive , tideous and most inmpotantly it is largely a manual task. One of the argument presented by
</p>
<p>Doshi-Velez and Kim (2017), is that **the need for interpretability and explainability arises from an incompleteness in problem formalization**. This means that for many real-world tasks, the formal objective function we optimise (e.g., classification accuracy) does not capture everything that matters.A single metric like classification accuracy gives us the <strong>“what”</strong> – the prediction.
- But it does not tell us the <strong>“why”</strong> – how the model arrived at that prediction.
one of the most important benefit of doing interpretability and explainability it lets us use these systems in mission critcial scenarios. Most real world tasks are incompletely formalised, have strong ethical and moral concerns and contextual factors associated with them. Any slight error can lead to catastrophic consequenxces.
One of the important application of explanaibility and interpretability is in ai safety. It helps us avoid plothera of problems. Machine learning models deployed in real contexts have life altering decisions and with the current rate of progress they will fundamentally shape our lives. A oracle that simply gives you answers to anything but doesnt tell you how will distrupt humanity and it is deeply unsettling.
Reasons for investing in interpretability
<div>
<p><strong>Fairness:</strong> Ensuring predictions do not implicitly or explicitly discriminate against underrepresented groups. Without interpretability, detecting and correcting bias is nearly impossible.</p>
<p><strong>Privacy:</strong> Verifying that sensitive information in the training data is not being inadvertently memorised and leaked through predictions.</p>
<p><strong>Reliability / Robustness:</strong> Confirming that the model does not produce drastically different outputs for minimally perturbed inputs (a phenomenon adversarial examples exploit). Interpretability can reveal whether the model relies on brittle features.</p>
<p><strong>Causality:</strong> Ensuring the model picks up only genuine causal relationships, not mere correlations that might fail under distribution shift. A model relying on non-causal features is likely to fail in the real world.</p>
<p><strong>Trust:</strong> Humans find it easier to trust a system that can explain its decisions. Trust is built when an explanation aligns with or respectfully challenges a user’s prior knowledge, rather than being an opaque oracle.</p>
</div>
<p>
Interpretability and explanability would also allow us to analyse a prediction in counter factual terms we can analyse why a particular prediction is generated we can also elimiate why this did not.
By studying these it lets us look at abnormalities, what are the influential factors etc. These explanations should also not be misrepresentataive if a particular reson reson is plusible is it transferable, generalizable etc should also be studied with the help of interpretrability
</p>
</p>
<p>
from a practical stand point you should also look at when to use interpretability if you are looking to increase the model accuracy or finding a causal explanation for a particular case. The anology goes like this a particular resercher when trying to mitigate bias used various complicated interpretability techniques to find the exact reason and solved it but a simple and the optimal method is simply using the more higher quality data which is much cheaper readily avaialble and saves a lot of time.
Imagine a scenario where an AI is extremely intelligent and has derived a <strong>. When we try to understand the internals of the model we find a particular <strong> (an internal element of the model) that is responsible for it. Now we know that to solve the proof, the model should have developed its own forms of, let’s say, <strong>. Here the <strong> are the <em> — they connect the model’s behaviour to existing scientific knowledge. The <strong> is the <em> element — it reveals what inside the model caused that behaviour. <strong>
Validate that the model is solving the problem in a reasonable way.
Detect when the model relies on non-causal features for prediction, which can lead to catastrophic failures under distribution shift.
Find wrong encodings or sub‑par feature engineering that degrade performance or introduce bias.
In a specific case, understand why this particular prediction was made; if the explanation conflicts with domain knowledge, the decision-maker might question the forecast and initiate an investigation, potentially averting a harmful decision.
</p>
<p>
When a neural network classifies an image, it doesn't <em>look</em> the way we do.
It propagates activations through layers of learned transformations, compressing
and expanding representations until a final linear combination of features produces
a prediction. The challenge of interpretability is making that process legible.
</p>
<p>
Over the last decade, a small set of core techniques has emerged: gradient-based
attribution, representation geometry, and attention visualization. Each peels back
a different layer of abstraction. None is complete on its own.
</p>
<h2>Saliency maps: which pixels matter?</h2>
<p>
The simplest interpretability question is attribution — given a prediction,
which input regions caused it? Saliency maps answer this via the gradient
of the output class score with respect to each input pixel:
</p>
<blockquote>
S(x) = |∂f_c / ∂x| — the magnitude of how much each pixel, if perturbed,
would change the class score.
</blockquote>
<p>
This is called <strong>vanilla gradient</strong> or simple backpropagation saliency.
It's fast — a single backward pass — and surprisingly informative, despite
its known instability to adversarial noise.
</p>
<div>
<div>
<span>vanilla gradient saliency</span>
<div>
<button>golden retriever</button>
<button>tabby cat</button>
<button>fire truck</button>
</div>
</div>
<div>
<div>
<div>
<div>predicted class</div>
<div>golden retriever</div>
</div>
<div>
<div>confidence</div>
<div>
<span>
</div>
</div>
<div>
<div>gradient magnitude</div>
<div>
<span>
</div>
<div>
<span>
</div>
</div>
<button>
re-run backprop →
</button>
</div>
</div>
</div>
Vanilla gradient saliency. Select a class above; the heatmap shows which
spatial regions carry the highest gradient magnitude. Re-run to watch the
backward pass animate.
<h3>Beyond vanilla gradients</h3>
<p>
Vanilla saliency has a saturation problem: in regions where the model is
highly confident, gradients become flat even though the features are critical.
Several methods address this.
</p>
<p>
<strong>Integrated Gradients</strong> accumulates gradients along a linear path
from a baseline (often a black image) to the actual input, satisfying an axiom
called <em>completeness</em> — the attributions sum to the total output difference.
<strong> SmoothGrad</strong> adds Gaussian noise n times and averages, reducing
high-frequency artifacts at the cost of n forward passes. <strong>GradCAM</strong>
avoids per-pixel resolution by pooling gradients over spatial feature maps in
the final convolutional layer, producing coarser but more stable localizations.
</p>
<p>
None of these is universally superior. The choice depends on the downstream use:
debugging a misclassification, explaining to a non-expert, or formally auditing
a model's decision process each demands a different fidelity-stability tradeoff.
</p>
<h2>J-Space: the Jacobian as geometry</h2>
<p>
Gradient-based attribution tells us where a model looks. A different question
is <em>how</em> the model has structured its internal representations — what
geometry has it learned in activation space?
</p>
<p>
The <strong>Jacobian matrix</strong> <code>J(x) = ∂f/∂x</code> evaluated at
an input <code>x</code> is a local linearization of the network. Its rows
point in the directions of steepest ascent for each output class; its singular
values tell us how much each of those directions amplifies or attenuates.
</p>
<p>
Projecting a dataset of inputs through their per-sample Jacobians — call it
the <strong>J-space embedding</strong> — yields a representation that captures
both the input's content and the model's local sensitivity structure. Unlike
penultimate-layer activations, J-space preserves information about which
input directions the model considers <em>discriminative</em> rather than merely
which are <em>active</em>.
</p>
<div>
<div>
<span>Jacobian feature space — ResNet-50 layer 4</span>
<button>pause</button>
</div>
<div>
<svg width="340" height="280"></svg>
<div>
<p>
Each point is an image projected through the network's Jacobian matrix — a linearization
of how the model responds to local perturbations around that input.
</p>
<p>
Semantically similar images cluster tightly, suggesting the Jacobian encodes
category structure even in mid-layer representations.
</p>
</div>
</div>
</div>
2D UMAP projection of the J-space embedding for 100 ImageNet images
(ResNet-50, layer 4 Jacobian, top-2 singular vectors). Hover a cluster
to highlight its class.
<p>
The structure visible here — tight, separated clusters — has a direct
interpretation: images that activate similar Jacobian directions cluster
together. This means the model has learned approximately <em>class-conditional</em>
sensitivity structure. A golden retriever and a tabby cat activate different
discriminative directions in weight space, even when their raw pixel distributions overlap.
</p>
<h3>Why J-space matters for interpretability</h3>
<p>
Standard activation-space analysis asks: <em>what did this layer output?</em>
J-space analysis asks: <em>what would have changed the output?</em> The latter
is closer to the counterfactual reasoning we care about in safety-critical
applications. A model that gets the right answer for wrong reasons —
relying on texture shortcuts, dataset artifacts, or spurious correlations —
may produce similar activations to a well-calibrated model while having
a very different J-space geometry.
</p>
<p>
This makes J-space a useful probe for <strong>shortcut learning</strong>.
If a model's J-space clusters cleanly by spurious feature (background color,
photographer watermark) rather than semantic category, the Jacobian exposes it
before it can cause a deployment failure.
</p>
<h2>Attention in Vision Transformers</h2>
<p>
Convolutional networks process images in fixed local neighborhoods. Vision
Transformers (ViTs) divide an image into a grid of patches and process them
as a sequence using self-attention — allowing every patch to attend to every
other patch in a single layer.
</p>
<p>
This makes attention weights a natural interpretability target: they tell us,
for each query patch, which other patches the model weighted most heavily when
computing its representation. In practice, attention is heads × patches × patches,
so the question "what is this model attending to?" requires choosing how to
aggregate across heads and layers.
</p>
<div>
<div>
<span>ViT attention — click to set query patch</span>
<div>
<button>head 0</button>
<button>head 3</button>
<button>head 7</button>
<button>head 11</button>
</div>
</div>
<div>
<div>
<p>
The orange patch is the <span>query</span> — the patch
asking "which other patches am I attending to?" Brighter blue indicates higher attention weight.
</p>
<p>
Different heads learn qualitatively different attention patterns.
Early heads tend toward local patterns; later heads show long-range semantic structure.
</p>
<div>
<span>low attention</span>
<span>
</div>
</div>
</div>
</div>
Self-attention weights from a ViT-B/16 (simulated). Click any patch to set
it as the query; brightness shows attention weight. Switch heads to see how
different heads specialize.
<h3>The head specialization hypothesis</h3>
<p>
A persistent empirical finding is that different attention heads learn
qualitatively different functions. Some heads attend locally, functioning
like edge detectors. Others span the image, picking up long-range semantic
dependencies — "this patch looks like an ear, which correlates with the
dog-snout patch at the other side of the image."
</p>
<p>
<strong>Attention Rollout</strong> propagates attention maps through all layers
by multiplying adjacency matrices, accounting for skip connections via identity
mixing. The result is a per-token "receptive field" in attention-space — analogous
to the spatial receptive field in CNNs, but dynamically computed per input.
</p>
<p>
The limitation is well-known: attention weight ≠ causal importance. A head
can attend strongly to a patch while that patch contributes minimally to the
final prediction (if subsequent MLP layers suppress the signal). Coupling
attention maps with gradient information — <strong>Grad-CAM over attention</strong>
— partially addresses this by weighting maps by their gradient w.r.t. the class score.
</p>
<h2>Activation maximization: what does a neuron want?</h2>
<p>
Saliency and attention tell us which parts of a given input mattered.
Activation maximization inverts the question: <em>what input would maximally
excite a given neuron?</em> This is found by gradient ascent in image space,
starting from noise and iterating:
</p>
<blockquote>
x* = argmax_x f_i(x) − λ·R(x)
</blockquote>
<p>
where <code>f_i</code> is the activation of unit <code>i</code> and
<code>R(x)</code> is a regularizer discouraging unnatural images (total variation,
Gaussian blur, frequency penalization, or a learned image prior).
</p>
<div>
<div>
<div>
<canvas width="96" height="96"></canvas>
<div>layer 1 · neuron 23</div>
<div>Gabor edge detector (45°)</div>
</div>
<div>
<canvas width="96" height="96"></canvas>
<div>layer 2 · neuron 71</div>
<div>high-frequency texture</div>
</div>
<div>
<canvas width="96" height="96"></canvas>
<div>layer 3 · neuron 142</div>
<div>curve / arc detector</div>
</div>
<div>
<canvas width="96" height="96"></canvas>
<div>layer 4 · neuron 8</div>
<div>color blob (warm)</div>
</div>
</div>
</div>
Synthetic activation maximization patterns for four neurons at different network depths.
Early layers show Gabor-like edge detectors; deeper layers produce complex textural structures.
(Animated — patterns evolve continuously via gradient ascent simulation.)
<h3>From neurons to concepts</h3>
<p>
Early conv layers reliably produce Gabor filters — oriented edge detectors at
various frequencies. This isn't surprising; it replicates the primary visual cortex.
What's remarkable is that it emerges from random initialization and gradient descent,
not from architectural inductive bias.
</p>
<p>
Deeper layers are more interesting and harder to interpret. A single neuron in
layer 4 might respond maximally to "a dog snout seen from slightly below, with
golden fur, in warm light" — a combination so specific it resists any single English
label. This is the <strong>polysemanticity problem</strong>: neurons at intermediate
depth respond to multiple distinct, unrelated concepts, presumably because the
network has learned to reuse representational capacity via superposition.
</p>
<p>
Sparse dictionary learning — training a sparse autoencoder to reconstruct layer
activations from an overcomplete basis — is the current best approach to decomposing
polysemantic neurons into monosemantic features. Each basis vector corresponds to
a single interpretable direction; their activation maximizations are far cleaner
than those of raw neurons.
</p>
<h3>Closing thoughts</h3>
<p>
Each technique described here illuminates a different facet of a vision model's
learned representation. No single method gives the full picture. Saliency maps
identify attribution but not mechanism. J-space characterizes representation
geometry but not causal structure. Attention weights are legible but not
causally faithful. Activation maximization synthesizes preferred stimuli but
conflates multiple functions.
</p>
<p>
The deeper ambition — a complete mechanistic account of how a model transforms
pixel values into semantic predictions — remains open. Progress is coming from
combining these tools: using attention to identify candidate circuits, patching
to verify causality, and sparse decomposition to isolate features. The field
is young. The images are starting to come into focus.
</p>
<div>
<div>Further Reading</div>
<div>
<div>
<span>Simonyan et al., 2014</span>
<a href="#">Deep Inside Convolutional Networks: Visualising Image Classification Models and Saliency Maps</a>
</div>
<div>
<span>Sundararajan et al., 2017</span>
<a href="#">Axiomatic Attribution for Deep Networks (Integrated Gradients)</a>
</div>
<div>
<span>Dosovitskiy et al., 2020</span>
<a href="#">An Image is Worth 16×16 Words: Transformers for Image Recognition at Scale</a>
</div>
<div>
<span>Elhage et al., 2022</span>
<a href="#">Toy Models of Superposition</a>
</div>
<div>
<span>Bricken et al., 2023</span>
<a href="#">Towards Monosemanticity: Decomposing Language Models with Dictionary Learning</a>
</div>
</div>
</div>
</div>