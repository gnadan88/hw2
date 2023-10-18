# 6주차 과제
## P3.1
**(a) state variable 설정**  
* $x_{1}(t)=y(t)$  
* $x_{2}(t)=\dfrac{dy(t)}{dt}$  

**(b) first-order differential equation 구하기**  
* $x_{1}(t)=y(t)$ 양변을 미분하면  
$\dfrac{dx_{1}(t)}{dt}=\dfrac{dy(t)}{dt}=x_{2}(t)$  
$\to\dfrac{dx_{1}(t)}{dt}=x_{2}(t)$

* spring-mass-damper 시스템에서 힘의 관계를 식으로 정리하면  
  $M\dfrac{dx_{2}(t)}{dt}+bx_{2}(t)+kx_{1}(t)=F(t)$  
  $\to\dfrac{dx_{2}(t)}{dt}=-\dfrac{b}{M}x_{2}(t)-\dfrac{k}{M}x_{1}(t)+\dfrac{1}{M}F(t)$  

**(c) state differential equation 구하기**  
* $\dfrac{dx_{1}(t)}{dt}=x_{2}(t)$  
* $\dfrac{dx_{2}(t)}{dt}=-\dfrac{b}{M}x_{2}(t)-\dfrac{k}{M}x_{1}(t)+\dfrac{1}{M}F(t)$  

위 두 식을 통해 다음과 같은 state differential equaiton을 구할 수 있다.  

$$\mathbf{\dot{x}}(t)=\begin{bmatrix} 0&1 \\
-\dfrac{k}{M}&-\dfrac{b}{M}\\ \end{bmatrix} \mathbf{x}(t)+
\begin{bmatrix} 0 \\
\dfrac{1}{M}\\ \end{bmatrix} F(t)$$  

## P3.3
state variable이 $x_{1}(t)=i_{L}(t)$, $x_{2}(t)=v_{c}(t)$이므로  
KVL에 의해 아래와 같은 두 개의 1차 미분방정식이 구해진다.  

* $-v_{1}(t)+L\dfrac{dx_{1}(t)}{dt}-x_{2}(t)+v_{2}(t)=0$  
  $L\dfrac{dx_{1}(t)}{dt}=x_{2}(t)+v_{1}(t)-v_{2}(t)$  
  $\dfrac{dx_{1}(t)}{dt}=\dfrac{1}{L}x_{2}(t)+\dfrac{1}{L}v_{1}(t)-\dfrac{1}{L}v_{2}(t)$

* $Rx_{1}(t)-RC\dfrac{dx_{2}}{dt}+x_{2}(t)-v_{2}(t)=0$  
  $RC\dfrac{dx_{2}(t)}{dt}=-Rx_{1}(t)-x_{2}(t)+v_{2}(t)$  
  $\dfrac{dx_{2}(t)}{dt}=-\dfrac{1}{C}x_{1}(t)-\dfrac{1}{RC}x_{2}(t)+\dfrac{1}{RC}v_{2}(t)$

이를 state differential equation으로 나타내면 다음과 같다.  

$$\mathbf{\dot{x}}(t)=\begin{bmatrix} 0&\dfrac{1}{L} \\
-\dfrac{1}{C}&-\dfrac{1}{RC}\\ \end{bmatrix} \mathbf{x}(t)+
\begin{bmatrix} \dfrac{1}{L}&-\dfrac{1}{L} \\
0&\dfrac{1}{RC}\\ \end{bmatrix} \mathbf{v}(t)$$  

## P3.5
**(a) transfer function 구하기**  

주어진 그림에서 transfer function을 구해보면  

$T(s)=\dfrac{\dfrac{s+2}{s+8}\cdot\dfrac{1}{s-3}\cdot\dfrac{1}{s}}{1+\dfrac{s+2}{s+8}\cdot\dfrac{1}{s-3}\cdot\dfrac{1}{s}}=\dfrac{s+2}{s^{3}+5s^{2}-23s+2}$  

**(b) state variable model**  

phase variable form을 사용해 state variable model을 구해보면  

$$\begin{pmatrix}
x_{1}(t) \\
x_{2}(t) \\
x_{3}(t)
\end{pmatrix}=
\begin{pmatrix}
z(t) \\
\dot{x_{1}}(t) \\
\dot{x_{2}}(t)\end{pmatrix}=
\begin{pmatrix}
z(t) \\
\dot{z}(t) \\
\ddot{z}(t)\end{pmatrix}$$

$\dfrac{Y(s)}{R(s)}=\dfrac{s+2}{s^{3}+5s^{2}-23s+2}\cdot\dfrac{Z(s)}{Z(s)}$  
$y(t)=\dot{z}(t)+2z(t)$  
$r(t)=\dddot{z}(t)+5\ddot{z}(t)-23\dot{z}(t)+2z(t)$  

$\dot{x_{1}}(t)=x_{2}(t)$  
$\dot{x_{2}}(t)=x_{3}(t)$  
$\dot{x_{3}}(t)=\dddot{z}(t)=-5\ddot{z}(t)+23\dot{z}(t)-2z(t)+r(t)=-5x_{3}(t)+23x_{2}(t)-2x_{1}(t)+r(t)$  

위 식을 통해 아래의 state variable model을 구할 수 있다.

$$\mathbf{\dot{x}}(t)=\begin{bmatrix} 0&1&0 \\
0&0&1 \\
-2&23&-5\end{bmatrix} \mathbf{x}(t)+
\begin{bmatrix} 0 \\
0 \\
1 \\ \end{bmatrix} r(t)$$  

$$y(t)=\begin{bmatrix} 2&1&0 \\ \end{bmatrix} \mathbf{x}(t)$$  

## P3.12
**(a) state variable model**  

$\dfrac{Y(s)}{R(s)}=T(s)=\dfrac{8s+40}{s^{3}+12s^{2}+44s+48}$  

matlab을 이용해 state variable model을 구해보면  
```matlab
b = [0, 0, 8, 40];
a = [1, 12, 44, 48];
[A, B, C, D] = tf2ss(b, a);
```
```
A =

   -12   -44   -48
     1     0     0
     0     1     0


B =

     1
     0
     0


C =

     0     8    40


D =

     0
```
위 결과를 바탕으로 state variable model을 구해보면

$$\mathbf{\dot{x}}(t)=\begin{bmatrix} 0&1&0 \\
0&0&1 \\
-48&-44&-12\end{bmatrix} \mathbf{x}(t)+
\begin{bmatrix} 0 \\
0 \\
1 \\ \end{bmatrix} r(t)$$  

$$y(t)=\begin{bmatrix} 40&8&0 \\ \end{bmatrix} \mathbf{x}(t)$$  

**(b) state transition matrix**  

state transition matrix는 아래의 식과 같이 구할 수 있다.  

$\mathbf{\Phi}(s)=[s\mathbf{I}-\mathbf{A}]^{-1}$  
$\mathbf{\Phi}(t)=\mathcal{L}^{-1}[\mathbf{\Phi}(s)]$  

위에서 구한 $\mathbf{A}$을 대입해서 state transition matrix를 matlab으로 구해보면  
```matlab
syms s
A = [0, 1, 0; 0, 0, 1; -48, -44, -12];
Phi = ilaplace(inv(s*eye(3)-A));
```
```
Phi =
 
[     3*exp(-2*t) - 3*exp(-4*t) + exp(-6*t), (5*exp(-2*t))/4 - 2*exp(-4*t) + (3*exp(-6*t))/4,     exp(-2*t)/8 - exp(-4*t)/4 + exp(-6*t)/8]
[  12*exp(-4*t) - 6*exp(-2*t) - 6*exp(-6*t), 8*exp(-4*t) - (5*exp(-2*t))/2 - (9*exp(-6*t))/2,   exp(-4*t) - exp(-2*t)/4 - (3*exp(-6*t))/4]
[12*exp(-2*t) - 48*exp(-4*t) + 36*exp(-6*t),       5*exp(-2*t) - 32*exp(-4*t) + 27*exp(-6*t), exp(-2*t)/2 - 4*exp(-4*t) + (9*exp(-6*t))/2]
```

위 결과를 정리하면 아래와 같이 구해진다.  

$$\mathbf{\Phi}(t)=\begin{bmatrix} 
3e^{-2t}-3e^{-4}+e^{-6t} & \dfrac{5}{4}e^{-2t}-2e^{-4}+\dfrac{4}{3}e^{-6t} & \dfrac{1}{8}e^{-2t}-\dfrac{1}{4}e^{-4}+\dfrac{1}{8}e^{-6t} \\
-6e^{-2t}+12e^{-4}+-6e^{-6t} & -\dfrac{5}{2}e^{-2t}+8e^{-4}+-\dfrac{9}{2}e^{-6t} & -\dfrac{1}{4}e^{-2t}+e^{-4}-\dfrac{3}{4}e^{-6t} \\
12e^{-2t}-48e^{-4}+36e^{-6t} & 5e^{-2t}-32e^{-4}+27e^{-6t} & \dfrac{1}{2}e^{-2t}-4e^{-4}+\dfrac{9}{2}e^{-6t}
\end{bmatrix}$$

## P3.17
$$\mathbf{\dot{x}}(t)=\begin{bmatrix} 1&1&-1 \\
4&3&0 \\
-2&1&10\end{bmatrix} \mathbf{x}(t)+
\begin{bmatrix} 0 \\
0 \\
4 \\ \end{bmatrix} u(t)$$  

$$y(t)=\begin{bmatrix} 1&0&0 \\ \end{bmatrix} \mathbf{x}(t)$$  

state variable equation이 다음과 같이 주어져 있으므로 행렬 $\mathbf{A}, \mathbf{B}, \mathbf{C}, \mathbf{D}$는 아래와 같다.

$$\mathbf{A}=\begin{bmatrix} 1&1&-1 \\
4&3&0 \\
-2&1&10\end{bmatrix},
\mathbf{B}=\begin{bmatrix} 0 \\
0 \\
4\end{bmatrix},
\mathbf{C}=\begin{bmatrix} 0&0&4 \end{bmatrix},
\mathbf{D}=\mathbf{0}$$

transfer function $G(s)$는 아래와 같은 식으로 구할 수 있고  

$G(s)=\dfrac{Y(s)}{U(s)}=\mathbf{C}\mathbf{\Phi}(s)+\mathbf{D}$  

이를 matlab으로 구현해 보면  
```matlab
syms s
A = [1, 1, -1; 4, 3, 0; -2, 1, 10];
B = [0; 0; 4];
C = [1, 0, 0];
D = 0;
[num, den] = ss2tf(A, B, C, D);
```

```
num =

     0     0    -4    12


den =

    1.0000  -14.0000   37.0000   20.0000
```

위 실행 결과를 바탕으로 다음과 같은 transfer function을 구할 수 있다.  

$G(s)=\dfrac{-4s+12}{s^{3}-14s^{2}+37s+20}$
