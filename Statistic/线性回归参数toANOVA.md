
$$
MSE = SSE/df2 \text{,}\quad SSE = RSS \text{,}\quad \frac{1}{n-2}RSS = RSE^2 \text{,}\quad df2 = n - p - 1
$$

$$
\rightarrow MSE = \frac{(n-2)RSE^2}{n - p - 1}\quad\text{when p=1, } MSE = RSE^2
$$

主要参数：
- p, f, df1, df2: 从参数中直接可得的p值，F值，自由度
- RSE: Residual standard error ($\sqrt{MSE}=RSE$)
- $f = \frac{MSR}{MSE}$ => $MSR = f \cdot MSE$

|            | SS        | df      | MS                     | F   | p   |
| ---------- | --------- | ------- | ---------------------- | --- | --- |
| Regression | $MSR*df1$ | df1     | $f \cdot RSE^2$        | f   | p   |
| Error      | $MSE*df2$ | df2     | $RSE^2$                |     |     |
| Total      | SSR+SSE   | df1+df2 |                        |     |     |
