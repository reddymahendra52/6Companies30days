# 4. Brackets in Matrix Chain Multiplication
## GFG(Geeks For Geeks)
### Prompt:
Given an array **p[]** of length **n** used to denote the dimensions of a series of matrices such that dimension of **i'th** matrix is **p[i] * p[i+1]**. 
There are a total of **n-1** matrices. Find the most efficient way to multiply these matrices together. 
The problem is not actually to perform the multiplications, but merely to decide in which order to perform the multiplications such that 
you need to perform minimum number of multiplications. There are many options to multiply a chain of matrices because matrix multiplication is associative i.e. 
no matter how one parenthesize the product, the result will be the same.

```java
class Solution{
     static String st="";
     static char name;
    
    static void printParenthesis(int i, int j, int n, int[][] bracket){
        
    	if (i == j){
    		st += name;
    		name++;
    		return;
    	}
    	st += '(';
    	printParenthesis(i, bracket[i][j], n,bracket);
    	printParenthesis(bracket[i][j] + 1, j,n, bracket);
    	st += ')';
    }
    
    static String matrixChainOrder(int p[], int n){
        int m[][]=new int[n][n];
    	int bracket[][]=new int[n][n];
    	for (int i = 1; i < n; i++)
    	    m[i][i] = 0;
    	for (int L = 2; L < n; L++){
    		for (int i = 1; i < n-L+1; i++){
    			int j = i+L-1;
    			m[i][j] = Integer.MAX_VALUE;
    			for (int k = i; k <= j-1; k++){
    				int q = m[i][k] + m[k+1][j] + p[i-1]*p[k]*p[j];
    				if (q < m[i][j]){
    					m[i][j] = q;
    					bracket[i][j] = k;
    				}
    			}
    		}
    	}
    	name = 'A';
    	st = "";
    	 printParenthesis(1, n-1, n, bracket);
    	return st;
    }
}

```
