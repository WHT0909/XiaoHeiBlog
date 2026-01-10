---
title: The Elements of Statistical Learning 阅读笔记
date: 2026-01-09 21:48:46
tags:
    - 统计学
    - 机器学习
categories:
    - 统计学
mathjax: true
---

<i>The Elements of Statistical Learning</i> 阅读笔记，持续更新中
<!-- more -->

<!-- MathJax配置 -->
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {
    inlineMath: [['$','$'], ['\\(','\\)']],
    displayMath: [['$$','$$'], ['\\[','\\]']],
    processEscapes: true,
    processEnvironments: true
  },
  TeX: {
    extensions: ["AMSmath.js", "AMSsymbols.js"],
    equationNumbers: { autoNumber: "AMS" }
  },
  "HTML-CSS": {
    linebreaks: { automatic: true },
    scale: 90
  },
  SVG: {
    linebreaks: { automatic: true }
  }
});
</script>

<!-- 加载MathJax 2.x版本（更兼容） -->
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.9/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

<style>
    .blue-card {
        background: #e3f2fd;
        padding: 20px 25px;
        border-radius: 8px;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
        margin-bottom: 24px;
        width: 100%;
        border-left: 4px solid #2196f3;
    }

    .proof-card {
        background: #fff8e1; /* 柔和的暖黄色背景 */
        padding: 25px 30px;
        border-radius: 8px;
        box-shadow: 0 3px 10px rgba(0, 0, 0, 0.08);
        margin: 30px 0;
        width: 100%;
        border-left: 4px solid #ff9800; /* 橙色边框 */
        position: relative;
        overflow: hidden;
    }
    
    .catalog {
        margin: 20px 0;
    }
    
    h2, h3 {
        margin-top: 30px;
        padding-top: 10px;
    }
/* 
    p{
        font-size: 17px;
    } */
</style>

<br>
<div class="catalog">
    <h3>目录</h3>
    <a href="#chapter1">1. 有监督学习概述</a><br>
    <a href="#chapter1.1" style="margin-left: 2em;">1.1 线性模型</a><br>
</div><br><br>

<h2 id="chapter1">1. 有监督学习概述</h2>

<h3 id="chapter1.1">1.1 线性模型</h3>

<p>输入：$ X^{T}=(X_{1}, X_{2}, \ldots , X_{p}) $</p>

<p>输出（估计值）：$ \hat{Y}=\hat{\beta_{0}}+\sum_{j=1}^{p}X_{j}\hat{\beta_{j}} $</p>

<p>向量形式：$ \hat{Y}=X^{T}\hat{\beta} $</p>

<div class="blue-card">
    <p>在机器学习中，带有 "hat" 的变量是实际估计出来的，有误差的结果；不带 "hat" 的是真实但未知的参数</p>
</div>

<p>$(X, \hat{Y})$构成了一个 p + 1 维的"超平面"，此时输入是 p 维，输出是 1 维</p>

<div class="blue-card">
    <p>超平面：在 n 维欧氏空间中，维度为 n - 1 的线性子空间</p>
</div>

<p>$f(x, y)=X^{T}\hat{\beta}$的梯度$\nabla f=\beta$</p>

<div class="proof-card">
<p><strong>证明</strong></p>

$$X^{T}=(X_{1}, X_{2}, \ldots, X_{p})$$

$$f(X)=\beta_{1}X_{1}+\beta_{2}X_{2}+\cdots+\beta_{p}X_{p}$$

<p>$f(X)$的梯度定义如下：</p>

$$
\nabla f(X)=
\begin{bmatrix}
\frac{\partial f}{\partial X_{1}} \\
\frac{\partial f}{\partial X_{2}} \\
\vdots \\
\frac{\partial f}{\partial X_{p}}
\end{bmatrix}
$$

<p>对每一个$X_{i}$求偏导数，将得到对应的$\beta_{i}$，将所有的$\beta_{i}$拼接到一起即可得到$\beta$</p>

$$
\beta = 
\begin{bmatrix}
\beta_{1} \\
\beta_{2} \\
\vdots \\
\beta_{p}
\end{bmatrix}
$$

</div>

<p><strong>直观理解：如果你站在 p 维的输入空间里，想要最快地爬到 $f(x,y)$（输出值）最高的地方，你应该沿着 $\beta$ 这个向量的方向走</strong></p>

<p style="font-family: Times New Roman; font-size: 20px;">
Page12: Viewed as a function over the p-dimensional input space, $f(X)=X^{T}\beta$ is linear, and the gradient $f^{'}(X)=\beta$ is a vector in input space that points in the steepest uphill direction.
</p>

<!-- 如果MathJax没有自动渲染，添加手动刷新 -->
<script>
if (typeof MathJax !== 'undefined') {
    MathJax.Hub.Queue(["Typeset", MathJax.Hub]);
}
</script>