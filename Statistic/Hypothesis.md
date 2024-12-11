## Forming

Null Hypothesis ($H_0$) is a statement that the value of a population parameter is equal to some claimed value. 原假设是一个关于总体参数的陈述，它的值等于某个特定值。
- MUST contain condition of equality 必须包含等号
- No effect or no difference 没有效果或没有差异
- Symbolic form: $=, \leq, \geq$

Alternative Hypothesis ($H_a$) is the statement that the parameter has a value that differs from the null hypothesis. 备择假设是一个关于总体参数的陈述，它的值不等于原假设的值。
- Hypothetical statement that the researcher wants to test 假设研究者想要检验的陈述
- Symbolic form: $\neq, <, >$

Example:
> A manufacturer claims that the average life of a transistor is less than1000 hours (h)
> - $H_0: \mu \geq 1000$
> - $H_a: \mu < 1000$
>
> A pharmaceutical firm maintains that the average time for a certain drug to take effect is 15 mins 
> - $H_0: \mu = 15$
> - $H_a: \mu \neq 15$
>
> The mean starting salary of graduates is higher than R50000 per annum 
> - $H_0: \mu \leq 50000 \quad\text{or}\quad \mu = 50000$
> - $H_a: \mu > 50000$

## Two Types of Errors

Because your decision is based on a sample, there is the possibility of making the wrong decision. 由于你的决策是基于样本，所以有可能做出错误的决定。
- Type I Error: Rejecting a true null hypothesis 原假设为真，却拒绝了原假设
- Type II Error: Failing to reject a false null hypothesis 原假设为假，却没有拒绝原假设

| Project | Not rejected $H_0$ | Rejected $H_0$ |
| --- | --- | --- |
| $H_0$ is true | 1 - $\alpha$ | $\alpha$ (Type I Error) |
| $H_0$ is false | $\beta$ | 1 - $\beta$ (Power of the test) |

### Level of Significance

Your maximum allowable probability of making a Type I error. 你允许的最大犯第一类错误的概率。($\alpha$)

\[Pre-specified] By setting $\alpha$ at a small value, you are saying that you want the probability of rejecting a true null hypothesis to be small. 通过将$\alpha$设置为一个小值，我们表明我们希望拒绝一个真实的原假设的概率很小。

Commonly used levels of significance are 0.01, 0.05, and 0.10. 通常使用的显著性水平是0.01、0.05和0.10。

## Statistical Tests

| Parameter | Sampling Distribution | Test Statistic |
| --- | --- | --- |
| Proportion: $p$ | Normal | $Z = \frac{\hat{p} - p}{\sqrt{\frac{p(1-p)}{n}}}$ |
| Mean: $\mu$ | Normal | $Z = \frac{\bar{x} - \mu}{\frac{\sigma}{\sqrt{n}}}$ |
| Mean: $\mu$ | t | $t = \frac{\bar{x} - \mu}{\frac{s}{\sqrt{n}}}$ |
| Variance: $\sigma^2$ | Chi-square | $\chi^2 = \frac{(n-1)s^2}{\sigma^2}$ |

### Types of Hypothesis Tests

- Left-tailed test: $H_a: \mu < \mu_0$ => $Z \leq -Z_{\alpha}$ => $p \leq \alpha$
- Right-tailed test: $H_a: \mu > \mu_0$ => $Z \geq Z_{1-\alpha}$ => $p \leq \alpha$
- Two-tailed test: $H_a: \mu \neq \mu_0$ => $\left| Z \right| \geq \left| Z_{1-\alpha/2} \right|$ => $p \leq \alpha/2$

### Conclusions

Critical Value Method:
- Reject $H_0$ if the test statistic falls in the critical region 拒绝$H_0$如果检验统计量落在临界区域内
- Fail to reject $H_0$ if the test statistic falls in the non-critical region 没有拒绝$H_0$如果检验统计量落在非临界区域内

P-value Method:
- Reject $H_0$ if the p-value is less than or equal to the level of significance 拒绝$H_0$如果p值小于或等于显著性水平
- Fail to reject $H_0$ if the p-value is greater than the level of significance 没有拒绝$H_0$如果p值大于显著性水平

1. Reject $H_0$: There is sufficient/enough evidence to conclude ...(whatever $H_a$ states)
2. Fail to reject $H_0$: There is insufficient evidence to conclude ...(whatever $H_a$ states)


## Parametric Hypothesis Tests

Parametric tests are restricted to data that:
1) show a normal distribution 显示正态分布
2) * are independent of one another  样本之间是独立的
3) * are on the same continuous scale of measurement 在相同的连续测量尺度上
### One-sample

test population mean ($\mu$):

| Sample Size         | $\sigma$ Known                                      | $\sigma$ Unknown                               |
| ------------------- | --------------------------------------------------- | ---------------------------------------------- |
| Large ($n \geq 30$) | $Z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$         | $Z = \frac{\bar{x} - \mu_0}{s/\sqrt{n}}$         |
| Small ($n < 30$)    | $Z = \frac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$         | $t = \frac{\bar{x} - \mu_0}{s/\sqrt{n}}$         |

- $\mu_0$: hypothesized population mean 假设的总体均值
- Z compared to $Z_{\alpha}$, t compared to $t_{\alpha, n-1}$

test population proportion ($p$):
$$
Z = \frac{\hat{p} - p_0}{\sqrt{\frac{p_0(1-p_0)}{n}}}
$$

- $p_0$: hypothesized population proportion 假设的总体比例
- Z compared to $Z_{\alpha}$

test population variance ($\sigma^2$):
$$
\chi^2 = \frac{(n-1)s^2}{{\sigma_0}^2}
$$

- $\sigma_0^2$: hypothesized population variance 假设的总体方差
- $\chi^2$ compared to $\chi^2_{\alpha, n-1}$

### Two-sample

test difference between two population means ($\mu_1 - \mu_2$):

- Large Sample, Known $\sigma_1$ and $\sigma_2$:
$$
Z = \frac{(\bar{x}_1 - \bar{x}_2) - (\mu_1 - \mu_2)}{\sqrt{\frac{\sigma_1^2}{n_1} + \frac{\sigma_2^2}{n_2}}} 
$$

- Large Sample, Unknown $\sigma_1$ and $\sigma_2$:
$$
Z = \frac{(\bar{x}_1 - \bar{x}_2) - (\mu_1 - \mu_2)}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}
$$

- Small Sample
  - Assumption: 1. Normality, 2. Two random samples are drawn independently from two populations.
  - Unknown $\sigma_1$ and $\sigma_2$ (equal):
$$
{s_p}^2 = \frac{(n_1 - 1)s_1^2 + (n_2 - 1)s_2^2}{n_1 + n_2 - 2}, df = n_1 + n_2 - 2
$$
$$
t = \frac{(\bar{x}_1 - \bar{x}_2) - (\mu_1 - \mu_2)}{s_p \cdot \sqrt{\frac{1}{n_1} + \frac{1}{n_2}}}
$$
  - Unknown $\sigma_1$ and $\sigma_2$ (not equal):
$$
df = \frac{\left( \frac{s_1^2}{n_1} + \frac{s_2^2}{n_2} \right)^2}{\frac{{(s_1^2/n_1)}^2}{n_1 - 1} + \frac{{(s_2^2/n_2)}^2}{n_2 - 1}}
$$
$$
t = \frac{(\bar{x}_1 - \bar{x}_2) - (\mu_1 - \mu_2)}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}
$$

- Paired Samples
  - Assumption: $\sigma_1 = \sigma_2$
  - $H_0: \mu_d = 0$
  - $\bar{d}$: sample mean of differences
  - $\sigma_d$: population standard deviation of differences
  - $s_d$: sample standard deviation of differences
$$
t = \frac{\bar{d}}{s_d/\sqrt{n}}
$$


test difference between two population proportions ($p_1 - p_2$):
- Test $p_1-p_2 = 0$
$$
\hat{p} = \frac{x_1 + x_2}{n_1 + n_2} = \frac{n_1 \hat{p}_1 + n_2 \hat{p}_2}{n_1 + n_2}
\quad,
Z = \frac{\hat{p}_1 - \hat{p}_2}{\sqrt{\hat{p}(1-\hat{p})\left(\frac{1}{n_1} + \frac{1}{n_2}\right)}}
$$
- Test $p_1-p_2 = d_0 \quad (d_0 \neq 0)$
$$
Z = \frac{(\hat{p}_1 - \hat{p}_2) - d_0}{\sqrt{\frac{\hat{p}_1(1-\hat{p}_1)}{n_1} + \frac{\hat{p}_2(1-\hat{p}_2)}{n_2}}}
$$

test ratio of two population variances ($\sigma_1^2/\sigma_2^2$):
- $H_0: \sigma_1^2 = \sigma_2^2$
- $H_a: \sigma_1^2 \neq \sigma_2^2$ => $F \geq F_{\alpha/2}(df_1, df_2)$
- $H_a: \sigma_1^2 > \sigma_2^2$ => $F \geq F_{\alpha}(df_1, df_2)$
$$
F = \frac{s_1^2}{s_2^2}
$$

![[Pasted image 20241211151245.png]]
## Nonparametric Hypothesis Tests

Non-parametric tests are used on data that: 
1) show an other-than normal distribution  显示非正态分布
2) are dependent or conditional on one another  依赖于彼此
3) in general, do not have a continuous scale of measurement  通常没有连续的测量尺度

### Variance: Levene's Test

- $H_0$: $\sigma_1^2 = \sigma_2^2$
- $H_a$: $\sigma_1^2 \neq \sigma_2^2$
$$
L = \frac{(N-k)}{k-1} \left( \frac{\sum_{i=1}^{k} n_i (\bar{z}_i - \bar{z})^2}{\sum_{i=1}^{k} \sum_{j=1}^{n_i} (z_{ij} - \bar{z}_i)^2} \right) \sim F(k-1, N-k)
$$
- $N$: total number of cases
- $k$: number of groups
- $n_i$: number of cases in group $i$
- $\bar{z}_i$: mean of group $i$
- $\bar{z}$: overall mean
- $z_{ij}$: respective value in group $i$ and $j$

### Independent Mean: Mann-Whitney U-Test

The Mann-Whitney U-Test is non-parametric counterpart to the t-test for independent samples. Mann-Whitney U 检验是独立样本 t 检验的非参数对应项。

- The t-test for independent samples tests whether there is a mean difference
- The Mann-Whitney U-Test checks whether there is a rank sum difference

- $H_0$: There is no difference (in terms of median) between the two groups 两组之间没有差异（中位数）
- $H_a$: There is a difference (in terms of median) between the two groups 两组之间有差异（中位数）

$$
T_1 = \sum_{i=1}^{n_1} R_i1 \quad \text{,} \quad T_2 = \sum_{i=1}^{n_2} R_i2
$$
$$
U_1 = n_1 n_2 + \frac{n_1(n_1+1)}{2} - T_1 \quad \text{,} \quad U_2 = n_1 n_2 + \frac{n_2(n_2+1)}{2} - T_2
$$
$$
U = \min(U_1, U_2) \text{,} \quad \mu_U = \frac{n_1 n_2}{2} \text{,} \quad \sigma_U = \sqrt{\frac{n_1 n_2(n_1+n_2+1)}{12}}
$$
$$
Z = \frac{U - \mu_U}{\sigma_U} \sim N(0, 1)
$$

> U-Test is a two-tailed test, so the p-value is doubled.