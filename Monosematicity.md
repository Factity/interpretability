
In the previous sections we have seen the phenomenon of superposition.  We have seen both the positive and negative effects of the superposition.

As the dimensions of the features grows larger sparsity grows rapidly, distances become less informative. 

![[Excalidraw/Pasted image 20260722143150.png]]

the volume of the latent space grows larger exponentially. The internal states cannot be understood unless they are decomposed into independent components. 
![[Excalidraw/Pasted image 20260722151016.png]]


The meaning of the concept of local neighborhood $\epsilon$ becomes less informative. It becomes a lot more interpretable when it is just one layer attention only models but as the size grows and MLP block is added it becomes almost impossible  to break it down into interpretable features. 


![[Excalidraw/Pasted image 20260722164401.png]]




So the natural question arises. How do we approach breaking down the MLP block into to understand what goes inside the model. 

In the previous sections we have covered simpler architectures with one or 2 layers and looked at induction heads inside the [transformers](https://factity.github.io/safe-ai/interp_test) .  we have exclusively focused on the attention blocks we broke them down into one layer attention blocks, two layer attention blocks and looked at how bigram statistics emerged. When it comes to MLP block it becomes impossible to break them down in this structure because the MLP is an actual traditional neural net. All parts of the layers matter to put this simply if we just took one layer depth the model will not predict well. we need all the different layers to get the needed performance to make a more accurate prediction. Fortunately traditional neural nets have established frameworks for interpretability and large body of work for all types like CNN's, RNN's, GAN's etc. 

Our objective is to break down the 



![[Excalidraw/Pasted image 20260722181138.png]]]

We mapped particular data points to the network and 





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




















