# Mundial de Futbol 2026
Taller Grupal
## Equipo de Desarrollo

| Integrante | Rol |
|------------|-----|
| Anthony Godoy | Diagrama UML|
| Adrian Guaman | Documentación del sistema |
| Daniel Vargas | Desarrollo del código fuente |

## Se evaluó al grupo 3 y se le asignó una nota de | 10 | 

---
## Descripción
Sistema orientado a objetos que simula la gestión de un Mundial de Fútbol. Permite registrar selecciones nacionales con sus plantillas (futbolistas y entrenadores), simular partidos de la fase de grupos y generar una tabla de posiciones con los clasificados.

Proyecto desarrollado como parte de un taller académico con enfoque en los pilares fundamentales de la **Programación Orientada a Objetos**: Herencia, Encapsulamiento, Clases y Objetos.

---
##  Objetivos del Proyecto

- Aplicar **herencia** mediante una jerarquía de clases centrada en `Persona`.
- Aplicar **encapsulamiento** con atributos privados y acceso controlado mediante getters/setters.
- Modelar entidades del mundo real (selecciones, jugadores, partidos) como objetos.
- Simular la fase de grupos y generar una tabla de clasificación.

---
##  Arquitectura del Sistema

### Jerarquía de Clases

<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Diagrama_UML/Diagrama_UML.jpeg" alt="Texto alternativo" width="700"/>

##  Clases y Responsabilidades

### `Persona` — Superclase
Representa a cualquier persona del mundial. Contiene `nombre`, `edad` y `pasaporte` como atributos privados, accesibles mediante getters y setters.

### `Futbolista` — Subclase de Persona
Extiende a Persona añadiendo `goles` y `posicion`. Incluye el método `registrarGol()` para actualizar sus goles de forma controlada.

### `Entrenador` — Subclase de Persona
Extiende a Persona añadiendo `estrategia`, que representa la táctica de juego del equipo. Accesible mediante getters y setters.

### `Seleccion`
Agrupa a un `Entrenador` y un `plantel` de futbolistas bajo un `nombrePais`. Lleva el control de `puntos` mediante el método `sumarPuntos()`.

### `Partido`
Enfrenta a dos selecciones. Almacena los goles de cada equipo (`golesLocal`, `golesVisitante`) y determina el resultado con `calcularResultado()`, que se encarga de sumar los puntos correspondientes a cada selección.

##  Relaciones entre Clases

`Futbolista` y `Entrenador` heredan de `Persona`. Una `Seleccion` está compuesta por un plantel de `Futbolistas` y tiene asociado un `Entrenador`. Un `Partido` referencia a exactamente dos `Selecciones` para simular el enfrentamiento.

#  Descripción del Código

**Clase `Persona`**
Superclase base. Guarda `nombre` y `edad` como atributos privados.

**Clase `Entrenador`**
Hereda de `Persona`. Agrega el atributo `estrategia` y usa `super()` para inicializar los datos del padre.

<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/1_Clases.jpeg" alt="Texto alternativo" width="700"/>

**Clase `Seleccion`**
Representa a un equipo. Maneja de forma encapsulada los `puntos`, `goles_favor` y `goles_contra`. Tiene tres métodos para registrar resultados: `registrar_victoria()` suma 3 puntos, `registrar_empate()` suma 1, y `registrar_derrota()` no suma ninguno. También permite asignar un entrenador con `asignar_entrenador()`.

<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/2_Clases.jpeg" alt="Texto alternativo" width="700"/>
<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/2.1_Clases.jpeg" alt="Texto alternativo" width="700"/>

**Clase `Grupo`**
Agrupa exactamente 4 selecciones. El método `get_tabla()` ordena los equipos por puntos y diferencia de goles usando el algoritmo de burbuja, luego imprime la tabla de posiciones en consola.

<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/3_Clases.jpeg" alt="Texto alternativo" width="700"/>
<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/3.1_Tabla.jpeg" alt="Texto alternativo" width="700"/>

**Clase `Partido`**
Enfrenta a dos selecciones. El método `jugar_partido()` recibe las listas de goles de cada equipo, muestra el resultado en consola y llama al método correspondiente en cada selección según quien ganó, perdió o empató.

<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/4_Clases.jpeg" alt="Texto alternativo" width="700"/>
<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/4.1_Clases.jpeg" alt="Texto alternativo" width="700"/>

**Bloque principal**
Se crean las cuatro selecciones del grupo, se asignan entrenadores a Ecuador y Alemania, se arma el grupo A y se simula un partido entre Ecuador y Alemania enviando los goles con el nombre del jugador, posición y minuto. Al final se imprime la tabla.

<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/5_Presentacion.jpeg" alt="Texto alternativo" width="700"/>

##  Ejecución del Código
<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/6_Ejecucion.jpeg" alt="Texto alternativo" width="700"/>
<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Codigo/6.1_Ejecucion.jpeg" alt="Texto alternativo" width="700"/>


##  Reflexiones del Equipo

**¿Por qué usar herencia en este sistema?**
La herencia nos permitió evitar repetir atributos como `nombre`, `edad` y `pasaporte` en cada clase. Al centralizar esos datos en `Persona`, cualquier cambio en la estructura base se propaga automáticamente a `Futbolista` y `Entrenador`, haciendo el sistema más mantenible.

**¿Qué ventaja ofrece el encapsulamiento en la simulación?**
Al hacer `puntos` un atributo privado de `Seleccion` y solo modificarlo mediante `sumarPuntos()`, garantizamos que ninguna parte del código pueda asignar puntos arbitrariamente. La lógica de negocio (3 puntos por ganar, 1 por empate) queda centralizada en `Partido.asignarPuntos()`, haciendo el sistema más robusto y fácil de auditar.

**¿Qué representa la clase `Partido` en términos de POO?**
`Partido` es un ejemplo de **composición**: no hereda de ninguna clase, sino que *usa* objetos de tipo `Seleccion` para operar. Esto muestra que la herencia no es la única relación entre clases; la composición es igualmente poderosa cuando una clase necesita coordinar el comportamiento de otras.

---
