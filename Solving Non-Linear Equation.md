# Solving Non-Linear Equation. 
 **수식의 꼴은 $f(x)=0$이 되어야 한다.**
 ## Function in Matlab what we made: fzero(@func,t1)
   - define parameter
   - @func: 우리가 풀고 싶은 비선형 수식
   - t1: 비선형 수식의 입력 초깃값
## Kind of method 
 ### Bisection method
 ### Newton-Rapson method (we use)
 ### Secant's method

## Newton-Rapson method
**변곡점($\frac{df(x)}{dx}=0$)에서 오류가 난다.**

**$\frac{df(x)}{dx}=0$을 손으로 구해야한다.**
- Condition
-   범위 내에서 연속
-   범위 내에서 미분 가능 할 것
-   해와 가까이에 있는 초깃값을 잘 잡을 것

### Main formular
$x_{k+1}=x_{k}-\frac{f(x_{k})}{f'{x_{k}}}$

$x_{k+1}-x_{k}=h_{k}$

<img width="380" alt="image" src="https://github.com/LeeGeonWoo2964/NumericalProgramming_21900489/assets/145029302/1d64586f-2288-44d9-947b-840aa9c43b06">

## Repeat Condition
$|\frac{x_{k+1}-x_{k}}{x_{k}}|<=ε(ep)$ or $|f(x_{k})|<=δ(delta)$

$x_{k+1},x_{k}$의 차이가 유의미하지 않을 때 까지 반복한다.
$|f(x_{k})|$가 거의 0과 같으면 해를 찾았다고 본다. 

## Code
```c
double newtonRaphson(double func(double x), double dfunc(double x), double x0, double tol) {
/*define input parameter
double func(double x): 풀고자 하는 수식
double dfunc(double x): 수식을 미분한 수식
double x0: 초깃값
double tol: 오차 허용값
*/
	double xn = x0; // xn
	double xn1 = 0; //xn+1
	int k = 0; // 실행횟수
	int Nmax = 1000; // 최대 실행횟수
	double h = 0;
	double ep = 0.00001;
	do
	{
		xn = xn1;
		if (dfunc(xn) == 0) {
			printf("Error df = 0\n");
			return 0;
		}
		else {
			ep = func(xn);
			h = -func(xn) / dfunc(xn);
			/*printf("f = %lf\n", func(xn));
			printf("df = %lf\n", dfunc(xn));*/
			xn1 = xn + h;
			k++;
			/*printf("h = %lf\n", h);
			printf("k = %d\n", k);*/
			printf("Iteration : %d\t X(n): %lf\t Tolerance: %lf\n", k, xn, func(xn));
		}
	} while (k <= Nmax && fabs(func(xn)) >= tol);

	return xn;
}
```

## Example 
```C
double x0 = 3;
double tol = 0.000001;
double Result = newtonRaphson(func, dfunc, x0, tol);
//define func,dfunc

double func (double xn){
~~
return Result;
}

double dfunc (double xn){
~~
return Result;
}

```


 
