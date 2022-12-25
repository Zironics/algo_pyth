# algo_pyth

import numpy as np

def norme(X):
    X = np.array(X)
    return np.sqrt(np.sum(X**2))

def landa(A,X):
    return norme(A@X)

def X_iter(A,X):
    D = A@X
    return D/norme(D)

def cond(j,i,e):
    return (j-i < e)

def algorithme(A,X,e):
    i = 0
    while True : 
        X = X_iter(A,X)
        j = landa(A,X)
        if cond(j,i,e) : 
            break
        i =  j
    return X

A =np.array([[1,2,3],[1,2,1],[3,2,1]])
X = np.array([1,1,1])
e = 0.5

r = algorithme(A,X,e)
print(r)
