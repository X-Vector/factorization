# Legender's Congruence 

- Every Subsequent method for integer factorization is based on Simpler Observation based on Legender's Congruence introduced By Adrien-Marle legender (1752 - 1833)

> proof :

- if we want factorization number n which is composed of factor p,q ϵ P ( set of all prime number ) There exist congruence of form ![f](https://render.githubusercontent.com/render/math?math=x^{2}) ≡ ![f](https://render.githubusercontent.com/render/math?math=y^{2}) mod n and y ≠ x mod n Where x,y ϵ ( 2 , 3 , ..... n - 1 ) 

- This Congruence can Be Written as ![f](https://render.githubusercontent.com/render/math?math=x^{2}%20-%20y^{2}) ≡ ( X - Y ) ( X + Y ) ≡ 0 mod n 
  which lead us to that p | (x - y) (x + y) and q | (x-y)(x+y) because of condition and x ≠ y mod n .
  
- There are only two option for each Condition .

- First Condition consider if p | (x - y)(x + y) is chosen .

- Then We have that p | (x - y) and p * x (x + y)  or  p * x (x - y) and p | (x + y)

- but if p | (x - y) and p | (x + y) 

- ∴ n | (x - y) or n | (x + y) 

- ∴ (x - y = k1 * n) or (x + y = k2 * n) 

- ∴ x = y + k1 * n or x = k2 * n - y 

- ∴ x ≡ y mod n or x ≡ -y mod n  which is contradict with our condition

- ∴ p | (x - y) and p*x (x + y)  or  p*x (x - y) and p | (x + y)

- **at the first case** if p | (x - y) and p*x (x + y)  we must have that q*x (x - y) if q | (x - y)

- we will have n | (x - y)  → x ≡ y mod n ( contradiction )

- ∴ q*x (x - y) but q | (x + y)(x - y) , q ϵ P

- ∴ q | (x - y) 			∴ gcd( x - y , n) = p , gcd( x + y , n) = q

- **at the second case** if p*x (x - y) and p | (x + y)

- we must have that q*x (x + y) or if q | (x + y) → n | (x + y) → x ≡ -y mod n (contradiction)

- ∴ qx (x - y) but q | (x + y)(x - y) , q ϵ P

- ∴ q | (x - y) 			∴ gcd(x-y , n) = p , gcd(x+y , n) = q

- In order word if we can get x and y such that ![f](https://render.githubusercontent.com/render/math?math=x^{2}) ≡ ![f](https://render.githubusercontent.com/render/math?math=y^{2}) mod n and X ≠±Y mod n

- then we can calculate easily the value of gcd( x+ y , n) By The Euclidean Algorithm Which is usable for this Purpose , so the principle of factorization based on legender's congruence is behind all modern method of factorization . 

> End of proof :

## Example of Factoring By Legender's Congruence 

- Let N = 119 and m = 144 = ![f](https://render.githubusercontent.com/render/math?math=12^{2})

- **∴** ![f](https://render.githubusercontent.com/render/math?math=12^{2}) mod 119 = ![f](https://render.githubusercontent.com/render/math?math=5^{2}) mod 119 . 

- **∴** (d1,d2) = (gcd(12+5,119) , gcd(12-5,119)) = (17,7)  

- where n = 119 = 17 * 7
