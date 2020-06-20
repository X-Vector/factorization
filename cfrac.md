# Continued Fraction Factorization Method (CFRAC)

- **The CFRAC method is a general purpose integer Factorization Method . First Describe By D.H Lehmer and R.E Powers in 1931 and published as a computer algorithm By Michal A. Morrison and John Brimhart in 1975 as a first general-purpose factorization algorithm with sub exponential running time.**

- **CFRAC is based on that the unique representation for the number using Continued Fraction find a numerical approximation for the square root of number of a relation number also using the same base of Legender's Congruence factorization method which representing n as differance of two square** ![f](https://render.githubusercontent.com/render/math?math=n+=+x^{2}%20-%20n*y^{2})

- **we can note that √n is irrational number so it will be represented as an infinite number of elements .**

- **i.e √n = [ a0 ; a1 , a2 ,..... ] = [a0 ; an] n ∈ N**

- **otherwise if  √n is integer we will done the require since if  √n  ϵ N**

- **∴ n =  √n  ,√n  is a factorization of n so it will give us an itaration process of a approximation .**

## Example of Factoring By Continued Fraction Factorization Method

- Let n = 3053

- First we compute  B as ![f](https://render.githubusercontent.com/render/math?math=exp(\frac{\sqrt{ln(n)%20*%20ln(ln(n))}}{2}))

- which in our case is : B = 7
 
- The next step is creating the factor base by iterating over the primes  p ≤ B and collecting those primes for which the [Kronecker symbol](https://en.wikipedia.org/wiki/Kronecker_symbol) ![f](https://render.githubusercontent.com/render/math?math=(\frac{n}{p})=1)

- It's generally a good idea to also allow  p=2 in the factor base. In our case, factor base =  {2,7}

- The next step is taking the product of all the primes in the factor base, as this product will be used in recognizing the B smooth quadratic residues that factor over our factor base, using the following efficient algorithm

```
 1 - Let n be the number to be tested.
 2 - Let k be the product of the primes in the factor base.
 3 - Compute the greatest common divisor:  g = gcd(n,k) .
 4 - If g is greater than 1, then  n = r * power(g,e)  for some  e ≥ 1
        - If r = 1 , then n is smooth over the factor base. 
        - Otherwise, set  n = r and go to step 3.
 If this step is reached, then  n is not smooth.
```

- For  n = 3053 , the following table shows the square root convergents ![f](https://render.githubusercontent.com/render/math?math=(\frac{A_{k}}{B_{k}})) along with the quadratic residues ![f](https://render.githubusercontent.com/render/math?math=A_{k}^{2}) ≡ ![f](https://render.githubusercontent.com/render/math?math=A_{k}) mod n , where ![f](https://render.githubusercontent.com/render/math?math=|A_{k}^{2}\+mod\+n|) ≤ ![f](https://render.githubusercontent.com/render/math?math=2\sqrt{2})

|   A_k / B_k    | A_k mod n | (A_k)^2 mod n  |
| ----------- | ----------- | ----------- |
|     55 / 1     |     55    | -28 = -2^2 * 7 |
|    166 / 3     |    166    |  79 = 79       |
|    221 / 4     |    221    |  -7 = -7       |
|   3481 / 63    |    428    |   4 = 2^2      |
|  94208 / 1705  |   2618    | -61 = -61      |
|  97689 / 1768  |   3046    |  49 = 7^2      |

- Each quadratic residue  ∣ ![f](https://render.githubusercontent.com/render/math?math=A_{k}^{2}) mod n ∣ that factors over the factor base, along with  ![f](https://render.githubusercontent.com/render/math?math=A_{k}) mod n , are stored into an array as pairs  [ ![f](https://render.githubusercontent.com/render/math?math=A_{k}) mod n | ![f](https://render.githubusercontent.com/render/math?math=A_{k}^{2}) mod n |] :

Q = 
(
[  55, 28]

[ 221,  7]

[ 428,  4]

[3046, 49]
)
    
- Since each quadratic residue that passes the smoothness test is B-smooth, we can easily factorize it using [trial division](https://github.com/X-Vector/factorization/blob/master/Trial-Division-Method.md) over the primes  p ≤ B , from which we create a matrix of vector exponents, where the number of columns is the number of primes in the factor base, while the number of rows should be at least one more than the number of columns to ensure a linear dependency exists.

A = [
[2, 1],       # ![f](https://render.githubusercontent.com/render/math?math=28=2^{2}*7^{1})
    
[0, 1],       # ![f](https://render.githubusercontent.com/render/math?math=7=2^{0}*7^{1})

[2, 0],       # ![f](https://render.githubusercontent.com/render/math?math=4=2^{2}*7^{0})
    
[0, 2],       # ![f](https://render.githubusercontent.com/render/math?math=49=2^{0}*7^{2})
]

- The key idea here is taking advantage of the following elementary identity: ![f](https://render.githubusercontent.com/render/math?math=p^{a}.p^{b}=p^{a%2Bb}) and the fact that a square has an even exponent (e.g.: ![f](https://render.githubusercontent.com/render/math?math=x^{2},x^{4},x^{6},%20....)) which allows us to work modulo 2 and efficiently find a linear dependency using a linear algebra algorithm, such as [Gaussian elimination](https://en.wikipedia.org/wiki/Gaussian_elimination) over a GF(2) matrix, where each vector exponent is a base-2 encoded integer.

- This allows us to find a subset of vector exponents, such that when all these vectors are added together entrywise, the resulting vector will contain only even exponents.

- In our case, the first linear dependency found is: [2,1] + [0,1] = [2,2]

- meaning that 28 * 7 is a square, namely : ![f](https://render.githubusercontent.com/render/math?math=2^{2}.7^{2})

 
- y = 28 * 7 = ![f](https://render.githubusercontent.com/render/math?math=14^{2})

- x = 55 * 221 = 12155

- This means that ![f](https://render.githubusercontent.com/render/math?math=12155^{2}) ≡ ![f](https://render.githubusercontent.com/render/math?math=14^{2}) mod n , allowing us to factorize  n as:
 
- n = gcd(12155 + 14 , n) *  gcd(12155 − 14 , n)

- concluding the factorization:

- n = 43 * 71
