# ProyectoDiscretas1

# Documento explicativo 

## Introducción
Este programa es un evaluador de fórmulas en lógica proposicional. Permite:
1. Evaluar fórmulas con valores de verdad predefinidos para sus átomos (Parte A).
2. Determinar si una fórmula es una **tautología**, **contradicción** o **contingencia** probando todas sus posibles valoraciones de verdad (Parte B).

---

## Explicación de las Funciones

### `cadena_a_lista(cadena: str, ignorar: set) -> list[str]`
Convierte una cadena en una lista de caracteres, eliminando los que están en el conjunto `ignorar`.

#### **Parámetros**
- `cadena`: La cadena con la fórmula.
- `ignorar`: Conjunto de caracteres a eliminar (Espacios en blanco).

#### **Retorno**
- Lista de caracteres sin los elementos ignorados.

---

### `valorar_expresion(expresion: list, izq: int, der: int)`
Evalúa una expresión lógica utilizando los valores de verdad almacenados.

#### **Parámetros**
- `expresion`: Lista de caracteres que representa la fórmula lógica.
- `izq`: Índice inicial dentro de la expresión.
- `der`: Índice final dentro de la expresión.

#### **Funcionamiento**
1. Si la expresión es un solo átomo, devuelve su valor de verdad almacenado.
2. Si empieza con `!`, devuelve la negación de la evaluación recursiva.
3. Si la expresión está entre paréntesis, busca el operador principal `&` o `|`, y evalúa recursivamente ambos lados:
   - `&` (conjunción): True si **ambos** operandos son True.
   - `|` (disyunción): True si **al menos uno** de los operandos es True.

#### **Retorno**
- `True` o `False` según la evaluación.
- `-1` si la expresión no es válida.

---

### `evaluar_formula(formula: str, atomos: list)`
Determina si una fórmula es una **tautología**, **contradicción** o **contingencia**.

#### **Parámetros**
- `formula`: La fórmula en formato de cadena.
- `atomos`: Lista de átomos que aparecen en la fórmula.

#### **Funcionamiento**
1. Convierte la fórmula en una lista de caracteres sin espacios.
2. Genera todas las combinaciones de valores de verdad para los átomos.
3. Evalúa la fórmula con cada combinación y almacena los resultados.
4. Clasifica la fórmula:
   - **Tautología (`1`)**: Siempre es `True`.
   - **Contradicción (`0`)**: Siempre es `False`.
   - **Contingencia (`-1`)**: Algunas veces `True`, otras `False`.

#### **Retorno**
- `1` si es una tautología.
- `0` si es una contradicción.
- `-1` si es una contingencia o si la fórmula es inválida.

---

### `main()`
Función principal que gestiona la entrada y salida.

#### **Funcionamiento**
1. **Parte A:**
   - Lee el número de átomos (`N`) y sus valores de verdad.
   - Lee `M` fórmulas y las evalúa con los valores dados.
   - Imprime `1` si la fórmula es `True`, `0` si es `False`.

2. **Parte B:**
   - Lee `S` fórmulas y extrae los átomos presentes.
   - Evalúa cada fórmula con todas las combinaciones posibles de valores de verdad.
   - Imprime `1` si es tautología, `0` si es contradicción, `-1` si es contingencia.

---

## Ejemplo de Entrada y Salida

### **Parte A**
#### **Entrada**
```
2
p 1
q 0
3
(p & q)
(p | q)
!(p & q)
```

#### **Salida**
```
0
1
1
```

### **Parte B**
#### **Entrada**
```
2
(p | !p)
(p & !p)
```

#### **Salida**
```
1
0
```

---


