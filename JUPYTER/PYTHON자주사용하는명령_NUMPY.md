# NUMPY

- 대각행렬 (Diagonal matrix): np.diag(x)
- 내적 (Dot product, Inner product): np.dot(a, b)
- 대각합 (Trace): np.trace(x)
- 행렬식 (Matrix Determinant): np.linalg.det(x)
- 역행렬 (Inverse of a matrix): np.linalg.inv(x)
- 고유값 (Eigenvalue), 고유벡터 (Eigenvector): w, v = np.linalg.eig(x)
- 특이값 분해 (Singular Value Decomposition): u, s, vh = np.linalg.svd(A)
- 연립방정식 해 풀기 (Solve a linear matrix equation): np.linalg.solve(a, b)
- 최소자승 해 풀기 (Compute the Least-squares solution): m, c = np.linalg.lstsq(A, y, rcond=None)[0]

## 1. 대각행렬 (Diagonal matrix): np.diag(x)

대각행렬은 대각성분 이외의 모든 성분이 모두 '0'인 n차 정방행렬을 말합니다. 아래 예시의 행렬에서 빨간색으로 표시한 원소를 '0'으로 바꾼 행렬이 대각행렬입니다.

```python
import numpy as np
x = np.arange(9).reshape(3, 3)
print(x)
[[0 1 2]
 [3 4 5]
 [6 7 8]]

np.diag(x)
array([0, 4, 8])

np.diag(np.diag(x))
array([[0, 0, 0],
        [0, 4, 0],
        [0, 0, 8]])
```

## 2. 내적 (Dot product, Inner product): np.dot(a, b), a.dot(b)
matrix dot product, inner product, scalar product, projection product

Python에서 '*' 를 사용한 두 행렬 간 곱은 원소 간 곱(element-wise product)을 반환하며, 선형대수에서 말하는 행렬 간 내적 곱을 위해서는 np.dot() 함수를 이용해야 합니다. 스칼라곱. 보통 내적은 벡터의 크기를 측정하는 용도

### 원소 간 곱 (element-wise product)

: a*b

```python
a = np.arange(4).reshape(2, 2)
print(a)
[[0 1]
 [2 3]]

a*a
array([[0, 1],
        [4, 9]])
```

### 내적 (dot product, inner product)

: np.dot(a, b)

```python
a = np.arange(4).reshape(2, 2)
print(a)
[[0 1]
 [2 3]]

np.dot(a, a)
array([[ 2, 3],
        [ 6, 11]])
```

np.dot(a, b) NumPy 함수와 a.dot(b)의 배열 메소드의 결과는 동일합니다.

```python
a.dot(a)
array([[ 2, 3],
        [ 6, 11]])
```

## 3. 대각합 (Trace): np.trace(x)
 


정방행렬의 대각에 위치한 원소를 전부 더해줍니다. 

아래의 2차 정방행렬 예의 대각합은 0+5+10+15 = 30 이 됩니다. (파란색으로 표시함)









In [12]: b = np.arange(16).reshape(4, 4)




In [13]: print(b)

[[ 0 1 2 3]

 [ 4 5 6 7]

 [ 8 9 10 11]

 [12 13 14 15]]




In [14]: np.trace(b)



Out[14]: 30

 
 







3차원 행렬에 대해서도 대각합을 구할 수 있습니다. 2차원은 대각선 부분의 원소 값을 전부 더하면 되지만 3차원 행렬에서는 대각(diagonal)이 어떻게 되나 좀 헷갈릴 수 있겠습니다. 아래의 3차원 행렬의 대각합을 구하는 예를 살펴보면, [0+12+24, 1+13+25, 2+14+26] = [36, 39, 42] 가 됩니다. 








In [15]: c = np.arange(27).reshape(3, 3, 3)




In [16]: print(c)

[[[ 0 1 2]

  [ 3 4 5]

  [ 6 7 8]]




 [[ 9 10 11]

  [12 13 14]

  [15 16 17]]




 [[18 19 20]

  [21 22 23]

  [24 25 26]]]




In [17]: np.trace(c)



Out[17]: array([36, 39, 42])

 
 












  4. 행렬식 (Matrix Determinant): np.linalg.det(x)
 




역행렬이 존재하는지 여부를 확인하는 방법으로 행렬식(determinant, 줄여서 det)이라는 지표를 사용합니다. 이 행렬식이 '0'이 아니면 역행렬이 존재하고, 이 행렬식이 '0'이면 역행렬이 존재하지 않습니다. 




* 참고 링크 : http://rfriend.tistory.com/142




아래의 예에서 array([[1, 2], [3, 4]]) 의 행렬식이 '-2.0'으로서, '0'이 아니므로 역행렬이 존재한다고 판단할 수 있습니다. 








In [18]: d = np.array([[1, 2], [3, 4]])




In [19]: np.linalg.det(a)



Out[19]: -2.0

 
 










  5. 역행렬 (Inverse of a matrix): np.linalg.inv(x)
 



역행렬은 n차정방행렬 Amn과의 곱이 항등행렬 또는 단위행렬 In이 되는 n차정방행렬을 말합니다. A*B 와 B*A 모두 순서에 상관없이 곱했을 때 단위행렬이 나오는 n차정방행렬이 있다면 역행렬이 존재하는 것입니다.



역행렬은 가우스 소거법(Gauss-Jordan elimination method), 혹은 여인수(cofactor method)로 풀 수 있습니다. 




* 참고 링크 : http://rfriend.tistory.com/142












In [20]: a = np.array(range(4)).reshape(2, 2)




In [21]: print(a)

[[0 1]

 [2 3]]




In [22]: a_inv = np.linalg.inv(a)




In [23]: a_inv

Out[23]: 

array([[-1.5, 0.5],

        [ 1. , 0. ]])



 







위의 예제에서 np.linalg.inv() 함수를 사용하여 푼 역행렬이 제대로 푼 것인지 확인을 해보겠습니다. 역행렬의 정의에 따라서 원래의 행렬에 역행렬을 곱하면, 즉, a.dot(a_inv) 또는 np.dot(a, a_inv) 를 하면 단위행렬(unit matrix)가 되는지 확인해보겠습니다. 









In [24]: a.dot(a_inv)

Out[24]:

array([[1., 0.],



         [0., 1.]])

 
 












  6. 고유값 (Eigenvalue), 고유벡터 (Eigenvector): w, v = np.linalg.eig(x)
 



정방행렬 A에 대하여 Ax = λx  (상수 λ) 가 성립하는 0이 아닌 벡터 x가 존재할 때 상수 λ 를 행렬 A의 고유값 (eigenvalue), x 를 이에 대응하는 고유벡터 (eigenvector) 라고 합니다. 



* 참고 링크 : http://rfriend.tistory.com/181, http://rfriend.tistory.com/182




np.linalg.eig() 함수는 고유값(eigenvalue) w, 고유벡터(eigenvector) v 의 두 개의 객체를 반환합니다. 









In [25]: e = np.array([[4, 2],[3, 5]])




In [26]: print(e)

[[4 2]

 [3 5]]




In [27]: w, v = np.linalg.eig(e)




#  w: the eigenvalues lambda

In [28]: print(w)

[2. 7.]




# v: the corresponding eigenvectors, one eigenvector per column

In [29]: print(v)

[[-0.70710678 -0.5547002 ]

 [ 0.70710678 -0.83205029]]

 
 







고유벡터는 배열 인덱싱하는 방법을 사용해서 각 고유값에 대응하는 고유벡터를 선택할 수 있습니다. 








# eigenvector of eigenvalue lambda 2

In [30]: print(v[:, 0]) 

[-0.70710678 0.70710678]




# eigenvector of eigenvalue labmda 7

In [31]: print(v[:, 1]) 


[-0.5547002 -0.83205029]

 
 












  7. 특이값 분해 (Singular Value Decomposition): u, s, vh = np.linalg.svd(A)
 




특이값 분해는 고유값 분해(eigen decomposition)처럼 행렬을 대각화하는 한 방법으로서, 정방행렬뿐만 아니라 모든 m x n 행렬에 대해 적용 가능합니다. 특이값 분해는 차원축소, 데이터 압축 등에 사용할 수 있습니다. 이론적인 부분은 설명하자면 너무 길기 때문에 이 포스팅에서는 설명하지 않겠으며, 아래의 링크를 참고하시기 바랍니다. 




* 참고 링크 : http://rfriend.tistory.com/185


아래의 np.linalg.svd(A) 예제는 위의 참고 링크에서 사용했던 예제와 동일한 것을 사용하였습니다. 









In [32]: A = np.array([[3,6], [2,3], [0,0], [0,0]])




In [33]: print(A)

[[3 6]

 [2 3]

 [0 0]

 [0 0]]




In [34]: u, s, vh = np.linalg.svd(A)




In [35]: print(u)

[[-0.8816746 -0.47185793 0. 0. ]

 [-0.47185793 0.8816746 0. 0. ]

 [ 0. 0. 1. 0. ]

 [ 0. 0. 0. 1. ]]




In [36]: print(s)

[7.60555128 0.39444872]




In [37]: print(vh)

[[-0.47185793 -0.8816746 ]



 [ 0.8816746 -0.47185793]]

 
 












  8. 연립방정식 해 풀기 (Solve a linear matrix equation): np.linalg.solve(a, b)
 




아래의 두 개 연립방정식의 해(x0, x1)를 np.linalg.solve(a, b) 함수를 사용하여 풀어보겠습니다. 









위의 연립방정식을 어떻게 행렬로 입력하고, np.linalg.solve(a, b)에 입력하는지 유심히 살펴보시기 바랍니다. 









In [38]: a = np.array([[4, 3], [3, 2]])




In [39]: b = np.array([23, 16])




In [40]: x = np.linalg.solve(a, b)




In [41]: print(x)



[2. 5.]

 
 







NumPy 가 제대로 x0, x1의 해를 풀었는지 확인해보겠습니다. x0=2, x1=5 가 해 맞네요!








In [42]: np.allclose(np.dot(a, x), b)



Out[42]: True

 
 












  9. 최소자승 해 풀기 (Compute the Least-squares solution)

     : m, c = np.linalg.lstsq(A, y, rcond=None)[0]
 




회귀모형 적합할 때 최소자승법(Least-squares method)으로 잔차 제곱합을 최소화하는 회귀계수를 추정합니다. 




* 참고 링크 : https://docs.scipy.org/doc/numpy/reference/generated/numpy.linalg.lstsq.html







아래의 예에서는 회귀계수 m, y절편 c를 최소자승법을 사용해서 구해보겠습니다. 








In [43]: x = np.array([0, 1, 2, 3])




In [44]: y = np.array([-1, 0.2, 0.9, 2.1])




In [45]: A = np.vstack([x, np.ones(len(x))]).T




In [46]: A

Out[46]: 

array([[0., 1.],

        [1., 1.],

        [2., 1.],

        [3., 1.]])




In [47]: m, c = np.linalg.lstsq(A, y, rcond=None)[0]




In [48]: print(m, c)



0.9999999999999999 -0.9499999999999997

 
 







아래의 그래프에서 점은 원래의 데이터이며, 빨간색 선은 최소자승법으로 추정한 회귀식의 적합선이 되겠습니다. 








In [49]: import matplotlib.pyplot as plt

    ...: plt.plot(x, y, 'o', label='Original data', markersize=10)

    ...: plt.plot(x, m*x + c, 'r', label='Fitted line')

    ...: plt.legend()



    ...: plt.show()





 


출처: https://rfriend.tistory.com/380 [R, Python 분석과 프로그래밍 (by R Friend)]