# Mundial-de-Futbol-2026
Taller Grupal
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

<img src="https://github.com/AdrianCa17-G/Mundial-de-Futbol-2026/blob/main/Diagrama_UML/Diagrama_UML.jpg" alt="Texto alternativo" width="700"/>

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

## 🔗 Relaciones entre Clases

`Futbolista` y `Entrenador` heredan de `Persona`. Una `Seleccion` está compuesta por un plantel de `Futbolistas` y tiene asociado un `Entrenador`. Un `Partido` referencia a exactamente dos `Selecciones` para simular el enfrentamiento.
