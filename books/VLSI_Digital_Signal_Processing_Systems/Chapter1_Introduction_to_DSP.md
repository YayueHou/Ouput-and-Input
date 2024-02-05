# Introduction to DSP
- What is digital signal?
- Why we use Digital signal?
## Basic Background in DSP
### Convolution
Before we define what is convolution, we should first explain what is unit sample response and what is linear time-invariant system.
- **Unit sample response**
  - It could be easily explained as the response of the system to a unit sample function
  - Actually the defination is :[TODO]
  - Unit sample function is well-known as $\delta(i)$ and if the system is $T\lbrace  Func(i)\rbrace$ than the unit sample response of $T\lbrace Func(i)\rbrace$ is $T\lbrace \delta(i)\rbrace$
- **Linear time-invariant system**
  - If the system output could be defined by: $y[n] = x[n]*h[n]$, where $h[n]$ is the unit sample response of the system, it is linear time-invariant.
  - Why does this happens?
    - It is easy to know linear system is linear with $$T\lbrace a+b\rbrace= T\lbrace a\rbrace+T\lbrace b\rbrace$$
    - And time-invarient system has $$T\lbrace x[n]\rbrace = T\lbrace n-i\rbrace$$
    - For discrete signal, we express $$x[n] =\sum_{i=-\infty}^{\infty} x[i]\cdot \delta[n-i]$$ there is:
      $$T\lbrace x[n]\rbrace=T\lbrace\sum_{i=-\infty}^{\infty} x[i]\cdot \delta[n-i]\rbrace$$
    - For linear: $$T\lbrace x[n]\rbrace=\sum_{i=-\infty}^{\infty}T\lbrace x[i]\cdot \delta[n-i]\rbrace$$
     $$T\lbrace x[n]\rbrace=\sum_{i=-\infty}^{\infty} x[i] T\lbrace\delta[n-i]\rbrace$$
    - For time-invarient $$T\lbrace\delta[n]\rbrace = h[n]$$ and $$T\lbrace\delta[n-i]\rbrace=h[n-i]$$
    - hense here is  $$T\lbrace x[n]\rbrace=\sum_{i=-\infty}^{\infty} x[i] h[n-i] = x[n]*h[n]$$
- **Convolution**
  - We call the funtion $$T\lbrace x[n]\rbrace=\sum_{i=-\infty}^{\infty} x[i] h[n-i] = x[n]*h[n]$$ as convolution.
