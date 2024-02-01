# Introduction to DSP
- What is digital signal?
- Why we use Digital signal?
## Basic Background in DSP
### Convolution
Before we define what is convolution, we should first explain what is unit sample response and what is linear time-invariant system.
- **Unit sample response**
  - It could be easily explained as the response of the system to a unit sample function
  - Actually the defination is :[TODO]
  - Unit sample function is well-known as $\delta(i)$ and if the system is $T\{Func(i)\}$ than the unit sample response of $T\{Func(i)\}$ is $T\{\delta(i)\}$
- **Linear time-invariant system**
  - If the system output could be defined by: $y[n] = x[n]*h[n]$, where $h[n]$ is the unit sample response of the system, it is linear time-invariant.
  - Why does this happens?
    - It is easy to know linear system is linear with $T\{a+b\}= T\{a\}+T\{b\}$
    - And time-invarient system has $T\{x[n]\} = T\{n-i\}$
    - For discrete signal, we express $x[n] =\sum_{i=-\infty}^{\infty} x[i]\cdot \delta[n-i]$ there is:
    - $T\{x[n]\}=T\{\sum_{i=-\infty}^{\infty} x[i]\cdot \delta[n-i]\}$
    - For linear: $T\{x[n]\}=\sum_{i=-\infty}^{\infty}T\{x[i]\cdot \delta[n-i]\}$
    - $T\{x[n]\}=\sum_{i=-\infty}^{\infty} x[i] T\{\delta[n-i]\}$
    - For time-invarient $T\{\delta[n]\} = h[n]$ and $T\{\delta[n-i]\}=h[n-i]$
    - hense here is  $T\{x[n]\}=\sum_{i=-\infty}^{\infty} x[i] h[n-i] = x[n]*h[n]$
- **Convolution**
  - We call the funtion $T\{x[n]\}=\sum_{i=-\infty}^{\infty} x[i] h[n-i] = x[n]*h[n]$ as convolution.