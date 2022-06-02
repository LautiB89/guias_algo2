$\bf{T(n)=T(n-2)+5}$

$$
T(n) = T(n-2) + 5 = T(n-4) + 10 = ... = T(n-2k) + 5k
$$
Donde k es la cantidad de veces que evalue la expresion  
Quiero parar de expandir la expresion cuando llegue a T(1)  
⟹   
Ocurre cuando n-2k = 1 ⟺ k = $\frac n 2$
T(n) = T(1) + $\frac 5 2$ n ⟹ T(n) ∈ O(n)

---

$\bf{T(n) = T(n-1) + n}$
$$
T(n) = T(n-1)+n = T(n-2) + (n-1) + n = \dots \\
T(n-k) + \sum_{j=0}^{k-1}n-j
$$
Expando la expesion hasta que n-k=1 ⟺  k = n-1
$$
T(n) = T(1) + \sum_{j=0}^{n-2}n-j = 
\text{cte} + \sum_{j=0}^{n-2}n - \sum_{j=0}^{n-2}j = \\
\text{cte} + (n-1)n - \frac{(n-2)(n-1)}{2} ∈ O(n^2)
$$

---

$\bf{T(n)=T(n-1)+\sqrt{n}}$
$$
T(n)=T(n-1)+\sqrt{n}=T(n-2)+\sqrt{n-1}+\sqrt{n} = \dots \\
T(n-k) + \sum_{j=n-k+1}^{n}j
$$
Quiero expandir la expresion hasta que n-k=1 ⟺ k=n-1  
$T(n)=T(1) + \sum_{j=2}^{n}\sqrt{j} ≤ T(1)+n\max{(\sqrt{n},\dots,\sqrt{2})}=T(1)+n\sqrt{2}∈ O(n)$  

---

$\bf{T(n)=T(n-1)+n^2}$
$$
T(n)=T(n-1)+n^2=T(n-2)+(n-1)^2+n^2=\dots\\
T(n-k)+\sum_{j=n-k+1}^{n}j^2
$$
Quiero que n-k=1 ⟺ k=n-1  
$$
T(n) =T(1)+\sum_{j=2}^{n}j^2 =
T(1)+\sum_{j=1}^{n}j^2 - 1 ∈ O(n^3)
$$

---

$\bf{T(n)=2T(n-1)}$
$$
T(n)=2T(n-1)=2^2T(n-2)=2^3T(n-3)=\dots=\\
2^kT(n-k)
$$
Quiero que n-k=1 ⟺ k=n-1
$$
T(n)=2^{n-1}T(1) ∈ O(2^n)
$$

---

$\bf{T(n)=T(n/2)+n}$
$$
T(n)=T(n/2)+n=T(n/2^2)+ \frac n 2 + n = \dots = \\ 
T(\frac n {2^k})+n\sum_{i=0}^{k-1}\frac{1}{2^i}
$$
Quiero que $\frac{n}{2^k}=1 ⟺ \log_2n=k$  
$$
T(n)=T(1)+n\sum_{i=0}^{\log_2n-1}\frac{1}{2^i}≤\\ 
T(1)+n(\log_2n)\max{\{1,\frac{1}{2},\frac{1}{4},\dots,\frac{1}{n-1}\}} =
T(1)+n(\log_2n)∈ O(n\log n)
$$

---

$\bf{T(n)=T(n/2)+n}$
## Falta la mitad...
