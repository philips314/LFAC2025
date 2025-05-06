# Práctica 5 / Ejercicio 1  
## Dar expresiones regulares para los lenguajes de los ejercicios 1 a 3 de la práctica 2, a excepción de los incisos d y e del ejercicio 1.  
### Ejercicios del 1.  
Cadenas sobre Σ = {0} de longitud par: `(00)*`  
Cadenas sobre Σ = {0, 1} con cantidad par de ceros: `(01*0|1)*`  
Cadenas sobre Σ = {0, 1} con cantidad impar de unos: `(0|10*1*)*1(0|10*1)*`  
### Ejercicios del 2.  
Cadenas que comiencen con 010: `a`  
Cadenas que terminen con 010: `a`  
Cadenas que contengan la subcadena 000:  `a`  
Cadenas que no contengan la subcadena 000:   `a`  
### Ejercicios del 3.  
Identificadores de cualquier longitud que comiencen con una letra o guión y contengan letras, dígitos o guiones: `a`
Constantes enteras con signo: `a`  
Constantes enteras con signo opcional: `a`  
Constantes reales con signo: `a`  
Constantes reales con signo opcional y partes enteras y fraccionarias opcionales: `a`  
Constantes reales con notación exponencial opcional: `a`  
