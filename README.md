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
> 
> 3. __Back-propagating through the trained RNN model to predict the tags from the predicted tag-sets:__ In the previous step, we predicted the tag-sets of the words using the input sequences of tag-sets for corresponding words. After this, we will use the predicted tag sets to predict the individual tags for words 'f' previous to the current word. the last step and this step together, let's us use the context of sequence of words coming before and after a particular word. Figure-2 represents the process.

While this approach was very thorough and complex, we decided to use this approach, but with slight modifications. For our approach, we did not back propagate through the trained RNN for second training phase, but predicted the tags from tag-sets in the first attempt only. This removed the context of words coming after a particular word, while predicting its POS tag. 

On the other hand, we did not face any uncertainity on what value of 'f' to be chosen, which as described in the research paper further, had a very great impact on the accuracy of model. We will not go in that much detail and explain the comparision of our implementation results with the results of the research paper implementation. The implementation documentation of our approach can be understood in the [Jupyter notebook](https://github.com/HardySLAYS/POS-tagging-using-RNN/blob/main/final_project.ipynb) itself. You can go through it first.

The structure of RNN model we trained is provided below.

## Figures:
![fig1](https://github.com/HardySLAYS/POS-tagging-using-RNN/blob/main/pics/fig1.png)
<p align="center">Figure-1</p>


![fig2](https://github.com/HardySLAYS/POS-tagging-using-RNN/blob/main/pics/fig2.png)
<p align="center">Figure-2</p>

![rnn model](https://github.com/HardySLAYS/POS-tagging-using-RNN/blob/main/pics/rnn.png)
<p align="center">Structure of RNN model</p>

## Comparision of our implementation with research papers methodology:
Overall, the accuracy shown in research paper on Penn Trebank's POS tagged dataset was about 92%, which was very near to the traditional Hidden Markov Model's accuracy. While the implementation we had done gave a shocking accuracy of about 96.8% for the same dataset. So, what went wrong? One of the reasons we could deduce was the fact that they over-considered the context of nearbywords while underestimating the context of the current word itself. Another one was that the indirect prediction of tags in two step process seemed to have opposite action from the expectation, and backfired while predicting the POS tags. Hence, we can say with surity that a simple model is a good model in this case.

## Bonus: Praising the creativity of intution:
One mentionable thing, which we all considered very beautiful as well as meaningful was the conversion of converting the words into corresponding tag-sets. Though there are some fatal flaws regarding this approach, but can we just take some time to be amazed at the beauty of this approach :heart_eyes::heart_eyes:. The down-side that should really be mentioned is that after the initial training we are bounded for considering the words with some probable tags only. This generates two problems: first is that the words is considered to have tags none other than the mentioned tags here, and second is that for words that are not having a corresponding tag set from the training data-set, will be considered an unknown word and its prediction can go totally wrong.

## Prolouge
This project was a team effort, and made for the submission of our 6th semester project submission for the course of Pattern Recognition. My team members that helped me a lot were [Yashwant Meena](https://github.com/pAge444) and [Himanshu](https://github.com/HardySLAYS). I would also like to thank my mentors and professor, who introduced and guided me towards world of Pattern recognition, and made me fall a little in love with Machine learning.

If you like the project, please star it and if you would like to contribute, fork the repo and create a pull request.

Adios.

---
