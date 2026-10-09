# Decisiones de diseño — CBini OrquestrAI

🇪🇸 **Español** · 🇧🇷 [Português](design-br.md) · 🇺🇸 [English](design.md) · [README](../README-ES.md) · [Arquitectura](arch-es.md) · [Seguridad](security-es.md)

Por qué el producto tiene la forma que tiene. Cada decisión indica el costo que acepta.

| Decisión | Por qué | Costo aceptado |
|---|---|---|
| **El chat nunca ejecuta** | La conversación es donde vive la incertidumbre; ejecutar necesita un artefacto estable y revisable. | Un paso más entre pedir y cambiar. |
| **Chat, bloque de comando y terminal son superficies separadas** | Conversar, cambiar e inspeccionar tienen riesgos distintos, así que tienen permisos distintos. La terminal del proyecto es de solo lectura. | Los operadores aprenden tres superficies en lugar de una. |
| **La autonomía termina antes del efecto real** | Los agentes pueden planificar, escribir y explicar sin límite; el momento en que algo cambia de verdad pertenece a una persona. | Más lento que la ejecución autónoma, a propósito, justo en ese punto. |
| **Explicar antes del código** | El bloque muestra primero qué va a pasar (objetivo, datos, archivos, efecto) y después el código completo. | Un bloque un poco más largo. |
| **Una versión vetada nunca se ejecuta** | Un rechazo debe ser definitivo, y su motivo debe mejorar el siguiente plan. | Un comando corregido necesita una versión nueva. |
| **Rechazar cuando el efecto no puede analizarse** | Adivinar el alcance es peor que rechazar; el operador puede reformular el cambio de forma explícita. | Algunos comandos válidos se rechazan y deben escribirse de forma más literal. |
| **El proyecto es la unidad de aislamiento y de contexto** | Conversaciones, comandos, terminales, vistas previas, lecciones y costos comparten una frontera; el conocimiento pertenece al proyecto, no al modelo. | El trabajo entre proyectos no es una sola operación. |
| **Las vistas previas viven en un origen separado** | Las páginas generadas no deben ver la sesión del operador. | Las vistas previas no pueden reutilizar el inicio de sesión del cockpit. |
| **La evolución de la base de datos es aditiva** | Agregar un campo nunca pone en riesgo los registros existentes; eliminar o renombrar sí, y eso exige una decisión humana fuera del flujo automático. | Algunos cambios de esquema no se hacen por el chat. |
| **El costo desconocido no es cero** | Un precio ausente que se lee como cero oculta gasto; lo desconocido se muestra como desconocido. | Algunos totales quedan incompletos y lo dicen. |
| **Las lecciones necesitan aprobación humana** | El conocimiento que llega a todos los agentes cambia comportamiento y recibe la misma gobernanza que el código. | Aprender es más lento que aprender solo. |
| **El código que existe no es una capacidad** | Una capacidad es *Disponible* solo tras prueba automática y humana; los cambios sensibles también necesitan revisión independiente. | Las funcionalidades esperan en validación más de lo que podrían. |
| **Un full stack completo antes que varios parciales** | Un solo camino demostrado enseña más que varios a medias y se vuelve la plantilla del siguiente. | Menos opciones de stack por ahora. |
| **No competir con los modelos** | Los modelos y agentes de programación mejoran rápido; la capa duradera es la gobernanza, el aislamiento, la evidencia y el costo a su alrededor. | OrquestrAI depende de modelos externos para la inteligencia. |
| **Autoalojado, una organización por instalación** | El cliente controla la infraestructura y la elección de proveedores. | No hay oferta multiinquilino alojada en la versión actual. |

La tesis detrás de las dos últimas filas es una apuesta de producto, no una ventaja de mercado demostrada. ¿No está de acuerdo con alguna fila?
[Cuestione la arquitectura](https://github.com/cristhianbini/CBini-OrquestrAI/discussions/2).
