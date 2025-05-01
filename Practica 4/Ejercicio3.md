# Practica 4 / Ejercicio 3  
A tener en cuenta: DUDAS
```
Una ocurrencia de x está ligada si aparece adentro de una abstracción “λ x”.
Una ocurrencia de x está libre si no está ligada.
```
## a. Marcar las ocurrencias del término `x` como subtérmino en `λx: Nat. succ((λx: Nat. x) x)`.  
```
Hay dos ocurrencias de x:
{1}: En λx: Nat. succ(...) -> el x es un parámetro de la función
{2}: En (λx: Nat. x) -> el x dentro 
```
## b. Ocurre `x1` como subtérmino en `λx1 : Nat. succ(x2)`?  
```
```
## c. Ocurre `x (y z)` como subtérmino en `u x (y z)`?  
```
```
