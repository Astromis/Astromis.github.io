Recently on work, I had to solve a quite abstracted task that lies in sentence compression. One specific of this task is a lack of data which means no neural networks and other deep learning approaches. I started serving Google Scholar and found many interesting things. I discovered for myself a sentence fusion domain. It was incredible because I have been thinking about exact task for a long time and just didn't know about it. I don't know whu I didn't just google it. 

Back to the sentence compression. Until about 2002 there is many papers authors of that explores rule based approach. It obviuosly is not our path. So after this year papers began to appear where is used probabilistic approach. The core of these papers is syntactic parsing of sentence. That is why my previous post is about UDPipe and its syntactic parser. Because of real lack of data I was finding something unsupervised and was lucky. I found the paper of 2008 year Dependency Tree Based Sentence Compression by Katja Filippova in which author proposes a completly unsupervised approach to comress the sentence. In two words, the compression is done by deleting words. In the paper is approached as pruning some edges from dependency tree of sentence. At first we obtain a sentence tree, after that apply to it several transofrmation, having done which we are getting new structre that is called sentence graph. Applying this to relatively large corpus and extract from this some probabilities, we obtain the model from which can be obtained the shorter sentences with integer linear programming technique.

We start with getting a dependency tree of the sentence. According to the paper we need to do some change to turn on the tree into the graph.

1) First of all, we make the root node explicit and connecnt to it all verbs in the sentence pointing edges as 's'. Also, we remove all auxiliary edges and memorize such grammatical properties as voice, tense or negation for verbs.

2) Remove prepositional nodes and place them as labels on the edge of respective noun.

3) Decompose the conjoined elements and attach them to the head of the first element preserving attributes of link. This rule is not applyed for the verbs.

Now I get some explanations:

For the first one, let's assume that we have next sentence:

He said they have to be held in Beirut.

In that sentence there are two clauses, basic grammar structre common consisting of a subject (noun) and verb.  Main clause is "He said" and a residue part as embedded clause. By default, parsers are rooted only main clause verbs, that would be not so informative like in sentence above. It is obviuos the sentence should be compressed to embedded one. So that, we are rooting all verbs to have possobility of compressing the source sentence to any clause. 

The porpose of the second and third modifications is to make relations between open-class words. It is such words that readily accept new members, like, for English, nouns, lexical verbs, adjectives, and adverbs. "Accept new members" means to append new words that never be in language before. In result of science, for example. Many words in Russian is being borrowed from English because the science speaks on it.

Okey, I hope you are get insight about open-class words. Go ahead. When we consider wheather prune an edge or not, it is make sense to know how important this node for the head is and how informative the depended node is. To ilustrate the sense of second transofrmation, let's look on this sentene from the papre:

After some time, he moved to London.

The dependency parser defines both after and to as preposition, but it is not enogh to decide which preposition should be pruned ('After some time, he moved' is not the main idea). However, direct name give missing information.

At last, decomposing the conjugated elements just gives us more flexibility allowing us pruning any part whiout needing to preserve whole sequence.

Now we are ready to formulte our task as an integer linear programming problem.  Given a transformed dependency tree, we decide which dependency edge to remove. For each edge we assosiate a binary variable.
(variable)
where l is a lable, h is a head and w is a word.

We need to find a subtree which get the highest score of next objective function:

(obj. function)

where P(L|h) is probability if label given word and I(w) is importance of word.
The conditional probability prevent us from removing obligatory dependencies. For example, P(subj|work) is higher then P(with|work). In addition, this is a place why we have to apply prepositional transofrmation - because there are more than one label PP. It allows us to distinguish the diffirence beetwen them in sense of their obligatory.

Now about measuring of word importans. There are many approaches to do that. In the papar is proposed the next formula:

(importance formula)

The second part of formula is quite simple. The first one needs to be explained.

Come back to out clauses. Let's consider the next sentence:

“Mr Field has said he will resign if he is not reselected, a move which could divide the party nationally”.

How many clauses do you see? I see 4. You can also see, that there is a seria of clauses embedded one into another. Intuitively, it seems that the deeper clause is the more semantic content it carry. We can construct a hierarchy of sentence and it going to look like this.

So it makes sense to give words in deeper clauses more importance. The l in the formula is a level of clause its word enters, and N is a count of all clauses in one hieracly. For example, for word said it is 1/4, for reselected is 1. For all words in SBAR it will be one because it is another hierackly with one level.
Unfortunatly, a couldn't do this logic in my programm because UDPipe has another format insted of Stanford parser, that uses in paper. I think it could be done I don't have enogh knowladge.

So far, previously collected the probabities and corpus data, we are ready to optimization. For doing ILP we need to define some constrains, two for us. First constrains will be stuctural and ensure that the preserved dependencies result in a tree. 1.a ensures that each word has one head at most, 1.b ensures the connectivity in the tree and 1.c restrict the size of the resulting tree to alpha words. This is a core.
For my mind it was hard to understand the meaning of these forula because I'd never used with ILP so I add some comments.
Let's start from first.
For each  word in sentence we need to consider all heads and get ensured that it has only one. It can be consider as sum through heads that might be got as a result of optimization. For some word it cold be two out more heads. So if the sum is one or zero it means that the words indeed has no more then one head and our constrains is secured.
For the second one the idea is next. Let's get a word...
The third is simple. It says that sum of word can't exceed the constant alpha.

The second confition I could understand yet because of lack of my knowladge in English grammar. Even though I could, as I mention above UDpipe can't get the information about clauses (or I don't undestand something). Althoy my realisation works quate good without it, I'll back to it in near time.

After we have completed the optimization, we need to get a sentence from the pruned graph or linearize the graph. According to the paper we simply present words in order as a source sentence. It works not for all languages like for German, native language of authors. In Russian we can freely swap the words without loss of sense.

So far, the algothim is over. Here you can see the results of the algorithm.

The undestanding of this algorithm ws quate difficult because it uses 'old' NLP with linguistic features. I addicted to consider an NLP problem mosly in end-to-end domain. I heard some opinions that probably NLP will louse independence because of that. Anyway, I know that this framework is used for along time. I saw several papers about sentence fusion based on this. It make sense because it's too expensive to create manually the dataset for neural networks due to required amount of data. So I look at this framework more presicly and code I've writen will help with my futher experements.

