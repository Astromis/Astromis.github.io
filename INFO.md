To use the math rendering engine the mathjax is used; Tutorial was : https://lyk6756.github.io/2016/11/25/write_latex_equations.html


Basic usage:
The default math delimiters are $$...$$ and \[...\] for displayed mathematics, and \(...\) for in-line mathematics.

The following is a math block:$$ 5 + 5 $$

But next comes a paragraph with an inline math statement:\$$ 5 + 5 $$

The following kramdown fragment:

```
$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$

```
------------------------------

If jejyll doesn't want start with an error about bundler 2.0, try this:

```bash
sudo gem update --system
sudo gem install bundler
bundler update --bundler
```
