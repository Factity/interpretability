The transformer architecture is the modern basis for large language models. The concepts surrounding the topic are dense and there are several useful guides to studying them. It is one of the powerful architectures born out of a phenomenal paper called attention is all you need. Although the one proposed in the paper was an encoder decoder based translation model. The traditional llms use a slightly different variant called as auto regressive decoder based models. The literature around deep learning architecture is very dense with several successful structures dealing with different use cases are thoroughly studied by several people. Although I wanted to include this detailed breakdown in the chapter interpretability in my book (open draft) safe ai. The content in the topic itself is very dense and do not want the detour to be a bottleneck for someone to finish the chapter. I built this log purely for aesthetic reasons alone and just to try out some new visuals. Probably the best way to remember is to study something visual in the spirit of that I developed this blog. 

Before you take a deep dive if you find my writing to be out of scope and does not like the way I present content. Please feel free to check the below guides , Honestly this where i took most of the content from. 

Absolute wonderful work by neel nandha and team at → https://transformer-circuits.pub/2021/framework/index.html

If you are visual learner or like me you have an attention span of an humming bird there are incredibly well presented work by grant sanderson at 3 blue one brown → https://youtube.com/playlist?list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi&si=KOpLEeWnHF9EgVBy

Or if you just wanna go with the original please check out the original paper at 

→ https://arxiv.org/abs/1706.03762

All of the above guides are absolutely fabulous and I cannot recommend them enough. 

It is always good to have a basic understanding of linear algebra and matrices in general if you are looking to learn about that please have a look at my linear algebra guide -> https://factity.github.io/safe-ai/APPEN/Linearalgebra.html




Before we implement the generative pre trained transformer we are building upon the foundation of a a simple two layered transformer with only attention blocks. (heavely inspired from the blog post by (Link ))  specific attention heads that we term “induction heads” can explain in-context learning in these small models, and that these heads only develop in models with at least two attention layers.

To intuitively understand let us consider some edge case scenarios a 0 layer model 

If the attention heads are missing it simply becomes a bigram model with the embedding matrix WE and unembedding matrix WU so the output becomes simply the probability of predicting the next token. If much of the concepts in this section does not immediately make sense dont worry we do indeed full recap in the below section where we dissect the gpt model 

In a one layer attention only model we sort of look back the previous token but with only on step of missing in the attention block given the current token (C) and some earlier token (A), the model can predict the next token based on the pattern “A … B C” — effectively copying information from token A to influence the prediction after C, even if there are intervening tokens.

As we progressively add more layers with 2 layers of attention only models this enables us induction phenomenon    similar to if ab….. a  then the model predicts b similar how induction works hence the name induction heads but it is not as simple as that. 





Implementation of a transformer from start to finish 

There are so many variants of transformers and each of them is pieced together with several different choices at different stages with different attention mechanisms etc. For the simple purposes of this work we will be looking at gpt specifically gpt 3. There have been several hundreds of methods proposed to date in various sub fields and it has been an iterative process till now every time the engineering is optimized for newer versions of the models with different techniques all the time.



A transformer block can only take matrices as input so what sort of matrix representations rightfully convey the essence of the text. There are several different ways for even how the embeddings could be generated. I cannot emphasize this enough that much of the training of these llms systems have been an engineering optimization problem all along.  Let us start by dividing up our text into chucks we call tokens your immediate guess might be to just simply divide up the words if you come older nlp based practices well you are not far from it but here we are trying to captures all the nuances and looking to gather as much information as possible we will take into account every character, punctuation mark, white space and sub word chunk. 
To do this we use an approach called as byte pair encoding. The vocabulary in our case consists of 50257 entries and there are 3 different types of these 

→ the base tokens 


If are looking for each of the you can find them here → 

I have built a simple tool to check how are different sentences split if are looking to write a piece of text and check how they are split you can use my tool here (add link to the tokviz tool )






What is tokenization ?

Itis simply the method of converting raw text into sequences of discrete units that the model can process.   The unicode strings are converted to -> [x1,x1………….]  so why do we even have to tokenize in the first place words are different and carry unique meaning thats how language works. The answer lies in trade off between vocabulary size and sequence length both of which can heavily effect the cost and capability of a model. If you break hye sentence down word by word the vocabulary size simply explodes imagine all the misspellings. Infected forms and just out of vocabulary words break the model. If we use a charac6ter level or byte level. The vocabulary becomes the standard 256 bytes but the sequence length becomes too large almost 4 times the length of the words. Also the information individual character carries is too small it anyway would be bound to create in the further layers GPT‑3’s 50k‑token vocabulary is precisely chosen to sit at this sweet spot. It means the model can process roughly 4× more text in the same context window compared to a character‑level model, while still representing any possible Unicode string without <UNK> it also helps with reconstructing the word boundaries 




In gpt-3 we use a tokenization methods called as subword tokenization : and the method used to encode the tokens is byte pair encoding. It simply works on bytes instead of unicode characters.

Byte encoding: the raw input text is encoded into a utf8 byte sequence. This means every character becomes 1-4 bytes. Even characters outside the vocabulary are representable as well. 


The initial vocabulary consists of 256 bytes and they are iteratively merged to most frequent adjacent byte pairs into new tokens producing 50,257 tokens.

Then the model uses a fixed ordered list of merge rules but on byte sequences to yield sub words (which can be of a single character, a full character or even multiple characters )
The final byte tokens are mapped to integer ids.

The vocabulary size of gpt 3 is 50,257, which consists of 50000 merges + 256 bytes and a special token. 



To be more rigorous and turn the above algorithm into a much more formal mathematical representation → 

We start of by making a training corpus simply by a multi set of words {w1, w2, w3 ……}
Each represented with an end of the word marker </w> or in the case of the gpt models they used a regular expression which read through the text and just simply breaks it into appropriate chunks. 

Here is the regular expression they use 

→ write regular expression they have used 

I have built a tool around how the regular expression is processed below for your reference give it a try it might help you understand them better (link to the )

One the initial splitting is done 




→ write the algorithm here and while writing it make usre to include the regex element and two stages of encoding and decoding that happened byte encode word encode byte decode byte discord word etc ………..   Here 

It is one of the crucial steps of training a transformer. 





 a learned token embedding matrix, and a learned absolute positional embedding matrix is used. 














Input : data must be converted into a set or sequence1 of N tokens x (0) n of dimension D 








The embeddings can be fixed or they can be learned with the rest of the parameters of the model e.g. the vectors representing words can be optimised or
a learned linear transform can be used to embed image patches

A sequence of tokens is a generic representation to use as an input – many
different types of data can be “tokenised” and transformers are then immediately
applicable rather than requiring a bespoke architectures for each modality as
was previously the case (CNNs for images, RNNs for sequences, deepsets for
sets etc.). Moreover, this means that you don’t need bespoke handcrafted
architectures for mixing data of different modalities — you can just throw them
all into a big set of tokens.

The transformer will ingest the input data X(0) and return a representation of
the sequence in terms of another matrix X(M) which is also of size D × N.
The slice xn = X
(M)
:,n will be a vector of features representing the sequence at
the location of token n.



We are constraining ourselves only to text based inputs for now and exclusively looking at generative pretrained transformer for now further discussion is  done in one of the other sections which you can find here (--> link to the resource ).

Byte‑pair encoding (BPE): Starts with characters/bytes and iteratively merges the most frequent adjacent pairs. Used by GPT, LLaMA, Mistral, Falcon, etc. The “byte‑level” variant works directly on raw UTF‑8 bytes, guaranteeing no out‑of‑vocabulary tokens.

WordPiece: Similar to BPE but selects merges based on likelihood (language‑model objective) rather than pure frequency. Used by BERT.

Unigram language model (SentencePiece): Treats tokenization as a probabilistic segmentation; selects a vocabulary that maximises the likelihood of the training corpus under a unigram model. Used by T5 and others.

SentencePiece: A library that can implement BPE or Unigram, and treats the input as a raw stream of characters (no pre‑tokenization into words), which is handy for languages without spaces.


Here are some of the variants of the techniques which are in popular use. 

The way we develop the vocabulary and what sort of methods we should use for the language models is very tricky and  much more of iterative and intuition style study. There have been several ways by which tokenization can be used to jail break an llm using adversarial inputs. 

https://www.lesswrong.com/posts/aPeJE8bSo6rAFoLqg


There are several anomalous tokens which result in several undocumented failures in gpt models. Some of these tokens break the determinism of the gpt models even with temperature set to zero. We will see in the later section that the transformer architecture is built around maximizing the probability of the next token. So instead of (ideally ) looking for a so called ground truth the models try to give there best approximation. We also find the tokens when represented in the embedding space have some sort of coherence. Sort of like if the embeddings are represented in a higher dimensional space the distance between the words girl and boy is much more similar to the distance between man and woman. So essentially we are able to cluster these embeddings to find all sorts of interesting patterns between them. 































Wait a minute …. Before we jump ahead of ourselves let us establish some definitions first so that we are all on the same page. Definition alert !!! 


Transformer → A particular kind of neural network design that uses attention to process sequences. It is the basis from which most of the variants of the model language models emerged. 

GPT → An acronym for Generative Pretrained Transformer. It is a family of models with a certain special kind of transformer architecture 

Back propagation → The standard algorithm for deep learning that adjusts all of the model parameters based on the loss calculated from the training text 

Token. A small chunk of text. May have mean may not be semantically correct we do not bother. 
Tokens can be whole words or straight characters or anything in between.

Embedding The process of turning a token into vector, a list of numbers that try to capture some form of information regarding the text 

Vectors → an ordered list of numbers that points to a point in n- dimensional space (vn)
Dot product -> A way of capturing the result of product of two vectors as to how much the two vectors point in the same direction 

Vocabulary
The fixed set of all tokens that the model knows about. For GPT‑3 this set contains about fifty thousand items.


Attention block -> this is the place where all the information about the embedding vectors get exchanged 

Multi layer perceptron →A stage where every vector is processed independently by the same simple network. Here weights are tubed with back prop to find the optimal ones 

Context size - the max number of tokens the models can look up at once 

Unembedding matrix: A table of numbers that maps the final, context‑rich vector back into a score for every possible token in the vocabulary.

Logit: One of the raw, unnormalised scores produced by the unembedding matrix before they are turned into probabilities.

Softmax
A function that converts an arbitrary list of numbers into a proper probability distribution, where all values lie between zero and one and add up to one. The one we use here is RELU although with a fine correction around the y axis called GELU for more smoothness 

Temperature
A single number that adjusts the softmax distribution. Higher values make the distribution more even and exploratory; lower values make it more concentrated on the most likely token.

System prompt: A predefined context given to the model before the real prompt is passed it established the format of the out, if there are any language changes, what should be the tone of the response and characteristics like this. 

Fine‑tuning
An extra round of training on a more specific dataset, after the initial pretraining, to adapt the model to a particular task.

Weight
One of the many adjustable numbers inside the model that control how information is transformed. Weights are learned from data during training.

Parameter
Another name for a weight; any number inside the model that is tuned during training

Tensor
A generic term for a multi‑dimensional grid of numbers, such as a list of vectors or a stack of matrices.





https://flask-production-477c.up.railway.app/


<li>I have build a simple tool you can play around with which tells you how different sentences are split which of the token represent a particular number in the vocab etc <a href="https://flask-production-477c.up.railway.app/" target="_blank" rel="noopener">have build a simple tool you can play around with which tells you how different sentences are split which of the token represent a particular number in the vocab</a></li>









Embedding Type	Modality	Description	Transformer Variant(s)
Learned token embedding (subword)	Text	Look‑up table over BPE/WordPiece tokens	BERT, GPT‑2/3/4, T5, LLaMA, all standard language transformers
Absolute sinusoidal positional encoding	Text	Fixed sine/cosine functions of position	Original Transformer, Transformer‑XL (on values), DETR (for images)
Absolute learned positional embedding	Text	Trainable vector per position	BERT, GPT, GPT‑2
Rotary Position Embedding (RoPE)	Text	Multiplicative rotation of query/key by position‑dependent angle	LLaMA, GPT‑NeoX, PaLM, Mistral, Falcon
ALiBi	Text	Adds a static, non‑learned linear bias to attention scores based on distance	Some GPT‑style models (e.g., BLOOM with ALiBi option)
Relative position bias (learned scalar per relative distance)	Text	Bias added to attention scores before softmax	T5, Transformer‑XL
Segment / token type embeddings	Text	Learned vector distinguishing sentence A vs. B	BERT, XLNet
Patch flatten + linear projection	Image	Split image into patches, flatten, project via a linear layer	ViT, DeiT, BEiT, MAE, SimMIM
2D sinusoidal positional encoding	Image	Sinusoidal encoding of row and column indices	DETR, some ViT implementations
Learned 2D positional embedding	Image	Trainable embedding per (row, col) patch position	ViT (original), MAE
Relative 2D position bias	Image	Learned bias based on relative 2D coordinates	Swin Transformer
CNN feature map tokens	Image	Feature vectors from a CNN backbone treated as input tokens, projected to d	DETR, early ViT hybrids
Pixel‑as‑token embedding	Image	Raw pixel intensities (0–255) mapped to learned embeddings + 2D position	iGPT
Spectrogram patch embedding	Audio	Patches of mel spectrogram flattened & linearly projected	Audio Spectrogram Transformer (AST)
CNN feature encoder + quantized codebook	Audio	Raw waveform → conv layers → discrete units from codebook	Wav2Vec 2.0, HuBERT, WavLM
3D tubelet patch embedding	Video	Spatio‑temporal patches (tubes) flattened & projected linearly	ViViT
Factorised spatial‑temporal embedding	Video	Separate spatial patch embeddings per frame + temporal position encoding per patch index	TimeSformer
Mini‑PointNet patch embedding	3D Point Cloud	Group points into patches, embed with shared MLP, add patch‑center positional encoding	Point‑BERT, Point‑MAE
Laplacian / Random Walk positional encoding + node projection	Graph	Node features projected; structural PE added	Graphormer, SAN, GRPE‑based transformers
Sub‑series patching + linear projection	Time Series	Univariate/multivariate series split into patches, then projected	PatchTST
Feature tokenizer (numerical × weight + categorical embedding) + column embedding	Tabular	Each numerical feature multiplied by a learned vector; categorical feature embedded; column ID added	FT‑Transformer, TabTransformer
Byte‑level embedding	Text	Directly embed raw UTF‑8 bytes via a small embedding table	ByT5, CANINE
Object query embeddings (learned)	Image (Detection)	A set of learned vectors interact with encoder output via cross‑attention, used as input to decoder	DETR (decoder queries)
Cross‑attention embedding via latent array	Multimodal	A fixed‑size array of learned latents queries raw input (pixels, audio, etc.) to produce tokens	Perceiver, Perceiver IO



