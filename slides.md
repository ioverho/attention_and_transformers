---
# You can also start simply with 'default'
theme: neversink
neversink_slug: "Attention & Transformers"
author: Ivo Verhoeven

# Export settings
exportFilename: "attention_and_transformers_2"
export:
  format: pdf
  timeout: 30000
  withClicks: true
  withToc: true

# Code block settings
lineNumbers: false

# Markup settings
colorSchema: light
aspectRatio: "16/9"
favicon: 'https://cdn.jsdelivr.net/gh/slidevjs/slidev/assets/favicon.png'

# Default slide settigns
defaults:
  hideInToc: true
  color: light

# Cover layout options
layout: intro
hideInToc: true
color: dark
---

# Attention & Transformers

[Ivo Verhoeven](mailto:i.o.verhoeven@uva.nl) | Advanced Topics in Computational Semantics

<!-- Presentation slides for developers -->

---
layout: two-cols-title
---

:: title ::

# About Me

:: left ::

<figure style="display: flex; justify-content: center;height: 100%">
  <img src="/about_me.jpg" style="position: relative;overflow: hidden;border-radius: 100%;width: 75%;">
</figure>

:: right ::

<div class="ns-c-tight">

- 2017 - 2020: BSc. Liberal Arts & Sciences

<br>

- 2020 – 2022: MSc. AI at University of Amsterdam

  - Thesis on meta-learning, morphology and translation

  - Took ATCS in 2021

<br>

- 2022 - ???: PhD at ILLC

  - Misinformation detection and generalisation with Katia Shutova

</div>

---
layout: two-cols-title
columns: is-6
align: l-lt-lb
---

:: title ::

# Vaswani et al.: Attention is All You Need

:: left ::

- Introduces the Transformer architecture in late 2017
  	- Google Brain/Google Research collab

<v-click>

- Paper currently has **169 248** citations

    - Or **~64 citations a day**

</v-click>

<v-click>

- Number of citations is only accelerating

<figure>
  <img src="/vaswani_et_al_citations_rate.svg">
</figure>

</v-click>

<v-click>

- Most cited paper ever has **233 829** citations
  ```
  Lowry et al. (1951) Protein measurement with
  the folin phenol reagent.
  ```

</v-click>

:: right ::


```
Vaswani et al. (2017). Attention is all you need. Advances in
neural information processing systems, 30.
```

<figure>
  <img src="/vaswani_paper.png">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-lt
---

:: title ::

# Vaswani et al.: Attention is All You Need

:: left ::

- It's hard to think of an AI area that hasn't been affected by the Transformer
  <div class="ns-c-tight">
  <v-click>

  - **NLP:** Transformer > RNN
    - Seq-to-seq: what it was designed for
    - Classification: encoder-only transformers
    - Generation: decoder-only transformers
  </v-click>

  <v-click>

  - **CV:** ViT > CNN
  - **Multi-modal:** Transformer > different architectures
  - **Speech:** Transformer > CNN
  - **Graphs:** Transformer/Attention > GCN

  </v-click>
  </div>

:: right ::

<figure>
  <img src="/transformer_affected_areas.png" style="width:70%;display: block;margin-left: auto;margin-right: auto;">
</figure>
```
Islam, et al. (2023). A Comprehensive Survey on Applications of
Transformers for Deep Learning Tasks. arXiv:2306.07303.
```

---
layout: side-title
color: dark
side: l
titlewidth: is-4
align: rm-mt
---

:: title ::

# The Transformer

:: content ::

<figure>
  <img src="/transformer_svg.svg">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-lt
---

:: title ::

# Breaking the Transformer into modules

:: left ::

<div class="ns-c-tight">
<v-click>

4. Output
    - <span class="bg-teal-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Softmax</span>
    - <span class="bg-violet-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Linear</span>

</v-click>
</div>

<div class="ns-c-tight">
<v-click>

3. Attention Blocks
    - <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>
    - <span class="bg-lime-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Add & Norm</span>
    - <span class="bg-blue-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Feed Forward</span>

</v-click>
</div>

<div class="ns-c-tight">
<v-click>

2. Embedding
    - <span class="bg-red-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Token Embedding</span>
    - <span class="bg-green-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Positional Encoding</span>

</v-click>
</div>

<div class="ns-c-tight">
<v-click>

1. Tokenization
    - (Not pictured)

</v-click>
</div>

:: right ::

<figure>
  <img src="/transformer_all_chapters.svg" style="width:100%;display: block;margin-left: auto;margin-right: auto;">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-lt
---

:: title ::

# Breaking the Transformer into modules

:: left ::

<div class="ns-c-tight">

4. ~~Output~~
    - <s><span class="bg-teal-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Softmax</span></s>
    - <s><span class="bg-violet-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Linear</span></s>

</div>

<div class="ns-c-tight">

3. Attention Blocks
    - <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>
    - <span class="bg-lime-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Add & Norm</span>
    - <span class="bg-blue-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Feed Forward</span>

</div>

<div class="ns-c-tight">

2. Embedding
    - <s><span class="bg-red-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Token Embedding</span></s>
    - <span class="bg-green-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Positional Encoding</span>

</div>

<div class="ns-c-tight">

1. Tokenization
    - (Not pictured)

</div>

:: right ::

<figure>
  <img src="/transformer_all_chapters.svg" style="width:100%;display: block;margin-left: auto;margin-right: auto;">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-lt
---

:: title ::

# Table of Contents

:: left ::

<div class="ns-c-tight">
<Toc />
</div>

:: right ::

<figure>
  <img src="/transformer_svg.svg" style="width:100%;display: block;margin-left: auto;margin-right: auto;">
</figure>

---
hideInToc: false
layout: section
color: dark
---

# Encoders & Decoders

Text comes in, text goes out

---
title: "Attention Blocks"
hideInToc: false
layout: section
color: dark
columns: is-6
align: l-lt-lt
---

# Attention Blocks

What makes the Transformer what it is --- and where it came from

---
hideInToc: false
layout: side-title
color: dark
side: l
titlewidth: is-5
align: lm-mt
---

:: title::

## <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: content ::

<figure>
  <img src="/transformer_svg.svg" style="width:100%;display: block;margin-left: auto;margin-right: auto;">
</figure>

---
hideInToc: false
layout: two-cols-title
columns: is-6
align: l-lt-lt
---

:: title ::

### Definition & Properties

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Let $\mathbf{V}$ be a matrix of (word) vectors
  - It has a sequence length of $t_{V}$
  - It has a dimensionality of $d_{V}$

<br>

<v-click>

- $\mathtt{Attention}$ is just a matrix product of $\mathbf{V}$ with an attention matrix $\mathbf{A}$
  - $\mathbf{A}$ is a square matrix of size $t_{V}\times t_{V}$
  - It's elements are all between $(0, 1)$
  - It's rows sum to $1$

</v-click>

:: right ::

$${3|all}
\begin{align*}
  &\mathtt{Attention}(?, ?, \mathbf{V})=\mathbf{A}\mathbf{V} \\
  &\quad\mathbf{A}\in(0,1)^{[t_{V}\times t_{V}]} \\
  &\quad\mathbf{V}\in\mathbb{R}^{[t_{V}\times d_{V}]}
\end{align*}
$$

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Definition & Properties

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- The result of $\mathtt{Attention}$ is just a [convex combination](https://en.wikipedia.org/wiki/Convex_combination) of $\mathbf{V}$

$$
\overset{\mathbf{A}}{
  \begin{bmatrix}
    0.6 & 0.1 & 0.3 \\
    0.3 & 0.5 & 0.2 \\
    0.2 & 0.1 & 0.7 \\
  \end{bmatrix}
}
\overset{\mathbf{V}}{
  \begin{bmatrix}
    \phantom{-}2.0 & \phantom{-}1.0 \\
    -0.5 & \phantom{-}2.0 \\
    -1.0 & -0.5 \\
  \end{bmatrix}
}
\begin{matrix}
  \text{\color{red}{I}} \\
  \text{\color{green}{am}} \\
  \text{\color{blue}{Sam}} \\
\end{matrix}
$$

<v-click>

$$
=
\begin{bmatrix}
  0.6 * \text{\color{red}{I}} + 0.1 * \text{\color{green}{am}} + 0.3 * \text{\color{blue}{Sam}} \\
  0.3 * \text{\color{red}{I}} + 0.5 * \text{\color{green}{am}} + 0.2 * \text{\color{blue}{Sam}} \\
  0.2 * \text{\color{red}{I}} + 0.1 * \text{\color{green}{am}} + 0.7 * \text{\color{blue}{Sam}} \\
\end{bmatrix}
$$

</v-click>

:: right ::

<figure style="position: relative;top: 0;left: 0;">
    <img v-after.hide src="/word_vectors.svg" style="position: relative;width: 400px;top: 0;left: 0;">
    <img v-after src="/adjusted_word_vectors.svg" style="position: absolute;width: 400px;top: 0%;">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Definition & Properties

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

<br>

<Admonition title="Convex Combination" color="light" width="100%" icon="mdi-pencil">

The elements of $V^\prime$ will lie inside the convex hull of all of the elements in $V$

</Admonition>

<v-click>
<Admonition title="Permutation Equivariance" color="light" width="100%" icon="mdi-pencil">

The elements of $\mathbf{V}^\prime$ are *equivariant* to a change in the order of the columns of $\mathbf{A}$ and the rows of $\mathbf{V}$

</Admonition>

- Attention does not care about word order
  - 'I am Sam' ~ 'Sam I am'

</v-click>

:: right ::

<figure style="position: relative;top: 0;left: 0;">
    <img v-after.hide src="/attention_as_convex_combination.svg" style="position: relative;width: 400px;top: 0;left: 0;">
    <img v-after src="/attention_permutation_equivariant.drawio.svg" style="position: absolute;width: 450px;top: 0;left: 0;">
</figure>

---
layout: default
---

### Definition & Properties

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

<br>

So is $\mathtt{Attention}$ just a linear map?
  - Not quite

<br>

Linear maps are:

<div class="ns-c-tight">
<v-clicks>

- Inflexible in terms of sequence length
- Parameter inefficient
- Invariant to the input content

</v-clicks>
</div>

---
layout: two-cols-title
columns: is-6
align: l-lt-lt
---

:: title ::

### Definition & Properties

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

<div class="ns-c-tight">

- Let $\mathbf{V}$ be a matrix of **value** vectors
  - It has a sequence length of $T_{V}$
  - It has a dimensionality of $d_{V}$

- Let $\mathbf{K}$ be a matrix of **key** vectors
  - It has a sequence length of $t_{V}$
  - It has a dimensionality of $d_{K}$

- Let $\mathbf{Q}$ be a matrix of **query** vectors
  - It has a sequence length of $t_{Q}$
  - It has a dimensionality of $d_{K}$

<div v-click>

- Let $f(\mathbf{Q}, \mathbf{K})$ be some kernel function
  - Read: similarity function

</div>

</div>

:: right ::

$${3,4,5|all}
\begin{align*}
&\mathtt{Attention}(\mathbf{Q}, \mathbf{K}, \mathbf{V})=\underbrace{\mathtt{softmax}\left(f\left(\mathbf{Q}, \mathbf{K}\right)\right)}_{\mathbf{A}}\mathbf{V} \\
&\quad\mathbf{A}\in(0,1)^{[t_{Q}\times t_{V}]} \\
&\quad\mathbf{V}\in\mathbb{R}^{[t_{V}\times d_{v}]} \\
&\quad\mathbf{K}\in\mathbb{R}^{[t_{V}\times d_{k}]} \\
&\quad\mathbf{Q}\in\mathbb{R}^{[t_{Q}\times d_{k}]} \\
\end{align*}
$$

---
hideInToc: false
layout: two-cols-title
columns: is-6
align: l-lt-cm
---

:: title ::

### Non-Transformer Examples

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

<div class="ns-c-tight">

- $\mathbf{V}$ contains information
- $\mathbf{K}$ contains information about information (i.e, metadata)
- $\mathbf{Q}$ contains metadata about what we want from $\mathbf{V}$
- $f(\mathbf{Q}, \mathbf{K})$ is high when $\mathbf{Q}$ is similar to $\mathbf{K}$

<br>

<div v-click>
<Admonition title="Soft lookup" color="light" width="100%" icon="mdi-alpha-e-box">

We want to find a textbook about NLP in the library ($\mathbf{V}$). We search for titles ($\mathbf{K}$) with "jurafsky" and "martin" as authors ($\mathbf{Q}$). The computer returns books with similar titles ($f$)

</Admonition>
</div>

</div>

:: right ::

<div v-after>
<figure>
  <img src="/retrieval_example.png" width="300px">
</figure>
</div>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Non-Transformer Examples

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- $f(\mathbf{Q}, \mathbf{K})$ is high when $\mathbf{Q}$ is similar to $\mathbf{K}$
- The output of $f$ must a matrix of size <br> $\mathbf{A}\in(0,1)^{[T_{Q}\times T_{V}]}$

<v-click at="1">
<Admonition title="Nadaraya-Watson Kernel Regression" color="light" width="100%" icon="mdi-alpha-e-box">

We have some sequence of values <br> $\mathcal{D}=[(1.36, 1.79), (3.40, -1.77) \ldots, (6.05, -2.17)]$

We want to predict a new sample at $x=4.25$

We compute the negative Euclidean distance of our new sample with all training samples ($f$). We normalize the outputs to lie between $(0,1)$

We compute our predicted value as the mean of the seen values, weighted by the computed similarities

</Admonition>
</v-click>

:: right ::

<div>
  <figure>
    <img v-click="2" src="/kernel_regression_weights_matrix.svg">
  </figure>

  <figure style="position: relative;top: 0px;left: 0;">
    <img v-click="[1, 3]" style="position: absolute;top: 0px;left: 0;" src="/kernel_regression.svg">
    <img v-click="[3, 4]" style="position: absolute;top: 0px;left: 0;" src="/kernel_regression_weights.svg">
    <img v-click="4" style="position: absolute;top: 0px;left: 0;" src="/kernel_regression_prediction.svg">
  </figure>
</div>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Non-Transformer Examples

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- The $\mathbf{Q}$ and $\mathbf{V}$ do not need to have the same sequence length
- Attention output will always have sequence length $T_{Q}$

<v-click at="1">

<Admonition title="Bahdanau et al. Attention" color="light" width="100%" icon="mdi-alpha-e-box">

In Neural Machine Translation (NMT) the encoder generates a representation of the input language

The decoder needs to generate in a target language

Token in input language != token in output language

Solution: have each token in the target language ($\mathbf{Q}$) attend back to all input language tokens ($\mathbf{K}$, $\mathbf{V}$)

</Admonition>

```
Bahdanau, Cho & Bengio (2014). Neural machine translation
by jointly learning to align and translate.
arXiv preprint arXiv:1409.0473.
```
</v-click>

:: right ::

<v-click at="1">
  <figure style="position: relative;">
    <img src="/bahdanau_attention.png" style="width: 350px">
  </figure>
</v-click>

---
layout: two-cols-title
columns: is-6
align: l-lt-c
hide: true
---

:: title ::

### Non-Transformer Examples

##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- The attention matrix can be interpreted as a weighted adjacency matrix in a fully-connected graph where tokens are nodes

<v-click at="1">
<Admonition title="Graph Attention" color="light" width="100%" icon="mdi-alpha-e-box">

We need to compute a represenation for node $\mathbf{h}_{i}$.

We get all representations for $\mathbf{h}_{j}\in \mathcal{N}(h_{i})\cup h_{i}$ ($\mathbf{K}$), and compare these to $\mathbf{h}_{i}$ ($\mathbf{Q}$).

We then compute the representation of $h_{i}$ from the attention weighted average of all nodes in $\mathbf{h}_{j}\in \mathcal{N}(h_{i})\cup h_{i}$.

</Admonition>

</v-click>

:: right ::

<v-click at="1">

<figure>
  <img src="/gat.png">
</figure>

```
Bahdanau, Cho & Bengio (2014). Neural machine translation
by jointly learning to align and translate.
arXiv preprint arXiv:1409.0473.
```
</v-click>

---
hideInToc: false
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Attention in Transformers
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Transformer attention uses a scaled dot-product kernel function

  $$f(\mathbf{Q}, \mathbf{K})=\dfrac{\mathbf{Q}\mathbf{K}^{\intercal}}{\sqrt{d_{k}}}$$

- $\mathbf{Q}$ is of size $t_{Q}\times d_{K}$
- $\mathbf{K}$ is of size $t_{V}\times d_{K}$
- Attention matrix is thus of size $t_{Q}\times t_{V}$

:: right ::

$$\mathtt{attention}(\mathbf{Q}, \mathbf{K}, \mathbf{V})=\mathtt{softmax}\left(f(\mathbf{Q}, \mathbf{K})\right)\mathbf{V}$$

<figure>
  <img src="/sdpa_self.drawio.svg" style="width: 350px;">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Attention in Transformers
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Transformer attention uses a scaled dot-product kernel function

  $$f(\mathbf{Q}, \mathbf{K})=\dfrac{\mathbf{Q}\mathbf{K}^{\intercal}}{\sqrt{d_{k}}}$$

- Why scale?
  - Assume the elements in $\mathbf{Q}$ and $\mathbf{K}$ come from *independent* normal distributions:
  $$\mathbf{q}, \mathbf{k}\sim\mathcal{N}(0, 1)$$
  - The [distribution of their dot-product](https://en.wikipedia.org/wiki/Distribution_of_the_product_of_two_random_variables#Independent_central-normal_distributions) is:
  $$\mathbf{q}^{\intercal}\mathbf{k}\sim\mathcal{N}(0, \sqrt{d_{k}})$$
:: right ::

$$
\begin{aligned}
\mathtt{var}\left[\mathbf{q}^{\intercal}\mathbf{k}\right]&=\mathtt{var}\left[\sum_{i}^{d_{k}}q_{i}k_{i}\right] \\
&=\sum_{i}^{d_{k}}\mathtt{var}\left[q_{i}k_{i}\right] \\
&=\sum_{i}^{d_{k}}\mathtt{var}\left[q_{i}\right]\mathtt{var}\left[k_{i}\right] \\
&=\sum_{i}^{d_{k}} 1\cdot 1 \\
&= d_{k}
\end{aligned}
$$

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Attention in Transformers
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Why mask?
  - Currently all tokens are treated equally
  - **Causal masking**: decoder tokens should never attend to future tokens, only to the past
  - **Local masking**: sometimes local attention is all you need


:: right ::

<figure>
  <img src="/causal_masking.png" style="width: 100%;">
  <nobr><a href="https://krypticmouse.hashnode.dev/attention-is-all-you-need" style="font-size: 9pt;">https://krypticmouse.hashnode.dev/attention-is-all-you-need</a></nobr>
  <img src="/efficient_masking.png" style="width: 100%;">
  <nobr><a href="https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/" style="font-size: 9pt;">https://lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/</a></nobr>
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Attention in Transformers
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Where do $\mathbf{V}$, $\mathbf{K}$, $\mathbf{Q}$ come from?

:: right ::

<figure>
  <img src="/sdpa_self.drawio.svg" style="width: 350px;">
</figure>


---
layout: two-cols-title
columns: is-6
align: l-ct-ct
---

:: title ::

### Attention in Transformers
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

**Self-attention**

<figure>
  <img src="/sdpa_self.drawio.svg" style="width: 350px;">
</figure>

:: right ::

**Cross-attention**

<figure>
  <img src="/sdpa_cross.drawio.svg" style="width: 350px;">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Attention in Transformers
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Where do $\mathbf{V}$, $\mathbf{K}$, $\mathbf{Q}$ come from?
  - **Self-attention**: everything comes from the same sequence
  - **Cross-attention**: $\mathbf{V}$, $\mathbf{K}$ come from source sequence, $\mathbf{Q}$ comes from target sequence
  - All components constructed from a projection of the token embeddings
    1. $\mathbf{V}=\mathbf{X}\mathbf{W}_{V}$
    2. $\mathbf{K}=\mathbf{X}\mathbf{W}_{K}$
    3. $\underbrace{\mathbf{Q}=\mathbf{X}\mathbf{W}_{Q}}_{\text{Self-attention}}$ or $\underbrace{\mathbf{Q}=\mathbf{Y}\mathbf{W}_{Q}}_{\text{Cross-attention}}$

:: right ::

<figure>
  <img src="/transformer_svg.svg">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Attention in Transformers
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Even in self-attention, attention matrix is **not** symmetric
  $$
  \begin{aligned}
  \dfrac{\mathbf{Q}\mathbf{K}^ {\intercal}}{\sqrt{d_{k}}}&=\dfrac{\mathbf{X}\mathbf{W}_{Q}(\mathbf{X}\mathbf{W}_{K})^{\intercal}}{\sqrt{d_{k}}} \\
  &=\dfrac{\mathbf{X}\mathbf{W}_{Q}\mathbf{W}^{\intercal}_{K}\mathbf{X}^{\intercal}}{\sqrt{d_{k}}}
  \end{aligned}
  $$

<br>

<Admonition title="Asymmetry" color="light" width="100%" icon="mdi-pencil">

The contribution of token $\mathbf{x}_{i}$ to $\mathbf{x}_{j}$, is **not** the same as the contribution of tokn $\mathbf{x}_{j}$ to $\mathbf{x}_{i}$

</Admonition>

:: right ::

<figure>
  <img src="/sdpa_self.drawio.svg" style="width: 350px;">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---

:: title ::

### Attention in Transformers
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Transformer attention between two sequences, $\mathbf{X}$ and $\mathbf{Y}$ has a computational cost of (excluding projections):
  $$\mathcal{O}\left(\underbrace{t_{x}\cdot t_{y}\cdot d_{k}}_{\text{MatMul 1}}+\underbrace{t_{x}\cdot t_{y}\cdot d_{v}}_{\text{MatMul 2}}\right)$$

- But RNNs have linear time complexity...
  $$\mathcal{O}\left(t_{x}\cdot d_{k}^2 + t_{x}\cdot d_{q}^2\right)$$

- RNNs are serial, Attention is parallel
  - GPUs *looove* parallelism

:: right ::

<figure>
  <img src="/sdpa_self.drawio.svg" style="width: 350px;">
</figure>

---
layout: full
color: white
---

<a href="https://3.bp.blogspot.com/-aZ3zvPiCoXM/WaiKQO7KRnI/AAAAAAAAB_8/7a1CYjp40nUg4lKpW7covGZJQAySxlg8QCLcBGAs/s640/transform20fps.gif">
<img src="/transformer_flow_of_information.gif" style="width:55%;display: block;margin-left: auto;margin-right: auto;" alt="GIF of the transformer in action">
</a>
```
Jakob Uszkoreit (August 31, 2017). Transformer: A Novel Neural Network Architecture for Language  Understanding.
https://research.google/blog/transformer-a-novel-neural-network-architecture-for-language-understanding/
```

---
hideInToc: false
layout: two-cols-title
columns: is-6
align: l-lt-ct
---
:: title::

### Multi-head Attention
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

- Currently we use 1 set of attention weights
  - Can only process 1 query type

<v-click at="1">

- With $h$ attention heads, we learn $h$ concepts
  - To reduce cost, reduce dimensionality $d_{K, V}/h$

</v-click>

<v-click at="2">

```python
self.attention_heads = [
  AttentionHead(d=self.d // self.h) for i in range(self.h)
  ]

self.mha_proj = nn.Linear(self.d, self.d)

mha = torch.concat([
  attention_heads[i](x) for i in range(self.h)
  ])

out = self.mha_proj(mha)
```
</v-click>

:: right ::

<figure v-click=1>
  <img src="/multihead_attention.drawio.svg" style="width: 100%;">
</figure>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---
:: title::

### Multi-head Attention
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

> Multi-head attention allows the model to jointly attend to information from different representation subspaces at different positions. [One] attention head, averaging inhibits this.

```
Vaswani et al. (2017). Attention is all you need. Advances
in neural information processing systems, 30. (p. 5 & 15)
```

<br>

<v-click at="1">

<div class="ns-c-tight">

Multiple heads, multiple different queries processed in parallel
- Positional heads
- Syntactic heads
- Rare words?

</div>

```
Voita et al. (2019). Analyzing Multi-Head Self-Attention:
Specialized Heads Do the Heavy Lifting, the Rest Can
Be Pruned. Association for Computational Linguistics.
```

</v-click>

:: right ::
<div class="grid w-full h-md grid-cols-2 m-t-0">
  <div class="grid-item grid-col-span-1"><img style="margin: 0 auto;" src="/attending_to_head_new.svg"></div>
  <div class="grid-item grid-col-span-1"><img style="margin: 0 auto;" src="/attending_to_head2_new.svg"></div>
</div>

---
layout: two-cols-title
columns: is-6
align: l-lt-ct
---
:: title::

### Multi-head Attention
##### <span class="bg-orange-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Multi-head Attention</span>

:: left ::

Do different heads attend to different concepts?

<div class="ns-c-tight">
  <v-click at="1">

  - Individual heads = high rank, concantenated heads = low rank
    ```
    Cordonnier, Loukas & Jaggi (2020). Multi-head attention:
    Collaborate instead of concatenate. arXiv:2006.16362.
    ```

  </v-click>

  <br>

  <v-click at="2">

  - Most heads can be pruned away
  - Enc-Dec heads are more important than Enc-Enc heads
    ```
    Voita et al. (2019). Analyzing Multi-Head Self-Attention:
    Specialized Heads Do the Heavy Lifting, the Rest Can
    Be Pruned. Association for Computational Linguistics.
    ```

  </v-click>
</div>

:: right ::

<div class="grid w-full h-full grid-cols-2">
  <div class="grid-item grid-col-span-1 mt-10" v-click="1"><img class="h-full" style="margin: 0 auto;" src="/captured_variance_base_by_head_cropped.svg"></div>
  <div class="grid-item grid-col-span-1 mt-10" v-click="1"><img class="h-full" style="margin: 0 auto;" src="/captured_variance_base_cropped.svg"></div>
  <div class="grid-item grid-col-span-2 mt-7" v-click="2"><img style="margin: 0 auto;" src="/heads_dying_by_attn_type_both-min.png"></div>
</div>

---
hideInToc: false
layout: side-title
color: dark
side: l
titlewidth: is-5
align: lm-mt
---

:: title::

## <span class="bg-lime-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Add & Norm</span>

:: content ::

<figure>
  <img src="/transformer_svg.svg" style="width:100%;display: block;margin-left: auto;margin-right: auto;">
</figure>

---
layout: default
---

## <span class="bg-lime-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Add & Norm</span>


---
layout: default
---

### Residual Connections
##### <span class="bg-lime-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Add & Norm</span>

---
layout: two-cols-title
columns: is-6
align: l-lt-lt
---

:: title ::

### LayerNorm
##### <span class="bg-lime-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Add & Norm</span>

::left::

These are the equations

::right::

$$
\begin{aligned}
\mathbf{X}_{l}~~=~~&\mathtt{LayerNorm}( \\
&~~\mathbf{X}_{l-1}+\texttt{SubLayer}\left(\mathbf{X}_{l-1}\right) \\
&)
\end{aligned}
$$

---
layout: default
---

## <span class="bg-blue-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Feed Forward</span>

---
layout: section
title: "Embedding"
color: dark
columns: is-6
align: l-lt-lt
---

# Embedding

---
layout: default
---

## <span class="bg-green-100 text-black p-0.5 pl-2 pr-2 m-0 rounded">Position Encoding</span>

---
layout: section
color: dark
columns: is-6
align: l-lt-lt
---

# Tokenization

---
layout: section
color: dark
columns: is-6
align: l-lt-lt
---

# Training Transformers

---
layout: "end"
hideInToc: true
---

# The End
