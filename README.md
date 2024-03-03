# Bigram Language Model with Additive Smoothing 

### Task Description:

This project aims to implement a bigram language model with additive smoothing. The model is trained on a given training set, and the smoothing parameter, α, is optimized to minimize the held-out perplexity of the validation set. 

### Implementation Steps:

1. **Maximum-Likelihood Estimation (MLE):**
   The model employs maximum-likelihood estimation for bigram probabilities, which is equivalent to relative frequency estimation. The formula used for estimating bigram probability is:
   
   $ \hat{p} {\text{MLE} (w_i|w_{i-1}) = \frac{\text{count}(w_{i-1}w_i)}{\text{count}(w_{i-1})} \]$

3. **Additive Smoothing:**
   Additive smoothing is applied to handle unseen n-grams. A pseudo-count, α, is added to each n-gram count. The formula for bigram probability with additive smoothing is:
   \[ \hat{p}_{\alpha}(w_i|w_{i-1}) = \frac{\text{count}(w_{i-1}w_i) + \alpha}{\text{count}(w_{i-1}) + \alpha \cdot V} \]
   where \( V \) is the vocabulary size.

4. **Optimization of α:**
   The value of α is optimized to minimize the held-out perplexity of the validation set. 

5. **Perplexity Computation:**
   Perplexity is computed for both the validation and test sets. The perplexity measures how well the model predicts the given data. It is calculated using the formula:
   \[ \text{Perplexity} = \exp\left(-\frac{1}{N} \sum_{i=1}^{N} \log \hat{p}(w_i|w_{i-1})\right) \]
   where \( N \) is the number of words in the dataset.

6. **Plotting:**
   A plot is generated to visualize the relationship between validation-set perplexity and test-set perplexity across a range of α values. This analysis helps identify the optimal α value for the model.

7. **Scaling to Larger Datasets:**
   For further learning, the implementation is tested on larger dataset. This provides insights into how well the model scales in terms of time and memory as the dataset size increases.

## Results

The α value that minimizes the validation set is different than the one for the test set.

The alpha value that minimizes the heldout perplexity of the validation set is larger, indicating that choosing this value for the test set would lead to poor results. We belive there are few possible reasons for this:

When we use the validation set to tune a hyperparameter such as alpha, there is a risk of overfitting to the validation set.
The validation and test sets have a data mismatch in terms of the number of tokens and sentence length, despite having the same number of unique words (6) in both sets. Specifically, the validation set has 11 tokens and sentences of different lengths, while the test set has only 6 tokens.

