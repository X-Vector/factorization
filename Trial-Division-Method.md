# **Trial Division Method**

**Trial Division based on the smallest positive divisor of any positive integer must be prime .**

**The Simplest factoring algorithm is the trial division method , which tries all the possible division of n to obtain it's complete prime number factorization Where n = p1 p2  p3  p4  p5  p6 ... pm** 

> Proof :

    let a is smallest positive divisor of n and a is not prime 		   (1)

    i.e : ah = n for some integer h

    ∴ we will have that a must be composite number

    i.e : there exist s,r integers such that s,r > 1 and a = sr		   (2)

    i.e : n = (sr)h = s(rh)

    i.e : s is also divides n 		[n | s]				   (3)

    from (1) , (3) we can see that a is not smallest positive divisor so there is a contradiction 

	Truth we have that the smallest  positive divisor of any positive integer must be prime.

> End of Proof

### Algorithm of Factoring n By Trial Division Method

This Algorithm factorize an integer n where n > 1 

	[1] input n and set t = 0 , k = 2

  	[2] if n = 1 Then :
    	go to [5]

  	[3] q = devided(n,k) and r = n % k
        if r ≠ 0 Then :
        	go to [4]
        t = t+1 
        pt = k 
        n = q 
        go to [2] 

	[4] if q greater than k , then :
    		k = k + 1 go to [3]
    	    t = t+1 
            pt = n

	[5] Exit

**We Can use This Algorithm to check if n is prime or not By trying all possible number less than square root n and greater than 1 ;  2 <= i < sqrt(n)**

	TrialDivision(n):

      i = 2 , k = sqrt(n)

      while i small than or equal k :

          if(n % i == 0)

              return Not_Prime

          i += 1

      return Prime
