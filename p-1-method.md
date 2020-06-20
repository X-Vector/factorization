# Brent-Pollard's ( P- 1 Method )

**Brent-Pollard's Method is based on (p - 1) has small factor .**
> Proof :

**Suppose we want factor a number n = p*q  where p is non trivial factor & (p - 1) has small factors = ![formula](https://render.githubusercontent.com/render/math?math=u1%20*%20u2%20*%20u3%20.....%20uk%20%20,%20ui%20%3C%20u) where (u) is upper bound if X0 ∈ Zp Where X0 ≠ 0**

**∴** ![formula](https://render.githubusercontent.com/render/math?math=X0^{x(p-1)}mod%20p=(X0^{x})^{(p-1)}mod%20p=1) (Fermat Therom)

**Let α =** ![formula](https://render.githubusercontent.com/render/math?math=X0^{x(p-1)}) 

**∴ α - 1 = 0 mod p where α ≠ 1**

**∴ p is divided α - 1 [ p | α - 1 ]**

**∴ we get Greatest common divisor between α - 1 and n it's equal p gcd(α - 1,n) = p**

**as we know we don't have The Value of p , but we have the properties of p which  (p - 1) has small factors =** ![formula](https://render.githubusercontent.com/render/math?math=u1%20*%20u2%20*%20u3%20.....%20uk%20%20,%20ui%20%3C%20u) .

**so we will get all prime factor and try all to get p then get q by dividing n/p**

> End of Proof :

# Algorithm of Factoring n By Brent-Pollard's ( P- 1 Method )

**The algorithm takes as its inputs n, the integer to be factored; and g(x) a polynomial in x computed modulo n In the original algorithm, g(x) =** ![formula](https://render.githubusercontent.com/render/math?math=x^{2}-1) **mod n, but nowadays it is more common to use g(x) =** ![formula](https://render.githubusercontent.com/render/math?math=x^{2}%2B1) **mod n the output is either a non-trivial factor of n, or failure. It performs the following steps**

```
    x ← 2
    y ← 2
    d ← 1
    while d = 1:
        x ← g(x)
        y ← g(g(y))
        d ← gcd(|x - y|, n)
    if d = n: 
        return "Error"
    else:
        return d
```

## Example of Factoring n with P- 1 Method

let n = 8051 and g(x) = ![formula](https://render.githubusercontent.com/render/math?math=x^{2}%2B1) mod n

| i  | x |	g(x)  | gcd(x-g(x),n) |
| ------------- | ------------- | ------------- | ------------- |
| 1  | 2  | 5  | 1  |
| 2  | 5  | 26  | 1  |
| 3  | 26  | 676  | 1  |
| 4  | 677  | 871  | 97  |


**97 is a non-trivial factor of 8051. Starting values other than x = y = 2 may give the cofactor (83) instead of 97. One extra iteration is shown above to make it clear that g(x) moves twice as fast as x. Note that even after a repetition, the GCD can return to 1.**
