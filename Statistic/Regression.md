## Notation 

$$
X = \begin{pmatrix}X_1
 \\X_2
 \\ \cdots
 \\X_n
\end{pmatrix}
\text{,} \quad Y = f(X) + \epsilon
$$
- $Y$: dependent variable / response
- $X$: independent variable / predictors
- $f(X)$: model function
- $e$: measurement error and other discrepancies
- $f(x) = E(Y|X=x)$: regression function

## Linear Regression

Linear regression is a simple approach to supervised  learning. It assumes that the dependence of $Y$ on $X$ is linear. 线性回归是一种简单的监督学习方法。它假设 $Y$ 对 $X$ 的依赖是线性的。

$$
f_{L}(X) = \beta_0 + \beta_1X_1 + \beta_2X_2 + \cdots + \beta_pX_p
$$

## Simple Linear Regression

$$
Y = \beta_0 + \beta_1X + \epsilon
$$

where $\beta_0$ and $\beta_1$ are two unknown constants that represent the intercept and slope, also known as coefficients or parameters, and $\epsilon$ is the error term. $\beta_0$ 和 $\beta_1$ 是两个未知常数，表示截距和斜率，也称为系数或参数，$\epsilon$ 是误差项。

Given some estimates $\hat{\beta_0}$ and $\hat{\beta_1}$ for the model coefficients, we predict future values of $Y$ by computing 给出模型系数的一些估计值 $\hat{\beta_0}$ 和 $\hat{\beta_1}$，我们通过计算来预测 $Y$ 的未来值：

$$
\hat{y} = \hat{\beta_0} + \hat{\beta_1}x
$$

where $\hat{y}$ indicates a prediction of $Y$ on the basis of $X=x$.  $\hat{y}$ 表示基于 $X=x$ 的 $Y$ 的预测。

### Residuals

The difference between the observed value of the dependent variable ($y$) and the predicted value ($\hat{y}$) is called the residual. 观测到的因变量值 ($y$) 与预测值 ($\hat{y}$) 之间的差异称为残差。

$$
e_i = y_i - \hat{y}_i
$$

We define the residual sum of squares (RSS) as 我们将残差平方和 (RSS) 定义为

$$
RSS = e_1^2 + e_2^2 + \cdots + e_n^2 = \sum_{i=1}^{n}(y_i - \hat{y}_i)^2
$$

> Also known as the sum of squared errors (SSE).

We define the explained sum of squares (ESS) as 我们将解释平方和 (ESS) 定义为

$$
ESS = \sum_{i=1}^{n}(\hat{y}_i - \bar{y})^2
$$

> Also known as the sum of squared regression (SSR).

### Formulas

The least squares approach chooses $\hat{\beta}_0$ amd $\hat{\beta}_1$ to minimize the RSS. The minimizing values can be shown to be  最小二乘法选择 $\hat{\beta}_0$ 和 $\hat{\beta}_1$ 来最小化 RSS。最小化值可以表示为

$$
\hat{\beta}_1 = \frac{\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^{n}(x_i - \bar{x})^2}
$$

$$
\hat{\beta}_0 = \bar{y} - \hat{\beta}_1\bar{x}
$$

The standard error of an estimator reflects how it varies under repeated sampling. We have 估计量的标准误反映了在重复抽样下它的变化。我们有

$$
s^2 = \frac{1}{n-2}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2 = \frac{1}{n-2}RSS = RSE^2
$$

> Residual standard error (RSE), and Mean squared error (MSE) equals $RSE^2$.

$$
SE(\hat{\beta}_1)^2 = \frac{\sigma^2}{\sum_{i=1}^{n}(x_i - \bar{x})^2}
$$

$$
SE(\hat{\beta}_0)^2 = \sigma^2\left[\frac{1}{n} + \frac{\bar{x}^2}{\sum_{i=1}^{n}(x_i - \bar{x})^2}\right]
    = SE(\hat{\beta}_1)^2 \cdot \frac{\sum_{i=1}^{n}x_i^2}{n}
$$

where $\sigma^2 = Var(\epsilon) = s^2 \text{(if variance unknown)}$.  其中 $\sigma^2 = Var(\epsilon) = s^2 \text{(如果总体方差未知)}$。

### Confidence Intervals

These standard errors can be used to compute confidence intervals. A 95% confidence interval is defined as a range of values such that with 95% probability, the range will contain the true unknown value of the parameter. It has the form 这些标准误差可用于计算置信区间。95% 置信区间被定义为一个值范围，使得有 95% 的概率，该范围将包含参数的真实未知值。它的形式为

$$
CI = \hat{\beta}_1 \pm t_{1-\alpha}(n-2) \cdot SE(\hat{\beta}_1)
$$

That is, there is approximately a (1-$\alpha$) chance that the CI will contain the true value of $\beta_1$ (under a scenario where we got repeated samples) 这意味着 CI 包含 $\beta_1$ 的真实值的概率约为 (1-$\alpha$) (在我们得到重复样本的情况下)。

### Prediction Intervals

The predicted response $\hat{y}_h$ for an individual value of $x_h$ is given by 个体值 $x_h$ 的预测响应 $\hat{y}_h$ 由

$$
E[Y|X = x_h] = \hat{\beta}_0 + \hat{\beta}_1x_h
$$

The 100(1-$\alpha$)% level prediction interval for a future observation on the response variable $y$ at $x_h$ is 未来观测值 $y$ 在 $x_h$ 处的 100(1-$\alpha$)% 置信区间为

$$
PI = \hat{\beta}_0 + \hat{\beta}_1x_h \pm t_{1-\alpha/2}(n-2) \cdot RSE\sqrt{1 + \frac{1}{n} + \frac{(x_h - \bar{x})^2}{\sum_{i=1}^{n}(x_i - \bar{x})^2}}
$$

### Hypothesis Testing

Standard errors can also be used to perform hypothesis tests on the coefficients. 标准误差也可用于对系数执行假设检验。
- $H_0: There is no relationship between $X$ and $Y$. => $H_0: \beta_1 = 0$
- $H_a: There is some relationship between $X$ and $Y$. => $H_a: \beta_1 \neq 0$

we compute a t-statistic  我们计算一个 t 统计量

$$
t = \frac{\hat{\beta}_1 - 0}{SE(\hat{\beta}_1)} \sim t_{n-2}
$$

> If we need to test whether $\beta_0$ is equal to some constant $c$, we can use a similar statistic. 如果我们需要测试 $\beta_0$ 是否等于某个常数 $c$，我们可以使用类似的统计量。
$$ t = \frac{\hat{\beta}_0 - c}{SE(\hat{\beta}_0)} \sim t_{n-2} $$

### Overall Accuracy of the Model

RSE provides an absolute measure of lack of fit of the model to the data. It is the square root of the variance of the residuals. RSE 提供了模型与数据不匹配的绝对度量。它是残差方差的平方根。

$$
RSE = \sqrt{\frac{1}{n-2}RSS} = \sqrt{\frac{1}{n-2}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2}
$$

R-squared statistic provides an alternative measure of fit. It takes the form of a proportion of variance explained, and so it always takes on a value between 0 and 1. R 平方统计量提供了另一种适合度量。它采用解释方差的比例形式，因此它总是在 0 和 1 之间。

$$
R^2 = \frac{TSS - RSS}{TSS} = 1 - \frac{RSS}{TSS}
$$

where TSS is the total sum of squares, defined as 其中 TSS 是总平方和，定义为 $TSS = \sum_{i=1}^{n}(y_i - \bar{y})^2$.

$$
F = \frac{(TSS - RSS)/p}{RSS/(n-p-1)} = \frac{R^2/p}{(1-R^2)/(n-p-1)}   \sim F_{p, n-p-1}
$$


## Multiple Linear Regression

$$
Y = \beta_0 + \beta_1X_1 + \beta_2X_2 + \cdots + \beta_pX_p + \epsilon
$$

We interpret $\beta_j$ as the average effect on $Y$ of a one unit increase in $X_j$, holding all other predictors fixed. 我们解释 $\beta_j$ 为 $X_j$ 增加一个单位对 $Y$ 的平均影响，保持所有其他预测变量不变。

95% CI for the $\beta_j$ is
$$
CI = \hat{\beta}_j \pm t_{1-\alpha/2}(n-p-1) \cdot SE(\hat{\beta}_j)
$$


## Residual Plots

A residual plot is a scatterplot of the residuals against the predictor variable. It is used to assess the following assumptions of the model: 残差图是残差与预测变量的散点图。它用于评估模型的以下假设：
- Linear Relationship
- Equal Variance (Homoscedasticity): The probability distribution of the errors has constant variance. 方差齐性：误差的概率分布具有恒定的方差。
- Normality: The errors are normally distributed. 正态性：误差是正态分布的。
- Independence: The errors are independent of each other. 独立性：误差彼此独立。
- No or little Multicollinearity: The predictors are not highly correlated. 没有或很少多重共线性：预测变量之间没有高度相关。

- A proper model will exhibit a random pattern for the spread of the residuals with no discernable shape. 合适的模型将呈现残差分布的随机模式，没有可辨别的形状。
- Residual plots are used extensively in linear regression for diagnostics and assumption testing. 残差图在线性回归中广泛用于诊断和假设检验。
- When apatternis observed, alinear regression modelis probablynot appropriate for the data. 当观察到一种模式时，线性回归模型可能不适合该数据。
- If the residuals form a curvature like shape, then we know that a transformation will be necessary. 如果残差形成类似曲率的形状，那么我们就知道需要进行变换。

### Heteroscedasticity

Heteroscedasticity is a problem that occurs when the residuals are not equally spread across the regression line. 方差不齐性是指残差在回归线周围分布不均匀的问题。

### Outliers

An outlier is an point for which $y_i$ is far from the value predicted by the model. 离群值是指 $y_i$ 远离模型预测值的点。

## Multicollinearity

Collinearity (or multicollinearity) is the undesirable situation where the correlations among the independent variables are strong. 共线性是指独立变量之间的相关性很强的不良情况。

Formally, variance inflation factors (VIF) measure how much the variance of the estimated coefficients are increased over the case of no correlation among the X variables. If no two X variables are correlated, then all the VIFs will be 1. 形式上，方差膨胀因子 (VIF) 衡量了估计系数的方差在 X 变量之间没有相关性的情况下增加了多少。如果没有两个 X 变量相关，则所有 VIF 值将为 1。

If VIF for one of the variables is around or greater than 5, there is collinearity associated with that variable. 如果某个变量的 VIF 大约等于或大于 5，则该变量存在共线性。