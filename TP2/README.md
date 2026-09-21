# Trabajo Práctico 2 - Sistemas de Computación

## Descripción
Proyecto de integración entre C y Assembler (x86_64, sintaxis AT&T) aplicando la convención de llamadas System V AMD64 ABI. El sistema se conecta a la API REST del Banco Mundial mediante `libcurl` para extraer el Índice GINI de Argentina y delega el procesamiento matemático y manejo de memoria a una subrutina de bajo nivel.

## Estructura del Repositorio
-  **/Iteracion_1**: Código fuente en C puro con la lógica de conexión a la API web y extracción de datos JSON.
- **/Iteracion_2**: Implementación final en C y Assembler. Incluye el análisis del Stack Frame mediante GDB.

## Requisitos y Compilación
Se requiere entorno Linux de 64 bits con `gcc` y `libcurl`.
Para compilar la versión final:
- `as --64 -g -o calculo.o calculo.s`
- `gcc -g -O0 -c -o main_2.o main_2.c`
- `gcc -g main_2.c calculo.s -lcurl -o tp2_final`

## Análisis de Memoria
Se documenta el comportamiento de la pila de memoria (Stack) validando la creación y destrucción del marco de pila (`%rbp` y `%rsp`) antes, durante y después de la llamada a la función en Assembler.
