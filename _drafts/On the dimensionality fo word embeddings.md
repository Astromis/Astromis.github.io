I guess every one who faced with word embeddings ask heself how to chose dimensionality. For me it is natural question because I don't like the open parametrs without some guides for correct chosing because my head is attacked by the question: "Are you sure the parameters you've chosen are as best as possible?". Maybe I'm a paranoic, but think yourself the not optimal parameters might damage you system in some aspect.

Fortunatly, the group researchers from ... tackled this problem and share the theoretical fundament and practical tool for figuring out the optimal embedding dimension. No more 300 dimension!

They starts with two statements:

First, let's make convinience about embeddings definition. The embeddings(of wods in out case) is assumed to be the resul of implicit or explicit matrix factorization in this general way: ... . As you might remember, the explicit result is obsearved in LSA algorithm wheares implicit is word2vec algorithm. If you wonder about the last statement, check this paper where Goldenberg proves that word2vec is equal to factorization of a shifted PMI. Proposed by him the GloVe schemme was designed directly in this manner. In GloVe the coocurance matrix is used. Not all schemmes of getting the embeddings are matrix factorization, for example, derived from language model like BERT and ELMo, or it haven't proved yet.

The second is the fact that word embeddigs defined above are unitary-invariant. It means that two embeddings are essentially identical if one can be obtained form the other by performing a unitary operation like rotation

(It is unclear how PIP relates with dimensionality)

Take these two statements, the authores proposed the loss funciton that can measure the goodness of word embeddings called Pairwase Inner Product (PIP) loss.

So now let's establish the task. We want to get the optimal embedding dimension. To do this, suppose we have an ideal basic matrix for factorization M(for example, it can be PMI matrix) and will call it signal matrix. So it produces an ideal embeddings E. However, we live in real word and we can only estimate M empirically from dataset that drives us to M~= M + Z where Z is a nose. From this matrix we obtain the trained embeddings E~. We need to get the E~ that would be as near as possible to E and the PIP loss, that is affected by k(dim), will be our metric.

Authors shows how they tackle this problem by representing it as bias-varions trade-off. This trade-off lies in signal-to-noise ratio between ideal and estimated matrices. Me can derive though experiment: 

So far, in reality we only have the estimated matrix M~ that is noised version of ideal signal matrix. It has some high n dimensionality. We want to produce dense embeddings with k dimension such that  k (<<) n under condition having more useful signal and less noise. So we'va establish the problem how to find the optimal signal-ro-noise ratio. Authors shows how they tackle this problem by representing it as bias-varions trade-off between ideal and estimated matrices.

Theirs main theorem is next:


From the previos statement goes that we need minimize the PIP loss by selecting the k* and so it will be an optimal dimensionality. 
