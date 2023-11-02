---
title: 一些不定积分的推导（一）
date: 2023-10-27 23:15:09
categories:
    - 总结
    - 数学
tags:
    - 积分
description: 本文总结了一些不定积分的推导过程。
---
# 摘要
本文总结了一些形如$\int(mx^2+na^2)^pdx$（其中$a$、$m$、$n$、$p$均为常数）的不定积分及其推导过程。
# 结论
+ $$\int\dfrac{1}{x^2+a^2}dx=\dfrac{1}{a}\arctan\dfrac{x}{a}+C$$

+ $$\int\dfrac{1}{-x^2+a^2}dx=\dfrac{1}{2a}\ln\left|\dfrac{a+x}{a-x}\right|+C$$

+ $$\int\dfrac{1}{x^2-a^2}dx=\dfrac{1}{2a}\ln\left|\dfrac{x-a}{x+a}\right|+C$$
    
+ $$\int\dfrac{1}{\sqrt{x^2+a^2}}dx=\ln\left|x+\sqrt{x^2+a^2}\right|+C$$
    
+ $$\int\dfrac{1}{\sqrt{-x^2+a^2}}dx=\arcsin\dfrac{x}{a}+C$$
    
+ $$\int\dfrac{1}{\sqrt{x^2-a^2}}dx=\ln\left|x+\sqrt{x^2-a^2}\right|+C$$
    
+ $$\int\sqrt{x^2+a^2}dx=\dfrac{1}{2}\left(x\sqrt{x^2+a^2}+a^2\ln\left|x+\sqrt{x^2+a^2}\right|\right)+C$$
    
+ $$\int\sqrt{-x^2+a^2}dx=\dfrac{1}{2}\left(a^2\arcsin\dfrac{x}{a}+x\sqrt{a^2-x^2}\right)+C$$
    
+ $$\int\sqrt{x^2-a^2}dx=\dfrac{1}{2}\left(x\sqrt{x^2-a^2}-a^2\ln\left|x+\sqrt{x^2-a^2}\right|\right)+C$$

# 推导
+ $m=1,n=1,p=-1$时：
$$\begin{aligned}
    \int\dfrac{1}{x^2+a^2}dx&=\dfrac{1}{a}\int\dfrac{1}{\left(\dfrac{x}{a}\right)^2+1}d\dfrac{x}{a}\\
    &=\dfrac{1}{a}\arctan\dfrac{x}{a}+C
\end{aligned}$$

+ $m=-1,n=1,p=-1$时：
$$\begin{aligned}
    \int\dfrac{1}{-x^2+a^2}dx&=\int\dfrac{1}{(a+x)(a-x)}dx\\
    &=\dfrac{1}{2a}\left(\int\dfrac{1}{a+x}dx+\int\dfrac{1}{a-x}dx\right)\\
    &=\dfrac{1}{2a}\ln\left|\dfrac{a+x}{a-x}\right|+C
\end{aligned}$$

+ $m=1,n=-1,p=-1$时：
$$\begin{aligned}
    \int\dfrac{1}{x^2-a^2}dx&=\int\dfrac{1}{(x+a)(x-a)}dx\\
    &=\dfrac{1}{2a}\left(\int\dfrac{1}{x-a}dx-\int\dfrac{1}{x+a}dx\right)\\
    &=\dfrac{1}{2a}\ln\left|\dfrac{x-a}{x+a}\right|+C
\end{aligned}$$
    
+ $m=1,n=1,p=-\dfrac{1}{2}$时：
$$\begin{aligned}
    \int\dfrac{1}{\sqrt{x^2+a^2}}dx&\xlongequal{x=a\tan t}\int\dfrac{a\sec^2t}{a\sec t}dt\\
    &=\int\sec t\,dt\\
    &=\ln\left|\tan t+\sec t\right|+C\\
    &=\ln\left|\dfrac{x}{a}+\sqrt{\left(\dfrac{x}{a}\right)^2+1}\right|+C\\
    &=\ln\left|x+\sqrt{x^2+a^2}\right|+C
\end{aligned}$$
    
+ $m=-1,n=1,p=-\dfrac{1}{2}$时：
$$\begin{aligned}
    \int\dfrac{1}{\sqrt{-x^2+a^2}}dx&=\int\dfrac{1}{\sqrt{1-\left(\dfrac{x}{a}\right)^2}}d\dfrac{x}{a}\\
    &=\arcsin\dfrac{x}{a}+C
\end{aligned}$$
    
+ $m=1,n=-1,p=-\dfrac{1}{2}$时：
$$\begin{aligned}
    \int\dfrac{1}{\sqrt{x^2-a^2}}dx&\xlongequal{x=a\sec t}\int\dfrac{a\tan t\sec t}{a\tan t}dt\\
    &=\int\sec t\,dt\\
    &=\ln\left|\tan t+\sec t\right|+C\\
    &=\ln\left|\dfrac{x}{a}+\sqrt{\left(\dfrac{x}{a}\right)^2-1}\right|+C\\
    &=\ln\left|x+\sqrt{x^2-a^2}\right|+C
\end{aligned}$$
    
+ $m=1,n=1,p=\dfrac{1}{2}$时：
$$\int\sqrt{x^2+a^2}dx\xlongequal{x=a\tan t}a^2\int\sec^3t\,dt$$
对$A=\int\sec^3t\,dt$进行求解：
$$\begin{aligned}
    A=\int\sec^3t\,dt&=\int\sec t\,d\tan t\\
    &=\sec t\tan t-\int\tan t\,d\sec t\\
    &=\sec t\tan t-\int\tan^2t\sec t\,dt\\
    &=\sec t\tan t-\int\left(\sec^2t-1\right)\sec t\,dt\\
    &=\sec t\tan t+\int\sec t\,dt-\int\sec^3t\,dt\\
    &=\sec t\tan t+\ln\left|\sec t+\tan t\right|-A
\end{aligned}$$
因此，可得$\int\sec^3t\,dt=\dfrac{1}{2}\left(\sec t\tan t+\ln\left|\sec t+\tan t\right|\right)+C$，那么：
$$\begin{aligned}
    \int\sqrt{x^2+a^2}dx&\xlongequal{x=a\tan t}a^2\int\sec^3t\,dt\\
    &=\dfrac{a^2}{2}\left(\tan t\sec t+\ln\left|\sec t+\tan t\right|\right)+C\\
    &=\dfrac{1}{2}\left(x\sqrt{x^2+a^2}+a^2\ln\left|x+\sqrt{x^2+a^2}\right|\right)+C\end{aligned}$$
    
+ $m=-1,n=1,p=\dfrac{1}{2}$时：
$$\begin{aligned}
    \int\sqrt{-x^2+a^2}dx&\xlongequal{x=a\sin t}a^2\int\cos^2 t\,dt\\
    &=\dfrac{a^2}{2}\int1+\cos2t\,dt\\
    &=\dfrac{a^2}{2}\left(t+\sin t\cos t\right)+C\\
    &=\dfrac{a^2}{2}\left(\arcsin \dfrac{x}{a}+\frac{x}{a}\sqrt{1-\left(\dfrac{x}{a}\right)^2}\right)+C\\
    &=\dfrac{1}{2}\left(a^2\arcsin\dfrac{x}{a}+x\sqrt{a^2-x^2}\right)+C
    \end{aligned}$$
    
+ $m=1,n=-1,p=\dfrac{1}{2}$时：
$$\begin{aligned}
    \int\sqrt{x^2-a^2}dx&\xlongequal{x=a\sec t}a^2\int\tan^2 t\sec t\,dt\\
    &=a^2\int\left(\sec^2t-1\right)\sec t\,dt\\
    &=a^2\left(\int\sec^3t\,dt-\int\sec t\,dt\right)\\
    &=\dfrac{a^2}{2}\left(\sec t\tan t-\ln\left|\sec t+\tan t\right|\right)+C\\
    &=\dfrac{1}{2}\left(x\sqrt{x^2-a^2}-a^2\ln\left|x+\sqrt{x^2-a^2}\right|\right)+C
\end{aligned}$$