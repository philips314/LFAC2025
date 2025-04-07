# Práctica 2 / Ejercicio 4  
Dado un autómata finito $\mathscr{L}$, indicar cómo construir autómatas finitos para los siguientes lenguajes. Indicar en cada caso si es necesario que el autómata de entrada sea determinístico o no, y de qué tipo es el autómata resultante.  
## I. 
$ℒ^c$, el complemento de ℒ.  
```
Dado un AFD M=<Q,Σ,δ,q0,F> nos aseguramos que esté completo (agregamos estados trampa si los necesita)
y armamos otro AFD M'=<Q,Σ,δ,q0,F'> donde F'=Q\F.
Es decir, invertimos los estados, consiguiendo el complemento de L.
```
## II.  
$ℒ^{*}$, la clausura de Kleene de ℒ.  
```
Dado un AFD M=<Q,Σ,δ,q0,F> construimos un AFND-λ M'=<Q',Σ,δ',q0',F'>
Donde:
* Q' = Q U {q0',qf'}
* F' = {qf'}
* δ' : Q' x (Σ U {λ}) -> P(Q') donde:
  * δ'(q0', λ) = {q0,q0'} 
  * δ'(qf, λ) = {qf'}
  * δ'(q,a) = δ(q,a) si q pertenece a los Q de M y a pertenece al alfabeto Σ.
* q0' es un estado inicial nuevo que se conecta al q0 de M con la transición λ.
* qf' es un estado final que se conecta a todo estado final de M con una transición λ.
* qf' tambien es conecta al estado inicial q0' con una transición λ para poder repetir el proceso.
* En relación a F', los estados finales de M ya no son finales en M'

No importa el determinismo de M.
```
<img src="./Images/4ej2.png" style="width: 500px;">  

## III.  
$ℒ^r$, la reversa de ℒ.  
```
Desarrollo↓
```
Dado un AFD $M=<Q,Σ,δ,q_0,F>$ definimos otro AFND-λ $M^r = <Q',Σ,δ^r,q_0',F'>$ tal que:  
* Q' = Q U { $q_0'$ }  (nuevo inicial)
* $δ^r(q_0',λ) = F \quad$(empieza por los finales)
* $(q_2 \in δ^r(q_1,a)) \leftrightarrow (q_1 \in δ(q_2,a)) \quad$(invertir las flechas)
* F' = { $q_0$ }  (termina en el estado que era inicial)

## IV.  
Ini(ℒ) = {𝛼 | ∃𝛽 tal que 𝛼𝛽 ∈ ℒ}, los prefijos de ℒ
```
Dado un autómata M=<Q,Σ,δ,q0,F>, construimos otro autómata M'=<Q,Σ,δ,q0,F'> donde:
* F' son todos los estados de Q que pertenecen a cualquiera de los caminos de aceptación.
 * Es decir, en F' pertenecen los estados que estan en algún camino entre q0 y un qf ∈ F.
 * F' ⊆ Q
* M' preserva el determinismo de M.
* L(M′) = Ini(L(M))
```

## V.  
Fin(ℒ) = {𝛼 | ∃𝛾 tal que 𝛾𝛼 ∈ ℒ}, los sufijos de ℒ  
```
Dado un autómata M=<Q,Σ,δ,q0,F>, construimos otro autómata M'=<Q,Σ,δ',q0,F> donde:
* Extendemos δ, agregando transiciones vacias (λ) desde el estado inicial q0 hacia todos los estados
  de Q que esten en algún camino entre q0 y algún estado final qf ∈ F.
```


## VI.  
Sub(ℒ) = {𝛼 | ∃(𝛽, 𝛾) tales que 𝛾𝛼𝛽 ∈ ℒ}, las subcadenas de ℒ  
```
Dado un autómata M=<Q,Σ,δ,q0,F>, construimos otro autómata M' donde:
* Combinamos lo modificado en el autómata sufijos y en el autómata prefijos, obteniendo a las subcadenas.
```


## VII.  
Máx(ℒ) = {𝛼 ∈ ℒ | ∀𝜔 ∈ $Σ^+$, 𝛼𝜔 ∉ ℒ}, las cadenas maximales de ℒ  
```
Dado un autómata M=<Q,Σ,δ,q0,F>, construimos otro autómata M'=<Q,Σ,δ,q0,F'> donde:
* F' ⊆ F, y para todo camino de aceptación desde q0 que pasa por varios estados finales, solo
  nos quedamos con los últimos de cada camino.
* Es decir, en M' no podemos aceptar más cadenas a partir del estado final.
* Si M tiene un estado final dento de un ciclo (M acepta cadenas
  arbitrariamente largas), modificamos ese estado para que no sea final en F'.
* L(M′) = Máx(L(M))
```


## VIII.  
Mín(ℒ) = {𝛼 ∈ ℒ | ningún prefijo propio de 𝛼 pertenece a ℒ}, las cadenas minimales de ℒ.  
Es decir, Mín(ℒ) = {𝛼 ∈ ℒ | ∄($𝜔_1$, $𝜔_2$) tales que 𝛼 = $𝜔_1𝜔_2$ ∧ $𝜔_1$ ∈ ℒ ∧ $𝜔_2 \neq$  𝜆}.  
```
Dado un autómata M=<Q,Σ,δ,q0,F>, construimos otro autómata M'=<Q,Σ,δ',q0,F'> donde:
* F' ⊆ F, y para todo camino de aceptación desde q0 que pasa por varios estados finales, solo
  nos quedamos con los primeros de cada camino.
* En δ' sacamos todas las transiciones (en δ) desde cualquiera de los estados finales en F'.
* Es necesario pedir que M sea un AFD para garantizar que no exista otro camino distinto que acepte
  como prefijos a las cadenas min.
```

## X.  
$ℒ_𝑇$ = {𝛼 ∈ $Σ^∗$| ∃($𝜔_1$ ∈ ℒ, $𝜔_2$ ∈ $Σ^∗$) tales que 𝛼 = $𝜔_1𝜔_2$} = $ℒ.Σ^*$
```
Closure por sufijos a derecha (right-quotient closure).
ℒ𝑇 es el conjunto de todas las cadenas que empiezan con una cadena de ℒ, y le siguen cadenas de Σ*.
Dado un autómata M=<Q,Σ,δ,q0,F>, construimos otro autómata M'=<Q,Σ,δ',q0,F> donde:
* En δ' extendemos a δ agregando transiciones desde cada estado final hacía si mismo para todo símbolo de Σ.
* Así, una vez que el autómata alcanza un estado final, acepta cualquier continuación.
```
