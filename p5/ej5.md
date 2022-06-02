### Ejercicio 5 $\star$
Se tiene un arreglo de n números naturales que se quiere ordenar por frecuencia, y en caso de igual frecuencia, por su valor. Por ejemplo, a partir del arreglo [1, 3, 1, 7, 2, 7, 1, 7, 3] se quiere obtener [1, 1, 1, 7, 7, 7, 3, 3, 2].  
Describa un algoritmo que realice el ordenamiento descrito, utilizando las estructuras de datos intermedias que
considere necesarias. Calcule el orden de complejidad temporal del algoritmo propuesto.  

```
ordenarFrecuencia(in/out a: arreglo(nat) )
    MergeSort(a)
    d: arreglo(⟨nat, nat⟩) ← Compactar(a)
    MergeSort(d) //Ordena comparando los segundos valores de las tuplas
    a ← Descompactar(d)
```

### Auxiliares

```
Compactar(in a: arreglo(nat)) → res: arreglo(⟨nat, nat⟩)
    //Recibe un arreglo ordenado a y devuelve un arreglo de tuplas donde:
    //  El primer elemento de c/tupla corresponde a cada elemento del arreglo a
    //  El segundo elemento de c/tupla corresponde a la cantidad de apariciones del elemento en a
    //La cantidad de tuplas es la cantidad de elementos unicos en el arreglo a
    //Ejemplo de uso: [1,1,2,2,2,4] → compactar → [⟨1,2⟩, ⟨2,3⟩, ⟨4,1⟩]

    cantElemDistintos ← 0
    if tamaño(a) > 0 then    
        ultimoElem ← a[0]
        cantElemDistintos ++
        for i =0...tamaño(a)-1:
            if ultimoElem ≠ a[i] then
                cantElemDistintos ++
                ultimoElem ← a[i]
            endif
        endfor
    endif

    res ← CrearArreglo(cantElemDistintos)
    nat i ← 0
    nat j ← 0 
    while i < tamaño(a):
        nat cant ← 0
        nat elemAContar ← a[i]
        while i < tamaño(a) ∧ elemAContar = a[i]:
            cant++
            i++
        endwhile
        res[j] ← ⟨elemAContar, cant⟩
        j++
    endwhile
```

```
Descompactar(in d: arreglo⟨nat,nat⟩) → a: arreglo(nat)
    //Recibe un arreglo de tuplas donde:
    //  El primer elemento de c/tupla corresponde a cada elemento del arreglo a
    //  El segundo elemento de c/tupla corresponde a la cantidad de apariciones del elemento en a
    //La cantidad de tuplas es la cantidad de elementos unicos en el arreglo a
    //Ejemplo de uso: [⟨1,2⟩, ⟨2,3⟩, ⟨4,1⟩] → descompactar → [1,1,2,2,2,4] 

    //calculo tamaño de a
    tamañoA ← 0
    for i = 0..tamaño(d)-1:
        tamañoA += π₂(d[i])
    endfor

    a ← CrearArreglo(tamañoA)
    
    nat i ← 0 //Indice de d
    nat j ← 0 //Indice de a

    while i < tamaño(d):
        elemAgregar ← π₁(d[i])
        for k = j..j + π₂(d[i]) - 1
            a[k] ← elemAgregar
        endfor
        j += π₂(d[i])
        i++

    endwhile
```

### Complejidad
MergeSort es $O(n \log n)$.  
Compactar es $O(n)$ (por recibir la lista ordenada como pre).  
Descompactar es $O(n)$.

El algoritmo tiene complejidad $O(\text{suma de las complejidades})$, por ende es $O(n\log n)$