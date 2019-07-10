--- 
layout: post 
author: Astromis 
title: Discover the UDpipe
use_math: false
--- 

Recently, I had to get syntactic dependancy tree for my experements with sentence comprssion. There is one trouble - for russian language is pretty hard to find a good parser. Of course, there is syntax net fro google, but I didn't want to dive into problems with dependances, version incopatibility and so on. So, I just was searching more simpler. And I've found. It is Universal Dependency Pipeline or UDPipe by Czech developer. This is c++ written framework that allows tokenize, tag and parse text. All you need is pre-treined model that for some languages can be downloaded or trained by yourself. This is sounds like a doubt, but don't worry - to learn this model is pretty simple. Moreover, this framework can be runned as REST web server or library(the executble setting is running by default). SWIG makes it possibly to wrapp up code for other languages such as Python, Java, R, Prel.

So at first, we need to download source codes through git:
```
git clone https://github.com/ufal/udpipe.git
```
Next, we go to ./src directory and run make
```
cd udpipe
make
```
After that, we will obtain udpipe executble file.

Now, we need in model. You can download a pre-trained model pack from [official site]( http://ufal.mff.cuni.cz/udpipe/models). Just check your version and follow the content. It wouldn't be hard.
If there is no model for your language like for Russian, let's try to find data for training [here](https://github.com/UniversalDependencies). Among the repositories you can try to search repo that contains treebank for requaired language as for Russian SynTagRus.

Download it
```
git clone https://github.com/UniversalDependencies/UD_Russian-SynTagRus.git
```
The things in that we have interest is ru_syntagrus-ud-dev(-train -test).conllu This is trebank that dividing to training and testing parts.

Now, to train the UDPipe model tun this command from src directory
```
cat UD_Russian-SynTagRus/ru_syntagrus-ud-train.conllu | ./udpipe/src/udpipe --train rus_model
```
where rus_model is name of file in which model will be seved. So this process take some time, because tolenizer, tagger and parser are training.

It is good so far, but let's wrapp up this with Python just to speed up protoryping process. You can use pip or maniually compile this for both Python2.7 and Python3+. 
For automatical installation just type
```
pip install ufal.udpipe
```
For maniually compiling go to downloaded git repo in ./repo/bindings/python directory and just run
```
make PYTON_INCLUDE=/path/to/python/include
```
What does this mean? You have to specify where python includes are. If you are using system python, make sure that you have installed python-dev(python3-dev) packege and type
```
make PYTHON_INCLUDE=/usr/include/pythonX.Xm/
```
Why is it important? I don't know yet, but empirically, if you are using anaconda, you should specify includes containing whithin anaconda, for example (Let's assume, that anaconda3 have been installed in user home directory)
```bash
make PYTHON_INCLUDE=/home/user_name/anaconda3/include/pythonX.Xm
```
If you didn't do this, it woulde cause problems with using of this.

Finally, you'll get some files and trap is that make file doesn't have an install option. I don't understand yet how to correctly add all files in right places by hand, but in place in which you have compiled package all will work well.

Author provides two scripts as exapmles of using udpipe. One of these bindings/python/exapmes/udpipe_model.py describes usefull class that makes easy to use to work with library. Here is an example of using directly from a file:

```python 
model = Model('rus_model')
sentences = model.tokenize("Мама мыла раму.")
for s in sentences:
  model.tag(s)
  model.parse(s)
conllu = model.write(sentences, "conllu")
print(conllu)
```

The whole code you can see you own it is pretty easy and clearly.

Here a couple of phrases about data representation. UDpip uses an CoNLL-U format that for syntax representation looks like that
```
# sent_id = 1
# text = They buy and sell books.
1   They     they    PRON    PRP    Case=Nom|Number=Plur               2   nsubj   2:nsubj|4:nsubj   _
2   buy      buy     VERB    VBP    Number=Plur|Person=3|Tense=Pres    0   root    0:root            _
3   and      and     CONJ    CC     _                                  4   cc      4:cc              _
4   sell     sell    VERB    VBP    Number=Plur|Person=3|Tense=Pres    2   conj    0:root|2:conj     _
5   books    book    NOUN    NNS    Number=Plur                        2   obj     2:obj|4:obj       SpaceAfter=No
6   .        .       PUNCT   .      _                                  2   punct   2:punct  
```
Here is 10 columns named 
* ID - word index
* FORM - word form or punctuation symbol
* LEMMA - lemma or stem of word form
* UPOS - universal part of speech tag
* XPOS - language specific part of speech tag
* FEATS - list of morphological features
* HEAD - head of the current word, which is either a value of ID or zero (0)
* DEPREL - universal dependency relation to the HEAD (root if HEAD = 0) or a defined language-specific subtype of one
* DEPS - enhanced dependency graph in the form of a list of head-deprel pairs
* MISC - any other annotation.

More about format you can found on [official site](http://universaldependencies.org/format.html)

Using HEAD and ID fields we can build a dependancy tree. There are several servicies that can drawn the tree, [for example](http://www.let.rug.nl/kleiweg/conllu/)

![Here is a screenshot of the tree](/assets/images/syntax_tree_example.png "Example of tree visualisation")

[This repo](https://github.com/EmilStenstrom/conllu) contains a nice and light python library that can give you a way to manipulate CoNLL-U data.

Links

http://wiki.apertium.org/wiki/UDPipe

Official site:
http://ufal.mff.cuni.cz/udpipe

CoNNL-U format:
http://universaldependencies.org/format.html

Repo with treebanks
https://github.com/UniversalDependencies
