*Este proyecto ha sido creado como parte del currículo de 42 por scamlett y lupin.*

# Rush 01: Skyscraper

![C](https://img.shields.io/badge/C-A8B9CC?logo=c&logoColor=black)
![42](https://img.shields.io/badge/42-Málaga-000000)
![Piscina](https://img.shields.io/badge/Piscina-rush-orange)

## Descripción

Rush de fin de semana de la Piscina de 42, hecho en pareja. El programa
resuelve el puzzle **Skyscraper** en un tablero de 4x4:

- Cada casilla es un edificio de altura 1 a 4.
- En cada fila y cada columna no se repite ninguna altura.
- Alrededor del tablero hay 16 pistas: cuántos edificios se ven desde ese
  lado, sabiendo que un edificio alto tapa a los más bajos que tiene detrás.

```
      4 3 2 1          ← pistas desde arriba
    ┌─────────┐
  4 │ 1 2 3 4 │ 1
  3 │ 2 3 4 1 │ 2      ← pistas desde la derecha
  2 │ 3 4 1 2 │ 2
  1 │ 4 1 2 3 │ 2
    └─────────┘
      1 2 2 2          ← pistas desde abajo
```

El orden de las pistas en la entrada es: arriba (de izquierda a derecha),
abajo, izquierda (de arriba a abajo) y derecha.

## Estructura

| Carpeta | Contenido |
|---------|-----------|
| `ex00/` | La entrega: `rush-01.c` (lectura de pistas y backtracking) y `check.c` (cuenta edificios visibles e imprime el tablero) |
| `codigocomentadosusi/` | La misma solución con comentarios línea a línea, para estudiarla |
| `códigocomentdolucas/` | La versión comentada de mi compañero |
| `es.subject.pdf` | El enunciado |

## Instrucciones

```bash
cd ex00
cc -Wall -Wextra -Werror rush-01.c check.c -o rush-01
./rush-01 "4 3 2 1 1 2 2 2 4 3 2 1 1 2 2 2"
```

Salida:

```
1 2 3 4
2 3 4 1
3 4 1 2
4 1 2 3
```

Si la entrada no tiene exactamente 16 números del 1 al 4 separados por un
espacio, o si el puzzle no tiene solución, el programa imprime `Error`.

## Lo que aprendí

- **Backtracking**: probar un valor en una casilla, avanzar a la siguiente
  y, si el camino no lleva a ninguna solución, deshacer (`board[row][column] = 0`)
  y probar el siguiente valor
- Recortar el árbol de búsqueda pronto: no colocar una altura que ya está en
  la fila o en la columna ahorra muchísimas combinaciones
- Recorrer un tablero 2D con un solo índice: `fila = celda / 4`,
  `columna = celda % 4`
- Parsear argumentos a mano en C, carácter a carácter, sin `atoi` ni
  librerías
- Repartir el trabajo en pareja y explicar el código al otro (de ahí las dos
  carpetas comentadas)
- Escribir C que pase la Norminette
