# 2.Numerical_Differentiation
  **주의 사항**
## using for
- Data 값들을 이용해 미분값을 구한다. 
## 1st Differentiation
### Kind of method
  ### 3-point forward 
   **Main formular**

$f'(x_{i})=\frac{-3f(x_{i})+4f(x_{i+1})-f(x_{i+2})}{2h}$
   
  ### 2-point central
   
   **Main formular**
   
$f'(x_{i})=\frac{f(x_{i+1})-f(x_{i-1})}{2h}$
    
  ### 3-point-backward
   **Main formular**

$f'(x_{i})=\frac{3f(x_{i})-4f(x_{i-1})+f(x_{i-2})}{2h}$
  
## Main Idea
- 첫 번째 미분값은 3-forward method를 이용해 얻고 마지막 미분 값은 3-point backward method를 이용해 얻는다. 그외의 중간의 미분 값들은 # 2-point central method를 사용하여 구한다. 

## Code
```C
void gradient1D(double x[], double y[], double dydx[], int N) {
	// Check if length x and y are equal	
	//check number of data(N)
	if (N < 3) {
	printf("ERROR: length of data must be more than three\n");
		return;
	}
	if (sizeof(x) != sizeof(y)) {
		printf("ERROR: length of x and y must be equal\n");
		return;
	}
	double h = x[1] - x[0];
	dydx[0] = 0; 
	dydx[N - 1] = 0;

	dydx[0] = (-3. * y[0] + 4. * y[1] - y[2]) / (2. * h); // forward three point diff
	for (int i = 1; i < N - 1; i++) {
		dydx[i] = (y[i + 1] - y[i - 1]) / (2 * h);//2-point central diff
	}
	dydx[N - 1] = (3 * y[N - 1] - 4 * y[N - 2] + y[N - 3]) / (2 * h); // backward three point diff
}
```

## Ex code
```C
define Parameter
int main(){
x[n] = {x1 x2 x3 ... xn};
y[n] = {y1 y2 y3 ... yn};

double h = (x[i+1]-x[i]);
int N = (x[n]-x[0])/h;
 gradient1D(x[], y[], dydx[], N);
}
```

