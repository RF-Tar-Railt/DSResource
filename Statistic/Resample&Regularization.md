## Resampling Methods

### Cross-Validation

Cross-validation is a statistical method used to estimate the skill of machine learning models. It is commonly used in applied machine learning to compare and select a model for a given predictive modeling problem because it is easy to understand, easy to implement, and results in skill estimates that generally have a lower bias than other methods. 交叉验证是一种用于估计机器学习模型技能的统计方法。它通常用于应用机器学习，以比较和选择给定预测建模问题的模型，因为它易于理解、易于实现，并且产生的技能估计通常比其他方法具有较低的偏差。

- K-Fold Cross-Validation: The dataset is divided into k subsets. The holdout method is repeated k times, such that each time, one of the k subsets is used as the test set and the other k-1 subsets are put together to form a training set. The error estimation is averaged over all k trials. 数据集被分成 k 个子集。保留法重复 k 次，每次将 k 个子集中的一个用作测试集，其他 k-1 个子集放在一起形成训练集。错误估计在所有 k 次试验中平均。
- Leave-One-Out Cross-Validation (LOOCV): A single observation from the original sample is used as the validation data, and the remaining observations are used as the training data. This is repeated such that each observation in the sample is used once as the validation data. 单个原始样本中的观测值用作验证数据，其余观测值用作训练数据。重复此过程，使得样本中的每个观测值都用作一次验证数据。
- Stratified K-Fold Cross-Validation: The folds are selected so that the mean response value is approximately equal in all the folds. 选择折叠，使所有折叠中的平均响应值大致相等。

| Method            | Advantages                                     | Disadvantages                                    |
|-------------------|------------------------------------------------|--------------------------------------------------|
| K-Fold            | Easy to implement, computationally efficient   | Can be biased towards majority classes           |
| Stratified K-Fold | Reduces bias, better representation of classes | Computationally expensive                        |
| LOOCV             | Provides a very accurate estimate              | Very computationally expensive, can include bias |

## Model Selection

- Subset Selection: We identify a subset of the $p$ predictors that we believe to be related to the response. We then fit a model using least squares on the reduced set of variables. 我们确定与响应相关的 $p$ 个预测变量的子集。然后，我们使用最小二乘法在减少的变量集上拟合模型。
- Shrinkage Methods: We fit a model involving all $p$ predictors, but the estimated coefficients are shrunken towards zero relative to the least squares estimates. This shrinkage (also known as regularization) reduces variance and can also perform variable selection. 我们拟合涉及所有 $p$ 个预测变量的模型，但相对于最小二乘估计，估计系数被缩小到零。这种收缩（也称为正则化）减少了方差，还可以执行变量选择。
- Dimension Reduction: We project the $p$ predictors into a $M$-dimensional subspace where $M < p$. This is achieved by computing $M$ different linear combinations, or projections, of the variables. 我们将 $p$ 个预测变量投影到一个 $M$ 维子空间，其中 $M < p$。这是通过计算变量的 $M$ 个不同线性组合或投影来实现的。 (PCA, PLS)

### Forward/Backward Stepwise Selection

Forward stepwise selection begins with a model containing no predictors, and then adds predictors to the model, one at a time, until all of the predictors are in the model. 向前逐步选择从不包含预测变量的模型开始，然后逐个向模型添加预测变量，直到所有预测变量都在模型中。

Backward stepwise selection begins with the full model, and then removes the least useful predictor, one at a time, until all of the remaining predictors are significant. 向后逐步选择从完整模型开始，然后逐个删除最不相关的预测变量，直到所有剩余的预测变量都显著。

## Ridge Regression and Lasso

The subset selection methods use least squares to fit a linear model that contains a subset of the predictors. 子集选择方法使用最小二乘法拟合包含预测变量子集的线性模型。

As an alternative, we can fit a model containing all $p$ predictors using a technique that constrains or regularizes the coefficient estimates or, equivalently, shrinks the coefficient estimates towards zero. 作为替代，我们可以使用一种技术拟合包含所有 $p$ 个预测变量的模型，该技术约束或正则化系数估计，或者等效地将系数估计值收缩到零。

### Ridge Regression (L2 Regularization)

Ridge Regression works by applying a penalizing term (reducing the weights and biases) to overcome overfitting. 岭回归通过应用惩罚项（减小权重和偏差）来克服过拟合。

Slope has been reduced with ridge regression penalty and therefore the model becomes less sensitive to changes in the independent variable (X). 使用岭回归惩罚减小了斜率，因此模型对自变量（X）的变化不太敏感。

$$
RSS^* = RSS + \lambda\sum_{j=1}^{p}\beta_j^2
$$

- We can show that ridge regression doesn’t set the coefficients exactly to zero unless $\lambda = \inf$, in which case they are all zero.  我们可以证明岭回归不会将系数设置为零，除非 $\lambda = \inf$，在这种情况下，它们都为零。
- Therefore, ridge regression cannot perform variable selection, i.e. will include all p predictors in the final model. 因此，岭回归无法执行变量选择，即在最终模型中将包含所有 p 个预测变量。
- Ridge regression performs well when there is a subset of true coefficients that are small or zero. 当存在一小部分真实系数为小或零时，岭回归表现良好。
- It doesn’t do well when all of the true coefficients are moderately large, however, will still perform better than OLS regression. 然而，当所有真实系数都适度大时，它表现不佳，但仍然优于OLS回归。

### Lasso (L1 Regularization)

Lasso works by introducing a bias term but instead of squaring the slope, the absolute value of the slope is added as a pnalty term. Lasso 通过引入一个偏差项，而不是平方斜率，将斜率的绝对值作为惩罚项添加。

$$
RSS^* = RSS + \lambda\sum_{j=1}^{p}|\beta_j|
$$

- The nature of the lasso penalty  causes some of the coefficients to be shrunken to zero exactly. lasso 惩罚的性质导致一些系数被缩小到零。
- This is what makes lasso different than ridge regression. It is able to perform variable selection in the linear model. 这就是使 lasso 与岭回归不同的地方。它能够在线性模型中执行变量选择。
- As $\lambda$ increases, more coefficients are set to zero, and among non-zero coefficients, more shrinkage is applied. 随着 $\lambda$ 的增加，更多的系数被设置为零，并且在非零系数中，应用了更多的收缩。