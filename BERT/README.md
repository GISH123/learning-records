我的筆記：
evolving process :  
RNN -> Seq2Seq -> With Attention -> Transformer -> BERT  
RNN : https://www.youtube.com/watch?v=UNmqTiOnRfg  

## Seq2Seq with Attention : 
https://jalammar.github.io/visualizing-neural-machine-translation-mechanics-of-seq2seq-models-with-attention

(1)Seq2Seq  
Encoder & Decoder  
Encoder : a series of RNN  
Decoder : a series of RNN  
One Context vector to feedforward without recording it(RNN's Hidden State)  

(2) With Attention   
Recording Encoder's every step's Hidden State   
Then compute a Context Vector for Decoder using these states(with one Decoder Hidden State)  
then feed Context Vector into Decoder  (the Decoder works the same as before, and output word vectors)  



### Seq2Seq with Attention vs Transformer:  
Transformer no longer uses RNN, but uses Self Attention(Both are alike, solves problem mainly for context, need to know which word are relate to other words)  
Self Attention is better at figuring out the relative words  
Because RNN has a shorter memory  (vs ELMo, LSTM Based)  


## Transformer : 
https://jalammar.github.io/illustrated-transformer/  

Input : word embeddings  
6 Encoder + 6 Decoder  
then Linear + Softmax    
Output : Probability Distribution of word indice

Encoder : Self Attention + Feed Forward Neural Network(FFNN)  
Decoder : Self Attention + Encoder-Decoder Attention + Feed Forward Neural Network(FFNN) 

Self Attention (8 heads, meaning 8 Query Key Value sets):  
"Query" + "Key" + "Value"
(1)compute score vector(Each "Query" multiply multiple "Key"s and sum them all, then divide by square root of dimension, then softmax)  
(2)compute "Value" * those softmax   
(3)Sum (2) to produce z vector  

Positional Encoding(Adding a vectors before embeddings enter the encoder)  

Encoder-Decoder Attention( on Decoder):  
Takes Input from top Encoder outputs(K and V vector, dont know what?)   
helps the decoder focus on appropriate places in the input sequence  

## BERT(need further investigation) :  
https://jalammar.github.io/illustrated-bert/  
from ELMo(LSTM, bi-directional) to BERT(Transformer with masks)  
  
Could we build a transformer-based model whose language model looks both forward and backwards?(in the technical jargon – “is conditioned on both left and right context”)?  
BERT uses masks to solve the problem  


