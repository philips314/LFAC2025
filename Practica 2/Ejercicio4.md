# Práctica 2 / Ejercicio 4  
Dado un autómata finito $\mathscr{L}$, indicar cómo construir autómatas finitos para los siguientes lenguajes. Indicar en cada caso si es necesario que el autómata de entrada sea determinístico o no, y de qué tipo es el autómata resultante.  
## I. 
$\mathscr{L}^c$, el complemento de $\mathscr{L}$.  
```
Dado un AFD M=<Q,Σ,δ,q0,F> nos aseguramos que esté completo (agregamos estados trampa si los necesita) y armamos otro AFD M'=<Q,Σ,δ,q0,F'> donde F'=Q\F.
Es decir, invertimos los estados, consiguiendo el complemento de L.
```
