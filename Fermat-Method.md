# Fermat Method

**Fermat Method is based on the Legender's Congruence as the difference of two squares ![formula](https://render.githubusercontent.com/render/math?math=N%20=%20a^{2}%20-%20b^{2})
 That difference is algebraically factorable as (a+b)(a-b); if neither factor equals one, it is a proper factorization of N.**

> Proof :

Let n = p*q , then n can be factorize if (p-q) = ![formula](https://render.githubusercontent.com/render/math?math=O(n)^{0.25})

since  ![formula](https://render.githubusercontent.com/render/math?math=(p%2Bq)^{2}) - 4n =  ![formula](https://render.githubusercontent.com/render/math?math=(p-q)^{2})

since ![formula](https://render.githubusercontent.com/render/math?math=(p%2Bq)^{2}) - 4n = [p + q + 2√n] * [p + q - 2√n]

∴ p + q - 2√n = ((p - q)(p - q)) / (p + q - 2√n)

if p , q is same bit size then p , q is O(√n)	

∴ p + q - 2√n = ((p - q)(p - q)) / (O(√n))     → (1)

if (p-q) = ![formula](https://render.githubusercontent.com/render/math?math=O(n)^{0.25})

∴ ![formula](https://render.githubusercontent.com/render/math?math=(p-q)^{2})  = O(√n) → (2)

∴ from (1) , (2)

((p - q)(p - q)) / (O(√n)) = O(1)

this mean that (p + q) is very nearest to 2√n 

∴ (p + q) = 2√n + O(1)

where O(1) is very limited number 

> End of Proof :

# Algorithm of Factoring n By Fermat Method

```
fermat(n):
	a = √n , b = √n , c = a*a - √n 
	while b*b ≠ c :
		a = a + 1
		c = a*a - n
    b = √c
    if b > n :
        return "Can't Factorize n"
	p = a+b
	q = a-b
	return p,q
```

# Example

```
let n = 35

a = 5	c = 5*5 - 5 = 20	b = 5
 
while b * b ≠ c :
  // a = a + 1
  // c = a*a - n
  // b = √c
	a = 6	c = 6*6 - 35 = 1	b = 1

∴ p = a + b = 7
∴ q = a - b = 5

∴ Then The two prime number is ( 7 , 5 )

```
