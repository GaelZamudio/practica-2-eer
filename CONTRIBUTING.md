# Distribución de Responsabilidades
### Ejercicio 1
**Gael**: Crear repositorio, agregar colaboradores, crear ramas.
**Alejandro** y **José**: Leer `CONTRIBUTING.md` completo, desarrollar su trabajo en la rama correspondiente para cada ejercicio, finalizar cada cambio (**commit**) con un Pull Request hacia la rama `practica-2` (**NO AUTO-ACEPTARSE EL PULL REQUEST**) y siguiendo la nomenclatura especificada al final de este documento.

### Ejercicio 2
**Gael**: Todo el ejercicio.

### Ejercicio 3
**Gael**: Leer artículos y hacer resumen del Artículo 1.
**Alejandro**: Leer artículos y hacer resumen del Artículo 2.
**José**: Leer artículos y hacer resumen del Artículo 3.

Cada resumen llevará el siguiente formato:
- Título
- ¿Qué problema aborda?
- Procesamiento de datos (de dónde provienen, en qué formato estaban y qué se tuvo que hacer para poder usarlos).
- Modelado de la información (qué entidades o dimensiones se identificaron, qué hechos se miden y cómo se relacionan).
- Qué preguntas concretas puede resolver el sistema.
- Limitaciones y trabajo futuro (qué limitaciones reconocen los autores y qué trabajo futuro proponen)
- Arial 14 para títulos, Arial 12 para cuerpo y subtítulos, todo el documento justificado. Títulos y subtítulos en negritas.

Todos los resúmenes se escribirán en el siguiente documento de Google Docs: https://docs.google.com/document/d/1TOTbG4L1Jq3l2obYpseIrGd1q7VX9n7WBHu_Kvx1shE/edit?usp=sharing
Cuando todos demos el visto bueno al documento lo exportamos y se sube al repositorio (rama `ejercicio-3` con pr a `practica-2`.

### Ejercicio 4
**Gael**: 4.1. Describa el problema de su proyecto propio y amplíe sus requisitos identificando
restricciones de cardinalidad específicas, entidades que dependen de otras, categorías o tipos dentro de sus entidades principales y, si aplica, relaciones que involucren más de dos entidades.
**José**: 4.3. Representar el modelo con la notación de Peter Chen.
**Alejandro**: 
- 4.3. Representar el modelo con la notación Crow's Feet.
- 4.4. Justificación: Explique por qué sus entidades débiles no pueden existir de forma independiente, por qué eligió ese tipo de especialización, cómo reflejan sus cardinalidades las reglas del negocio, y qué tres consultas permite responder su modelo que un modelo sin los conceptos extendidos no podría resolver.

### Ejercicio 5
**Gael**: Todo el ejercicio.

### Ejercicio 6
**Gael**: 
- Declarar 3 propuestas de mejoras como issues.
- Juntar 9 los issues en un documento pdf.
**Alejandro**: Declarar 3 propuestas de mejoras como issues.
**José**: Declarar 3 propuestas de mejoras como issues.

Cada propuesta debe indicar:
1. Un título breve y la necesidad o el problema que atiende.
2. La descripción de la funcionalidad, desde el punto de vista de quien la usaría.
3. Los cambios que implica en el modelo de datos —entidades, atributos o relaciones nuevas o modificadas—, mostrados sobre su modelo del ejercicio 5.
4. En qué se apoya: una limitación o una línea de trabajo futuro declarada en el artículo, un hallazgo al poner en funcionamiento el sistema, o una necesidad que el equipo identificó.
5. Su dificultad estimada, baja, media o alta, con una justificación de una línea.

Las secciones de limitaciones y trabajo futuro de los artículos son un buen punto de partida, pero
una propuesta que solo repite lo que dicen los autores sin desarrollarlo no cuenta.

**IMPORTANTE**: Al menos una de las tres propuestas de cada integrante
debe incorporar una técnica de inteligencia artificial o de aprendizaje automático, justificada con los datos que el sistema ya almacena. Los módulos de detección de anomalías que describen los capítulos 2 y 3 son un punto de partida natural.
### Ejercicio 7
Cada equipo expone en clase entre doce y quince minutos, más una ronda de preguntas. Todos los integrantes exponen. La presentación debe cubrir, en este orden:
1. Qué problema resuelve el proyecto asignado y con qué datos (**Gael**)
2. Una demostración del proyecto funcionando en su equipo, en vivo o grabada (**Alejandro**)
3. El modelo EER del proyecto asignado y su correspondencia con el esquema publicado (**Gael y Alejandro**)
4. Las propuestas de mejora, cada una presentada por su autor.
5. En un par de minutos, el modelo EER del proyecto propio. (**José**)
Cada uno realiza las diapositivas de su parte en la siguiente plantilla de Canva: https://canva.link/7krh19drmfjuugx
**IMPORTANTE**: Usar la paleta de colores y elementos **ya incluidos** en la plantilla para tener una presentación consistente. NO ELIMINAR diapositivas por defecto, DUPLICARLAS y modificar (y poner en visible) la copia.
# Nomenclatura de Commits y PRs
### Commits:

```
<tipo>(<ejercicio>): <descripción corta en minúsculas>
```

#### Tipos permitidos:

- `feat`: Nuevas características, resúmenes, diagramas, propuestas o documentación relevante.
    
- `fix`: Correcciones de errores en documentación, scripts, modelos o configuraciones.
    
- `docs`: Cambios exclusivamente en archivos de documentación (ej. `README.md`, `levantamiento.md`).
    
- `chore`: Tareas de mantenimiento o estructura de archivos (creación de carpetas, configuración de Git, `.gitignore`, etc.).

### Título de Pull Requests (PRs):

- `[Practica 2] Integración de ejercicio 3 - Resúmenes de artículos`
    
- `[Practica 2] Integración de ejercicio 4 - Modelo EER Proyecto Propio`

# Nombres de archivos
El nombre de los archivos debe seguir explícitamente este formato
```
proyecto-propio/
	requisitos-ampliados.pdf
	eer-chen.png
	eer-crows-feet.png
proyecto-asignado/
	levantamiento.md
	eer.png
	correspondencia-con-el-esquema.pdf
	evidencias/
		app-funcionando.png 
		terminal-arranque.png 
		consulta-resultado.png
articulos/
	resumenes.pdf
propuestas/
	propuestas-de-mejora.pdf
exposicion/
	presentacion.pdf
```