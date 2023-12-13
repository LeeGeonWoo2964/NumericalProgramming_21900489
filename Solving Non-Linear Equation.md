# Solving Non-Linear Equation. 
 **수식의 꼴은 $f(x)=0$이 되어야 한다.**
 ## Function in Matlab what we made: fzero(@func,t1)
   - define parameter
   - @func: 우리가 풀고 싶은 비선형 수식
   - t1: 비선형 수식의 입력 초깃값
## Kind of method 
 ### Bisection method
 ### Newton-Rapson method
 ### Secant's method

## Bisection method 
 - Condition
   - 범위[a,b] 내에서 연속적일 것
   - 범위[a,b] 내에서 Solution이 존재할 것
   - a와 b 곱이 음수일 것
 ### Main Idea
   **$x{_N}=\frac{a+b}{2}$**
   
   **$f(x_{N})*f(a)<0$ >> $x_{N}=b$***
   
   **$f(x_{N})*f(a)>0$ >> $x_{N}=a$***
     
     위의 과정을 우리가 원하는 오차 범위 내로 들어올 때까지 반복한다. 

<img width="451" alt="image" src="https://github.com/LeeGeonWoo2964/NumericalProgramming_21900489/assets/145029302/5d5d8c5c-7f70-4cc0-a28a-49e566a9f2c0">


### Define Tolerance $Tol_{f(x)}(k)=|f(x{_N})|$

```c
```
