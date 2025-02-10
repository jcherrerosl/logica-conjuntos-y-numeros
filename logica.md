# Lógica proposicional y operadores lógicos  

## Definición de proposición lógica  
Una **proposición lógica** es una afirmación que puede ser **verdadera** o **falsa**, pero no ambas a la vez.  

Ejemplos de proposiciones:  
- "2 es un número par." ✅ (Verdadera)  
- "5 es divisible por 2." ❌ (Falsa)  
- "¿Qué hora es?" ❌ (No es proposición porque no tiene valor de verdad).  

---

## Operadores lógicos fundamentales  

En lógica matemática, los operadores lógicos se utilizan para **modificar y combinar proposiciones**.  

| Operador       | Símbolo matemático |
|---------------|------------------|
| **Negación**  | ¬A           
| **Conjunción (Y)** | A ∧ B     
| **Disyunción (O)** | A ∨ B      
| **Implicación** | A → B    
| **Bicondicional** | A ↔ B  

Estos operadores permiten construir proposiciones más complejas y analizar sus relaciones lógicas.  

---

## **Negación en lógica proposicional**  

La **negación** de una proposición cambia su valor de verdad.  
Si una proposición es verdadera, su negación será falsa, y viceversa.  

Ejemplo:  
- **Proposición:** "Madrid es la capital de España."  
- **Negación:** "Madrid no es la capital de España."  

Formalmente, si **A** es una proposición, su negación se expresa como:  

- **Símbolo:** ¬A  
- **Lectura:** "No A" o "Es falso que A".  

Ejemplos en lenguaje natural:  
- **A:** "Está lloviendo."  
- **¬A:** "No está lloviendo."  

- **A:** "Todos los estudiantes aprobaron el examen."  
- **¬A:** "No todos los estudiantes aprobaron el examen." _(equivalente a "Al menos uno no aprobó")._  

---

## **Negación de proposiciones cuantificadas**  

Cuando una proposición involucra **cuantificadores** como "para todo" (∀) o "existe" (∃), su negación sigue reglas específicas:  

| Proposición original | Negación |
|----------------------|---------|
| ∀x P(x)  _(Para todo x, P es verdadera)_ | ∃x ¬P(x)  _(Existe al menos un x donde P es falsa)_ |
| ∃x P(x)  _(Existe algún x donde P es verdadera)_ | ∀x ¬P(x)  _(Para todo x, P es falsa)_ |

Ejemplo en lenguaje natural:  
- **Proposición:** "Todos los gatos son negros." _(∀x, si x es un gato, entonces x es negro)._  
- **Negación:** "Existe al menos un gato que no es negro." _(∃x tal que x es un gato y x no es negro)._  

- **Proposición:** "Hay al menos una persona que sabe ruso." _(∃x, x sabe ruso.)_  
- **Negación:** "Nadie sabe ruso." _(∀x, x no sabe ruso.)_  

---

## **Notación en programación**  

Hasta ahora hemos trabajado con la notación matemática tradicional. Sin embargo, en programación, los operadores lógicos pueden tener una sintaxis diferente dependiendo del lenguaje.  

En algunos lenguajes de alto nivel, como **Python**, los operadores se escriben en inglés:  
- `not A` (negación)  
- `and` (conjunción)  
- `or` (disyunción)  

Pero en la mayoría de los lenguajes más cercanos al hardware, como **C, C++, Java**, se utilizan símbolos específicos:  
- `!A` para la negación (¬A).  
- `A && B` para la conjunción (A ∧ B).  
- `A || B` para la disyunción (A ∨ B).  

A lo largo de este documento, utilizaremos **C** para ilustrar la aplicación de la lógica proposicional en programación. C es un lenguaje de bajo nivel, ampliamente utilizado en sistemas operativos y software de alto rendimiento, y su notación lógica es similar a la de muchos otros lenguajes de programación.  

A continuación, presentamos un primer ejemplo en C que muestra cómo se aplican estos operadores en un programa real:  

```c
#include <stdio.h>

int main() {
    int a = 1; // Representa "verdadero"
    int b = 0; // Representa "falso"

    printf("Negación de a: %d\n", !a); // Devuelve 0 (falso)
    printf("Conjunción de a y b: %d\n", a && b); // Devuelve 0
    printf("Disyunción de a y b: %d\n", a || b); // Devuelve 1 (verdadero)

    return 0;
}
```
Este programa imprime:

```
Negación de a: 0   
Conjunción de a y b: 0   
Disyunción de a y b: 1   
```

Como podemos ver, los operadores lógicos en C funcionan de manera similar a su equivalente matemático:

- `!a` invierte el valor de `a`, que era `1` (verdadero), y lo convierte en `0` (falso).
- `a && b` devuelve `0` porque `b` es `0` y la conjunción solo es verdadera si ambas proposiciones lo son.
- `a || b` devuelve `1` porque en una disyunción basta con que **al menos una** de las proposiciones sea verdadera.

Este tipo de operaciones son esenciales en programación para evaluar condiciones dentro de estructuras de control, como **sentencias `if` o bucles `while`**, que veremos más adelante.


---

## Tablas de verdad  

Las **tablas de verdad** son una herramienta fundamental en lógica proposicional. Permiten visualizar cómo los operadores lógicos afectan el valor de verdad de una proposición en función de sus entradas.  

A continuación, mostramos las tablas de verdad para los operadores **negación**, **conjunción** y **disyunción**.  

### **Tabla de verdad de la negación (¬A)**  
| A | ¬A |
|---|----|
| V | F  |
| F | V  |

### **Tabla de verdad de la conjunción (A ∧ B)**  
| A | B | A ∧ B |
|---|---|--------|
| V | V | V      |
| V | F | F      |
| F | V | F      |
| F | F | F      |

### **Tabla de verdad de la disyunción (A ∨ B)**  
| A | B | A ∨ B |
|---|---|--------|
| V | V | V      |
| V | F | V      |
| F | V | V      |
| F | F | F      |

---

### **Representación de las tablas de verdad en C**  

Ahora que hemos visto cómo funcionan las tablas de verdad en lógica matemática, podemos implementarlas en **C** usando `printf` para mostrar los valores de verdad de los operadores lógicos.  

```c
#include <stdio.h>

int main() {
    int A, B;

    printf("A | B | A && B | A || B | !A \n");
    printf("|----|----|--------|--------|----|\n");

    for (A = 1; A >= 0; A--) {
        for (B = 1; B >= 0; B--) {
            printf("%d | %d |   %d   |   %d   |  %d \n",
                   A, B, A && B, A || B, !A);
        }
    }
    return 0;
}
```

Este código genera la siguiente salida (la tabla es el formato markdown):   

| A  | B  | A && B | A \|\| B | !A |
|----|----|--------|--------|----|
1 | 1 |   1   |   1   |  0  
1 | 0 |   0   |   1   |  0  
0 | 1 |   0   |   1   |  1  
0 | 0 |   0   |   0   |  1  


Aquí podemos ver cómo los operadores lógicos de C producen los mismos resultados que las tablas de verdad de la lógica proposicional.

---

## Implicación lógica (→)  

En lógica proposicional, la **implicación** es una operación que relaciona dos proposiciones, **A** y **B**, y se denota como:  

**A → B**  

Su significado es: "**Si A es verdadera, entonces B también debe serlo**".  

| A | B | A → B |
|---|---|-------|
| V | V | V     |
| V | F | F     |
| F | V | V     |
| F | F | V     |

La única situación en la que la **implicación es falsa** es cuando **A es verdadera pero B es falsa**.  

🔹 **Ejemplo en lenguaje natural:**  
- **Proposición:** "Si llueve, entonces la calle está mojada."  
  - Si llueve y la calle está mojada (✅ verdadero).  
  - Si llueve pero la calle **no** está mojada (❌ falso, contradicción).  
  - Si **no llueve**, no podemos decir nada sobre la calle (✅ verdadero por defecto).  

📝 **Nota importante:**  
La implicación puede parecer contraintuitiva al principio, especialmente en el caso en que **A es falsa**. Sin embargo, en lógica formal, una **implicación con un antecedente falso** se considera **siempre verdadera**, porque no podemos comprobar si la conclusión es cierta o no.

---

## Bicondicional (↔)  

El **bicondicional** es una relación más fuerte que la implicación y se denota como:  

**A ↔ B**  

Su significado es: "**A es verdadera si y solo si B también lo es**". Para que **A ↔ B sea verdadero**, **A y B deben tener el mismo valor de verdad** (ambos verdaderos o ambos falsos).  

| A | B | A ↔ B |
|---|---|-------|
| V | V | V     |
| V | F | F     |
| F | V | F     |
| F | F | V     |

🔹 **Ejemplo en lenguaje natural:**  
- **Proposición:** "Una figura es un cuadrado si y solo si tiene cuatro lados iguales y cuatro ángulos rectos."  
  - Si una figura es un cuadrado, cumple ambas condiciones (✅ verdadero).  
  - Si una figura tiene cuatro lados iguales y ángulos rectos, es un cuadrado (✅ verdadero).  
  - Si una figura **no** es un cuadrado, **tampoco** cumple ambas condiciones (✅ verdadero).  
  - Si una figura **no** cumple las condiciones, **tampoco** es un cuadrado (✅ verdadero).  

El bicondicional es esencial en lógica, ya que expresa relaciones de **equivalencia lógica**.

---

