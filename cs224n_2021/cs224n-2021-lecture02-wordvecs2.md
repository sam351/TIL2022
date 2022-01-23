
# Lecture 2: Word Vectors, Word Senses, and Neural Network Classifiers

## 1. Review: Main idea of word2vec
* Initialize random vectors for each word → Predict surrounding words using center word, or vice versa
* Learning is done by Updating vectors so they can predict actual surrounding/center words better
<br><br><img src="images/lecture02_img1.png" height="80"> <br><br>
* `Word2vec` is "`Bag of words`" model - same prediction at each position (ignoring word positions in sentences)
* `Word2vec` maximizes objective function by putting similar words nearby in space

<br>

## 2. Optimization: Gradient Descent
### 1) Gradient Descent
* `Gradient Descent` : learning method for Word2vec - algorithm to minimize objective function $J(\theta)$ by changing $\theta$
    #### (1) Initialize random vectors for each word
    #### (2) Calculate gradient of $J(\theta)$
    #### (3) Take small step in the direction of negative gradient
    #### (4) Repeat (1)~(3)
    <br><img src="images/lecture02_img2.png" height="300"><br>

### 2) Stochastic Gradient Descent
* **Problem** - Original $\nabla_{\theta}J(\theta)$ is very 
expensive to compute
    * $J(\theta)$ is a function of all windows in the corpus 
* **Solution** - `Stochastic Gradient Descent` : Repeatedly sample windows, and update after each one, or each small batch
<br><br><img src="images/lecture02_img3.png" height="80">

<br>

## Word2vec algorithm family: More details

### 1) Two model variants of `Word2vec`
* `Skip-grams (SG)` : Predict context (“outside”) words (position independent) given center word
* `Continuous Bag of Words (CBOW)` : Predict center word from (bag of) context words

### 2) Negative sampling
* `Negative sampling` : training `binary logistic regressions` for a `true pair` (center word & context word) versus several `noise pairs` (center word & random words)
<br><br><img src="images/lecture02_img4.png" height="60"><br><br>

    #### (1) Take k `negative samples` (using word probabilities)
    * Sample with $ P(w)=U(w)^{3/4} ÷ Z $, the unigram distribution $U(w)$ raised to the 3/4 power
    #### (2) Maximize probability that real outside word appears, minimize probability that random words appear around center word


<br>

## 3. Why not capture co-occurrence counts directly?
### 1) Basic concept of `co-occurrence matrix`
* Another method to get word vectors
* the matrix of counts of **how frequently words occur with each other**
* representation of words as co-occurrence vectors
* 2 options of `co-occurrence matrix` : **Windows VS Full Document**
    * `Windows` - captures some syntactic and semantic
information (locality & proximity)
    * `Full Document` (ex. paragraphs, pages, documents) - Word-document co-occurrence matrix will give general topics leading to `Latent Semantic Analysis`

    <br><img src="images/lecture02_img5.png" height="200"><br>

### 2) Problems & Solutions
* **Problem with `co-occurrence matrix`** : Very high dimension & require lots of storage & Very high sparsity
    * Vectors increase in size with vocabulary
    * Subsequent classification models have sparsity issues → Models are less robust
* **Solution** : `Dimensionality Reduction` (Low-dimensional vectors)
    * Store most of the important information in a fixed, small number of dimensions (a `dense vector`)
    * Usually 25–1000 dimensions, similar to `word2vec`
    * `Singular Value Decomposition` : Decompose a matrix $X$ into three matrices $U, \Sigma, V^T$
    * We can get lower dimensional matrix than original `co-occurrence matrix` by rataining only *k* singular values 

    <br><img src="images/lecture02_img6.png" height="250"><br>

* **Problem with `SVD`** : Running on raw counts doesn’t work well
    * Mathmatical assumption of `SVD` : normally distributed errors
    * However, `function words` (ex. the, he, has) are too frequent in `co-occurrence matrix`
* **Solution** : **Scaling the counts** in the cells can help a lot
    * **Log** the frequencies
    * **Cap** the frequencies : $ min(X,t) $ , with $ t ≈ 100 $ 
    * **Ignore & Remove** the `function words`
* Example case of scaled vectors : `COALS` model (Rohde et al. ms., 2005)

<br>

## 4. Towards GloVe: Count based vs. direct prediction

<br>

## 5. How to evaluate word vectors?

<br>

## 6. Word senses and word sense ambiguity

<br>

## 7. Classification review and notation

<br>

## 8. Neural Network Classifiers



