#Mathematics  

aka. [[Normal Distribution]]

The [[Probability Density Function]] of the normal distribution in one dimension is:
<math xmlns="http://www.w3.org/1998/Math/MathML" alttext="f left-parenthesis x bar mu comma sigma squared right-parenthesis equals StartFraction 1 Over StartRoot 2 pi sigma squared EndRoot EndFraction e Superscript minus StartFraction left-parenthesis x minus mu right-parenthesis squared Over 2 sigma squared EndFraction" display="block">
  <mstyle scriptlevel="0" displaystyle="true">
    <mrow>
      <mi>f</mi>
      <mrow>
        <mo>(</mo>
        <mi>x</mi>
        <mo>&#x2223;</mo>
        <mi>&#x3BC;</mi>
        <mo>,</mo>
        <msup>
          <mi>&#x3C3;</mi>
          <mn>2</mn>
        </msup>
        <mo>)</mo>
      </mrow>
      <mo>=</mo>
      <mfrac>
        <mn>1</mn>
        <msqrt>
          <mrow>
            <mn>2</mn>
            <mi>&#x3C0;</mi>
            <msup>
              <mi>&#x3C3;</mi>
              <mn>2</mn>
            </msup>
          </mrow>
        </msqrt>
      </mfrac>
      <msup>
        <mi>e</mi>
        <mrow>
          <mo>-</mo>
          <mfrac>
            <msup>
              <mrow>
                <mo>(</mo>
                <mi>x</mi>
                <mo>-</mo>
                <mi>&#x3BC;</mi>
                <mo>)</mo>
              </mrow>
              <mn>2</mn>
            </msup>
            <mrow>
              <mn>2</mn>
              <msup>
                <mi>&#x3C3;</mi>
                <mn>2</mn>
              </msup>
            </mrow>
          </mfrac>
        </mrow>
      </msup>
    </mrow>
  </mstyle>
</math>
Where:

- $x$: value from the distribution
- $μ$: mean of the distribution
- $σ^2$: variance (and $σ$ is the standard deviation)

![[Pasted image 20230913051508.png]]

_multivariate normal distribution_ (or _multivariate Gaussian distribution_) $\mathcal{N}\left( \mu, \sum \right) \text{ in } k \text{ dimentions}$ with mean vector $\mu$ and symmetric covariance matrix $\sum$ is as follows: 
<math xmlns="http://www.w3.org/1998/Math/MathML" alttext="f left-parenthesis x 1 comma ellipsis comma x Subscript k Baseline right-parenthesis equals StartFraction exp left-parenthesis minus one-half left-parenthesis bold x minus mu right-parenthesis Superscript normal upper T Baseline bold upper Sigma Superscript negative 1 Baseline left-parenthesis bold x minus mu right-parenthesis right-parenthesis Over StartRoot left-parenthesis 2 pi right-parenthesis Superscript k Baseline StartAbsoluteValue bold upper Sigma EndAbsoluteValue EndRoot EndFraction" display="block">
  <mstyle scriptlevel="0" displaystyle="true">
    <mrow>
      <mi>f</mi>
      <mrow>
        <mo>(</mo>
        <msub>
          <mi>x</mi>
          <mn>1</mn>
        </msub>
        <mo>,</mo>
        <mo>...</mo>
        <mo>,</mo>
        <msub>
          <mi>x</mi>
          <mi>k</mi>
        </msub>
        <mo>)</mo>
      </mrow>
      <mo>=</mo>
      <mfrac>
        <mrow>
          <mo form="prefix">exp</mo>
          <mfenced separators="" open="(" close=")">
            <mo>-</mo>
            <mfrac>
              <mn>1</mn>
              <mn>2</mn>
            </mfrac>
            <msup>
              <mrow>
                <mo>(</mo>
                <mi>&#x1D431;</mi>
                <mo>-</mo>
                <mi>&#x3BC;</mi>
                <mo>)</mo>
              </mrow>
              <mi mathvariant="normal">T</mi>
            </msup>
            <msup>
              <mrow>
                <mi>&#x3A3;</mi>
              </mrow>
              <mrow>
                <mo>-</mo>
                <mn>1</mn>
              </mrow>
            </msup>
            <mrow>
              <mo>(</mo>
              <mi>&#x1D431;</mi>
              <mo>-</mo>
              <mi>&#x3BC;</mi>
              <mo>)</mo>
            </mrow>
          </mfenced>
        </mrow>
        <msqrt>
          <mrow>
            <msup>
              <mrow>
                <mo>(</mo>
                <mn>2</mn>
                <mi>&#x3C0;</mi>
                <mo>)</mo>
              </mrow>
              <mi>k</mi>
            </msup>
            <mrow>
              <mo>|</mo>
              <mi>&#x3A3;</mi>
              <mo>|</mo>
            </mrow>
          </mrow>
        </msqrt>
      </mfrac>
    </mrow>
  </mstyle>
</math>

