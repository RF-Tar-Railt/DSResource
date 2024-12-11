
主要参数：
- p, f, df1, df2: 从参数中直接可得的p值，F值，自由度
- RSE: Residual standard error ($\sqrt{MSE}=RSE$)

|            | SS        | df      | MS                     | F   | p   |
| ---------- | --------- | ------- | ---------------------- | --- | --- |
| Regression | $MSR*df1$ | df1     | $\sqrt{f \cdot RSE^2}$ | f   | p   |
| Error      | $MSE*df2$ | df2     | $RSE^2$                |     |     |
| Total      | SSR+SSE   | df1+df2 |                        |     |     |
