# hw2
## P3.1
**(a) 상태변수 설정**  
* $x_{1}(t)=y(t)$  
* $x_{2}(t)=\dfrac{dy(t)}{dt}$  

**(b) 1차 미분방정식 구하기**  
* $x_{1}(t)=y(t)$ 양변을 미분하면  
$\dfrac{dx_{1}(t)}{dt}=\dfrac{dy(t)}{dt}=x_{2}(t)$  
$\to\dfrac{dx_{1}(t)}{dt}=x_{2}(t)$

* $M\dfrac{dx_{2}(t)}{dt}+bx_{2}(t)+kx_{1}(t)=F(t)$  
$\to\dfrac{dx_{2}(t)}{dt}=-\dfrac{b}{M}x_{2}(t)-\dfrac{k}{M}x_{1}(t)+\dfrac{1}{M}F(t)$  

**(c) 상태미분방정식 구하기**  
위에서 구한 1차 미분방정식에 의해 상태미분방정식을 구하면 아래와 같다.  

$$\mathbf{\dot{x}}(t)=\begin{bmatrix} 0&1 \\
-\dfrac{k}{M}&-\dfrac{b}{M}\\ \end{bmatrix} \mathbf{x}(t)+
\begin{bmatrix} 0 \\
\dfrac{1}{M}\\ \end{bmatrix} F(t)$$  

## P3.3
상태변수가 $x_{1}(t)=i_{L}(t)$, $x_{2}(t)=v_{c}(t)$이므로  
KVL에 의해 아래와 같은 두 개의 1차 미분방정식이 구해진다.  

* $-v_{1}(t)+L\dfrac{dx_{1}(t)}{dt}-x_{2}(t)+v_{2}(t)=0$  
  $L\dfrac{dx_{1}(t)}{dt}=x_{2}(t)+v_{1}(t)-v_{2}(t)$  
  $\dfrac{dx_{1}(t)}{dt}=\dfrac{1}{L}x_{2}(t)+\dfrac{1}{L}v_{1}(t)-\dfrac{1}{L}v_{2}(t)$

* $Rx_{1}(t)-RC\dfrac{dx_{2}}{dt}+x_{2}(t)-v_{2}(t)=0$  
  $RC\dfrac{dx_{2}(t)}{dt}=-Rx_{1}(t)-x_{2}(t)+v_{2}(t)$  
  $\dfrac{dx_{2}(t)}{dt}=-\dfrac{1}{C}x_{1}(t)-\dfrac{1}{RC}x_{2}(t)+\dfrac{1}{RC}v_{2}(t)$

이를 상태미분방정식으로 나타내면 다음과 같다.  

$$\mathbf{\dot{x}}(t)=\begin{bmatrix} 0&\dfrac{1}{L} \\
-\dfrac{1}{C}&-\dfrac{1}{RC}\\ \end{bmatrix} \mathbf{x}(t)+
\begin{bmatrix} \dfrac{1}{L}&-\dfrac{1}{L} \\
0&\dfrac{1}{RC}\\ \end{bmatrix} \mathbf{v}(t)$$  

## P3.5
**(a) transfer function**  
$T(s)=\dfrac{\dfrac{s+2}{s+8}\cdot\dfrac{1}{s-3}\cdot\dfrac{1}{s}}{1+\dfrac{s+2}{s+8}\cdot\dfrac{1}{s-3}\cdot\dfrac{1}{s}}$
