# POS-tagging-using-RNN
A simple Jupyter script to implement a POS tagger using Recurrent Neural Networks.

## INTRODUCTION
Part-of-speech (POS) tagging is a popular Natural Language Processing process which refers to categorizing words in a text (corpus) in correspondence with a particular part of speech, depending on the definition of the word and its context. It is widely used as a bsic pre-proccesing in various advanced NLP problems, such as Named-entity recognition, sentence context recognition, mood recognition and text-to-speech conversion, just to name a few.

While the POS tagging problem is generally solved using [Hidden Markov Model](https://en.wikipedia.org/wiki/Hidden_Markov_model), in recent years, a general approach of using [Reccurent Neural Networks](https://en.wikipedia.org/wiki/Recurrent_neural_network) to solve this problem has emerged. This has increased the accuracy of POS tagging upto a great extent, and introduced a new dimension of flexibility for addition of context in the model.

This project is based on the review/implementation of the research paper ["Part-of-speech tagging with recurrent neural networks"](https://ieeexplore.ieee.org/abstract/document/938396), which was published in IJCNN'01. We have tried to implement the methodology described in the research paper to understand and compare a small intutive that we had regarding this research paper.

## OUR INTUTIVE OF THE RESEARCH PAPER
For our intutive of the research paper, we have to first explain the methodology described in the research paper.
> ## Methodology:
> 
> The methodology described in the research paper can be understood as a three-step process:
> 1. __Converting the sequence of words into sequence of tag-sets:__ The first step was to pre-process the data given, that is the input sentences, or sequences of words. Each word was defined as a set of probable tags, called the ambiguity class of the word, and it was done by checking for all of the occurences of words and grouping all of the corresponding tags assigned to the word in each case. We will address the Ambiguity class as Tag-sets only. After converting all the words into tag-sets, all the sequences of Words are converted into sequences of tag-sets.
>   What this does is that it reduces the computational complexity of the problem exponentially. this is because, while there could be an infinite amount of different words, the amount of tag-sets (which is generally just the combination of every tag, can be calculated by getting the power set of tags) is limited to a very small number, reducing the computations.
> 
> 2. __Training the model to predict probable tag-sets of each sequence of inputs:__ Now, each sequence of input is a tag-set, which will be used to predict the tag-sets of the words(defined by a certain tag-set) 'f' words after the current tag-set. In laymen language, if 'f' is 2 and you are currently at 3rd word, you will predict the probable tag-set of the (2+3 = 5th) word. Figure-1 explains the process of using RNN for this. 

