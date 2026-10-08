## 4.1 Requisitos ampliados

**Instituto Politécnico Nacional**  
**Escuela Superior de Cómputo (ESCOM)**  
**Asignatura:** Bases de Datos  
**Práctica 2:** "Modelo Entidad-Relación Extendido: proyecto propio y proyecto asignado"  
**Ejercicio 4**: Modelo EER del proyecto propio

**Profesor:** Hurtado Avilés Gabriel  
**Equipo:**
* Espinosa Ramírez José Luis
* Rojas Castro Alejandro Tonatiuh
* Zamudio Monroy Gael Armando

**Grupo:** 3BV1  
**Fecha de Entrega:** 8 de octubre de 2026


### 4.1.1 Descripción del problema

**Contexto.** En zonas urbanas hay un gran número de perros, gatos y otros animales de compañía en situación de calle. Su rescate y colocación suelen depender de rescatistas independientes y pequeñas asociaciones que rescatan al animal, lo atienden con veterinarios voluntarios, lo alojan en hogares temporales y buscan su adopción.

**Problema.** Esta coordinación se hace hoy con chats grupales y hojas de cálculo sueltas, lo que provoca que:

1. No exista un historial confiable por animal (dónde se rescató, quién lo atendió, dónde ha vivido).
2. Se pierda el control de vacunas, esterilizaciones y tratamientos pendientes.
3. Se desconozca cuántos lugares libres hay en los hogares temporales y para qué especies.
4. Las adopciones no tengan seguimiento y, cuando un animal es devuelto, no quede registro del motivo.
5. No se pueda analizar de qué zonas provienen más rescates ni cuánto tarda cada animal en ser adoptado.

**Objetivo.** Diseñar una base de datos que dé trazabilidad a cada animal desde su rescate hasta su adopción y seguimiento posterior, y que permita consultar la capacidad de los hogares temporales y obtener indicadores de la operación.

**Alcance.**

- Incluye: rescates, atención médica, hogares temporales, solicitudes de adopción, adopciones y seguimiento posadopción.
- No incluye: donaciones monetarias, contabilidad, inventario de insumos ni campañas de difusión.

**Usuarios:** rescatistas, veterinarios voluntarios, responsables de hogares temporales, adoptantes y el coordinador de la red.

### 4.1.2 Restricciones de cardinalidad

|Núm.|Requisito|Cardinalidad|
|---|---|---|
|RC1|Cada animal ingresa a la red mediante un único rescate; un rescate puede involucrar a una o más crías o animales (camada).|Rescate (1,N) – Animal (1,1)|
|RC2|Todo rescate cuenta con al menos un rescatista; un rescatista puede participar en varios rescates o en ninguno.|Rescate (1,N) – Rescatista (0,N)|
|RC3|Cada rescate ocurre en una sola zona; una zona puede tener muchos rescates o ninguno.|Rescate (1,1) – Zona (0,N)|
|RC4|Un animal puede tener muchas atenciones médicas o ninguna; cada atención corresponde a un solo animal.|Animal (0,N) – Atención (1,1)|
|RC5|Una atención se realiza, cuando aplica, en una clínica y por un veterinario voluntario (puede darse en campo, sin ninguno de los dos).|Atención (0,1) – Clínica (0,N); Atención (0,1) – Veterinario (0,N)|
|RC6|Cada vacunación aplica exactamente una vacuna del catálogo; una vacuna puede aplicarse muchas veces.|Vacunación (1,1) – Vacuna (0,N)|
|RC7|Cada hogar temporal tiene exactamente un responsable; una persona puede ser responsable de varios hogares.|Hogar (1,1) – Persona (0,N)|
|RC8|Cada hogar temporal está en una sola zona.|Hogar (1,1) – Zona (0,N)|
|RC9|Un animal puede tener muchas estancias a lo largo del tiempo, pero solo una activa a la vez; un hogar aloja varios animales, sin rebasar su capacidad máxima de forma simultánea.|Animal (0,N) – Hogar (0,N)|
|RC10|Un animal tiene a lo sumo una madre registrada; una madre puede tener muchas crías.|Madre (0,N) – Cría (0,1)|
|RC11|Un adoptante puede solicitar varios animales y un animal puede recibir varias solicitudes.|Animal (0,N) – Adoptante (0,N)|
|RC12|Un animal puede tener varias adopciones en el tiempo (por devoluciones), pero solo una vigente; un adoptante puede adoptar varios animales.|Animal (0,N) – Adoptante (0,N)|
|RC13|Una adopción puede tener muchos seguimientos o ninguno; cada seguimiento pertenece a una sola adopción.|Adopción (0,N) – Seguimiento (1,1)|

La cardinalidad junto a una entidad indica con cuántas instancias de la otra se relaciona cada instancia de esta, en la forma (mín,máx).

### 4.1.3 Entidades dependientes

|Entidad dependiente|Depende de|Justificación|
|---|---|---|
|Atención médica|Animal|Una atención no existe sin el animal atendido; se identifica por el animal más un número consecutivo de atención. Si se elimina el animal, se elimina su historial.|
|Seguimiento posadopción|Adopción|Un seguimiento solo tiene sentido dentro de una adopción concreta; se identifica por la adopción más un número de seguimiento.|

### 4.1.4 Categorías o tipos dentro de las entidades principales

|Entidad|Categorías|Atributos propios|Tipo de especialización|
|---|---|---|---|
|Animal|Perro, Gato, Otro|Perro: tamaño, nivel de energía, apto con niños. Gato: resultado de prueba de leucemia felina e inmunodeficiencia felina. Otro: descripción de la especie.|Disjunta y total: todo animal es de exactamente una categoría.|
|Persona|Rescatista, Veterinario voluntario, Adoptante|Rescatista: vehículo propio, disponibilidad. Veterinario: cédula, especialidad. Adoptante: tipo de vivienda, tiene patio, otras mascotas.|Solapada y parcial: una persona puede tener varios roles (rescatista y adoptante) y otras no tienen ninguno (por ejemplo, quien solo es responsable de un hogar).|
|Atención médica|Vacunación, Cirugía, Tratamiento|Vacunación: dosis, fecha de próxima dosis. Cirugía: tipo, complicaciones. Tratamiento: diagnóstico, duración en días.|Disjunta y parcial: una revisión general no pertenece a ninguna categoría.|

### 4.1.5 Relaciones que involucran más de dos entidades

**Traslado a hogar temporal (Animal – Hogar temporal – Rescatista).**  
Para cada ingreso de un animal a un hogar temporal debe conocerse qué animal fue, a qué hogar, qué rescatista lo trasladó y las fechas de inicio y fin de la estancia, junto con el motivo de salida. La relación no puede descomponerse en dos binarias sin perder información: el mismo animal puede ser trasladado por distintos rescatistas en distintas ocasiones, y un rescatista traslada a varios animales a varios hogares. Se trata de una relación ternaria N:M:N con atributos fecha_inicio, fecha_fin y motivo_salida.

**Adopción y seguimiento (agregación).**  
La adopción es una relación entre Animal y Adoptante con sus propios atributos (fecha de adopción, fecha de devolución, motivo de devolución). Como además debe relacionarse con los seguimientos posteriores, se trata como una agregación, es decir, una relación que participa en otra relación.

**Atención médica.**  
Involucra animal, veterinario y clínica, pero se modela con la entidad débil Atención médica y dos relaciones binarias opcionales, porque el veterinario y la clínica pueden faltar (atenciones de campo).