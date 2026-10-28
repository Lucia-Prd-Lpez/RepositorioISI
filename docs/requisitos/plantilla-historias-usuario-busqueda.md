# Historias de usuario de búsqueda

| Campo | Valor |
| --- | --- |
| Proyecto | Proyecto Simbiosis |
| Fecha | [28/10/2026] |
| Versión | [1.0] |
| Estado | Borrador |

## Fuentes comunes

- [Acta de UC-21 Buscar recetas](../captura/acta-acuerdos-uc-21-buscar-recetas.md), v1.1, Vigente.
- [Catálogo de requisitos](catalogo-requisitos.md), UR-08 y FR pertinentes.
- [Modelo de casos de uso](../modelos/modelo-casos-de-uso.md), UC-21.

## Épica de búsqueda

Como [usuario registrado], quiero [buscar recetas de cocina combinando texto, ingredientes requeridos e ingredientes a excluir], para [encontrar alternativas adaptadas a mis necesidades y preferencias alimentarias sin ver recetas no deseadas].

**Estado:** descompuesta en US-01, US-02 y US-03. Conserva la necesidad conjunta.

## Justificación de la división

[Se divide la épica en tres historias independientes porque cada criterio de búsqueda (por texto libre, por inclusión de ingredientes y por exclusión de ingredientes) aporta un valor de uso por sí mismo sin depender del desarrollo de los otros. Esta separación permite entregar funcionalidades útiles de forma incremental y facilita que el usuario pueda usar la exclusión o inclusión sin necesidad de introducir términos de texto.]

## US-01

**Título:** [Búsqueda de recetas por palabra o frase]

Como [usuario registrado], quiero [buscar recetas mediante una palabra o frase en el título o descripción breve], para [encontrar recetas específicas de forma rápida].

**Fuentes:** UR-08; UC-21; [FR -085]; acta, [apartado 2 (Criterios de búsqueda y Búsqueda sin resultados)].

### Criterios de aceptación

- **CA-01.** Dado que el usuario busca por el término texto «arroz», cuando ejecuta la búsqueda, entonces el sistema muestra únicamente las recetas publicadas y validadas que contengan la palabra «arroz» en el título o en la descripción breve, ordenadas por fecha de publicación con la más reciente primero.
- **CA-02.** Dado que el usuario introduce la frase «crema de verduras», cuando ejecuta la búsqueda, entonces el sistema devuelve solo las recetas que contengan exactamente esas palabras seguidas y en ese orden en su título o descripción breve, ignorando mayúsculas y tildes.
- **CA-03.** Dado que no existe ninguna receta con el término «pizza», cuando el usuario ejecuta la búsqueda, entonces el sistema indica que no hay resultados para esa búsqueda, conserva el término en el campo de entrada y propone la alternativa relacionada «pan de ajo» de forma separada sin cambiar los criterios ni ejecutar otra búsqueda automáticamente.
- 
## US-02

**Título:** [Búsqueda de recetas por ingredientes incluidos]

Como [usuario registrado], quiero [buscar recetas seleccionando uno o varios ingredientes requeridos], para [localizar platillos que utilicen los ingredientes que tengo disponibles].

**Fuentes:** UR-08; UC-21; [FR-086]; acta, [apartado 2 (Criterios de búsqueda y Búsqueda sin resultados)].

### Criterios de aceptación

- **CA-01.** Dado que el usuario selecciona los ingredientes «manzana» y «avena», cuando ejecuta la búsqueda, entonces el sistema muestra únicamente las recetas publicadas y validadas que contengan conjuntamente todos y cada uno de los ingredientes seleccionados («manzana» y «avena»).
- **CA-02.** Dado que el usuario introduce el texto «pastel» y selecciona el ingrediente «zanahoria», cuando ejecuta la búsqueda combinada, entonces el sistema devuelve únicamente las recetas que contengan la palabra «pastel» en título/descripción y que además incluyan la «zanahoria» entre sus ingredientes.
- **CA-03.** Dado que el usuario abre el formulario de búsqueda, cuando no selecciona ningún ingrediente ni introduce ningún texto e intenta buscar, entonces el sistema solicita que indique al menos un criterio y conserva el formulario sin ejecutar la búsqueda.

## US-03

**Título:** [Exclusión de ingredientes en la búsqueda de recetas]

Como [usuario registrado], quiero [seleccionar ingredientes], para [beneficio].

**Fuentes:** UR-08; UC-21; [FR-087]; acta, [apartado 2 (Criterios de búsqueda y Búsqueda sin resultados)].

### Criterios de aceptación

- **CA-01.** Dado que el usuario selecciona excluir el ingrediente «nueces», cuando ejecuta la búsqueda, entonces el sistema devuelve todas las recetas publicadas y validadas excepto aquellas que contengan «nueces» en su lista de ingredientes.
- **CA-02.** Dado que el usuario selecciona el ingrediente «tomate» para incluirlo y también selecciona «tomate» para excluirlo, cuando intenta ejecutar la búsqueda, entonces el sistema señala el conflicto de ingrediente e impide ejecutar la búsqueda hasta que se corrija la selección.
- **CA-03.** Dado que el usuario busca el término «sopa» excluyendo el ingrediente «pimienta», cuando no se encuentran recetas que cumplan ambas condiciones, entonces el sistema indica que no hay resultados y sugiere alternativas de búsqueda conservando la exclusión de «pimienta» sin proponerme retirarla.

## Revisión INVEST

La revisión abarca US-01, US-02 y US-03. «Aplicado» indica si se ha realizado la comprobación. «Cumple» indica si todas las historias cumplen el criterio. Si alguna no lo cumple, indicar «No» e identificar la historia y el motivo en la justificación. Si no se ha realizado la comprobación o faltan datos, indicar «Pendiente» en «Cumple».

| Criterio | Pregunta de revisión | Aplicado | Cumple | Justificación |
| --- | --- | --- | --- | --- |
| Independiente | ¿Puede implementarse cada historia y ofrecer un resultado útil sin implementar antes las otras historias del conjunto? Puede compartir infraestructura con ellas. | Sí | Sí | Cada historia (US-01, US-02 y US-03) permite realizar búsquedas autónomas por su respectivo criterio (texto, ingrediente incluido o ingrediente excluido) ofreciendo valor por sí sola. |
| Negociable | ¿Cada historia explica qué necesita la persona y deja margen para discutir los detalles de la solución, respetando los acuerdos confirmados? | Sí | Sí | Las historias definen las necesidades y beneficios del usuario respetando el acta de UC-21, dejando margen para el diseño de la interfaz o componentes visuales. |
| Valiosa | ¿La parte «para…» de cada historia explica el beneficio que obtiene la persona al usar esa capacidad? | Sí | Sí | Todas las historias incorporan la cláusula «para...» indicando claramente el valor de negocio y beneficio obtenido por el usuario. |
| Estimable | ¿Están claros el alcance y los datos necesarios para estimar el trabajo de cada historia? | Sí | Sí | El alcance de cada historia está acotado a un único tipo de filtrado y respaldado por sus FR correspondientes y los criterios de aceptación. |
| Pequeña | ¿Se centra cada historia en una única capacidad de alcance manejable? | Sí | Sí | Cada historia aborda una sola capacidad derivada de la descomposición de la épica (texto libre, incluir ingredientes o excluir ingredientes). |
| Comportable | ¿Los criterios de aceptación de cada historia describen acciones y resultados observables que permiten distinguir un comportamiento correcto de uno incorrecto? | Sí | Sí | Todos los CA utilizan el formato Dado-Cuando-Entonces con datos concretos (términos e ingredientes reales) para verificar el resultado. |

## Dudas pendientes:
[Ninguna]
