# Changelog — CBini OrquestrAI

🇺🇸 [English](CHANGELOG.md) · 🇧🇷 [Português](CHANGELOG-BR.md) · 🇪🇸 **Español**

Cómo ha cambiado el producto, escrito para personas y no para máquinas. Cada entrada dice lo que quien usa OrquestrAI ahora puede hacer, o
lo que dejó de fallar. Las herramientas internas, la infraestructura de pruebas y los mecanismos de seguridad aparecen resumidos, no
enumerados.

OrquestrAI fue ideado y es dirigido por **Cristhian Bini, fundador de CBini Soluções em TI**. Él define la visión del producto, toma las
decisiones de producto y aprueba cada versión. Los agentes de IA trabajan como colaboradores de ingeniería: escriben y prueban código y
proponen cambios. Una persona aprueba cada cambio antes de que entre en producción.

> **A IA acelera. O humano decide.** — La IA acelera. El humano decide.

**Estados.** **Publicada**: en producción en la instalación real. **En preparación**: construida y probada, aún no lanzada. **Planificado**:
todavía no es una funcionalidad. Fechas en formato AAAA-MM-DD.

---

## 0.45.0 — 2026-11-20 · MVP · Publicada

Es la primera versión pensada como producto mínimo completo. Se lanzó después de que tres construcciones reales superaran la
verificación funcional a través del cockpit en producción: un sitio institucional, un simulador de préstamos y un panel de datos. El
sitio y el simulador se construyeron con modelos de IA gratuitos, a costo cero. El panel de datos se construyó en el nivel Inteligente,
con un modelo de pago económico autorizado por el fundador y un costo máximo aceptado antes de empezar. Los paneles complejos son más
estables en el nivel Inteligente; el nivel Económico sigue siendo el mejor intento gratuito.

**Entregado**
- **Telemetría restaurada y aprobada por el fundador.** Muestra los últimos 30 días y el historial completo: inversión, tokens y ahorro
  estimado. Desglosa el costo por tipo de cobro, proyecto, agente y modelo, e incluye el control de gastos. Un fallo en los datos ya no deja
  en blanco toda la pantalla. Un costo desconocido aparece como "sin costo medido", nunca como gratuito.
- **Panel lateral de la construcción.** Muestra qué agentes no fueron llamados y por qué, cuánto tardó de verdad la construcción y accesos
  directos a la vista previa y al proyecto.
- **Verificación funcional en cada construcción.** Después de una construcción, la app generada se abre y se usa automáticamente. El
  proyecto muestra entonces uno de tres veredictos: ACEPTADA, RECHAZADA o NO CONCLUYENTE.
- **La Fábrica funciona con modelos gratuitos.** El razonamiento interno del modelo usa solo una parte del límite de salida, para que el
  código generado siga cabiendo. Se prueba primero el modelo gratuito más estable.
- **Gráficos en las apps generadas.** Barras, líneas y torta vienen de un componente de la plataforma, en tamaño legible y sin biblioteca
  externa.
- **Filtros de datos en los paneles generados.** Un filtro de la plataforma permite elegir una columna y un valor, por ejemplo
  *región = Sur*. Los totales y los gráficos siguen el filtro. Cuando el pedido menciona un filtro y el código generado no usa este
  componente, la Fábrica devuelve esa parte para corregirla.
- **Menú que llega a todas las secciones.** En sitios de una sola página, el menú ahora lista las secciones que existen. Un enlace que
  apuntaba a la propia página ahora lleva al visitante a la primera sección.
- **Indicadores sobre la columna numérica correcta.** Los KPI de un panel generado usan una columna numérica elegida por la
  plataforma, nunca la columna del filtro.
- **Menú que cabe en el móvil.** El menú de los sitios de una sola página salta de línea en pantallas pequeñas, sin desplazamiento lateral.
- **Fábrica gratuita más resistente.** Un rechazo por límite de uso del proveedor ya no agota los intentos entre modelos gratuitos, y el
  motivo de cada cambio queda registrado.
- **Formulario de contacto de demostración que responde.** El botón envía y la página muestra el aviso de que nada se envía de verdad.
- **Nivel Inteligente que completa paneles.** El costo máximo de un sitio de pago cubre la generación por partes, y el razonamiento interno
  del modelo de pago queda limitado para que el código quepa en la respuesta.
- **Paneles generados que no se bloquean ni se rechazan por error.** Un componente de la plataforma ya no entra en bucle al redibujar el
  panel, y la verificación reconoce más formas legítimas de usar los componentes.
- **Liberación por el operador.** Cada actualización del sistema en producción exige una liberación escrita por el operador. La liberación
  queda ligada a los archivos exactos que se verificaron.

**Corregido**
- La pantalla de Telemetría no cargaba cuando una ejecución no tenía costo medido.
- La Fábrica tenía varios fallos que hacían que la generación fallara o saliera rota:
  - un contrato de módulos mal leído detenía la generación;
  - un módulo llamaba a otro con el nombre equivocado y la página mostraba "no definido";
  - un plan ilegible ahora recibe un intento más;
  - un módulo rechazado ahora recibe un intento más;
  - los errores de ejecución ahora se detectan antes de publicar el sitio.
- El encabezado ya no muestra un número de versión provisional mientras carga la página.

## 0.44.2 — 2026-11-05 · Publicada
- **La Fábrica puede usar modelos de pago económicos.** El costo máximo se muestra y se autoriza antes de cualquier gasto.
- **El Chat de pago pregunta antes.** Cada mensaje de pago espera la autorización del operador, con un límite por mensaje. Hacer clic dos
  veces no cobra dos veces.
- **El Chat lee solo los archivos del proyecto,** en modo de solo lectura, en vez de pedir al operador que ejecute comandos. También sabe si
  la app está en producción, detenida o aún sin publicar.
- **Un manual más amplio,** con búsqueda y secciones nuevas: qué funciona hoy, tu primera app y modelos de pago.
- **Correcciones:**
  - la lista de proyectos podía ocultar un mensaje de error;
  - una construcción interrumpida por un reinicio seguía apareciendo como "generando";
  - la tarjeta del sitio mostraba falsos avisos en rojo;
  - un fallo al registrar un costo ahora bloquea nuevas llamadas de pago.

## 0.44.1 — 2026-11-04 · Publicada
- **El servidor rechaza modelos de pago sin una ventana de gasto abierta y autorizada,** incluso elegidos a mano. Antes solo se bloqueaba el
  cambio automático.
- **Mensajes más claros:** la tarjeta de una app terminada ya no dice que los agentes siguen trabajando, y los rechazos aparecen en
  portugués.

## 0.44.0 — 2026-11-04 · Publicada
- **Las nuevas apps Full Stack pueden tener hasta cuatro registros relacionados,** por ejemplo clientes y pedidos. Las apps existentes no
  cambian.
- **El operador elige el modelo de IA al crear la app.** Un modelo gratuito confirmado viene marcado por defecto.
- **Una app interrumpida puede retomarse con un modelo gratuito,** sin rehacer lo ya hecho.
- **Más proveedores de IA:** se pueden configurar MiniMax y DeepSeek.
- **Correcciones:**
  - editar un registro en una app generada fallaba dentro de la vista previa;
  - aparecían nombres internos en la pantalla;
  - cuando el modelo gratuito no responde, el cockpit ahora lo dice y ofrece otro.

## 0.43.0 — 2026-11-04 · Publicada
- **Una construcción de sitio interrumpida se explica:** por qué se detuvo, qué se hizo, qué falta y cómo continuar. No hay cambio
  automático a un modelo de pago.
- **El Chat guarda el pedido antes de llamar a la IA,** así un fallo del proveedor nunca lo pierde.
- **Modelos favoritos,** guardados por usuario.
- **Un panel de estado del primer producto,** construido a partir de los requisitos del producto.
- **Menos errores falsos:** un cambio ahora se compara con lo que el pedido quería decir.

## 0.42.0 – 0.42.5 — 2026-10-15 a 2026-10-16 · Publicadas
- **Apps generadas más completas:**
  - campos de lista de opciones, que aparecen como insignias de color y se pueden filtrar;
  - campos de valor en reales brasileños, con totales;
  - género gramatical correcto en las etiquetas;
  - una vista de **Detalles** para registros con muchos campos.
- **Los sitios generados ya no inventan números de registro profesional ni identificadores de empresa.** Lo no informado aparece como "a
  informar".
- **Entrenar a un agente ya no corta parte de su tarjeta.**
- **Una verificación semanal sin elementos en rojo,** una restauración de la copia de seguridad probada en un contenedor limpio y una guía
  de rutina del operador.

## 0.41.0 – 0.41.2 — 2026-10-14 a 2026-10-15 · Publicadas
- **Las apps generadas ganaron:**
  - edición, y eliminación con confirmación en la propia pantalla;
  - búsqueda y un mensaje de éxito después de guardar;
  - números y fechas en formato brasileño;
  - un diseño en tarjetas en el móvil;
  - una paleta de colores adecuada al negocio;
  - ordenación por columna, y listas que cargan por lotes.
- **Revisión renderizada de los sitios:** el contraste del texto se mide como lo pinta el navegador.
- **Una prueba A/B de pago mostró** que un brief de diseño produce sitios claramente mejores. Activarlo es decisión del fundador.

## 0.40.0 – 0.40.6 — 2026-10-12 a 2026-10-14 · Publicadas
- **Uso de punta a punta probado en un navegador real:** crear un proyecto, construirlo, verlo en la vista previa, conversar en el Chat y
  luego preparar y confirmar un cambio.
- **Cada ejecución termina en un único resultado claro:** falló sin cambios, parcial, aplicada, ya aplicada, sin efecto o indeterminado.
  Cada resultado dice si es seguro ejecutarla de nuevo.
- **Mejoras en el cockpit:**
  - un inicio de sesión nuevo empieza sin proyecto abierto;
  - un botón **+** lleva directo al asistente de nuevo proyecto;
  - el estado neutro siempre está a un clic.
- **Refuerzo de seguridad:** la vista previa y el flujo de deshacer se reforzaron tras una revisión independiente.
- **Primer instalador para un servidor nuevo.** Probado en un contenedor; la instalación limpia en un servidor real aún no está comprobada.

## 0.39.0 — 2026-10-12 · Publicada
- **EXPLICAR es más resiliente y se puede configurar.** Usa por defecto un modelo económico, y dice qué hará un comando y si se puede
  deshacer.
- **Resúmenes en lenguaje sencillo de los comandos** en proyectos de sitio, sin costo de IA.

## 0.37.0 – 0.38.0 — 2026-10-06 · Publicadas
- **El Chat es el camino para cambiar un proyecto.** Los bloques de comando se guardan por proyecto y no pasan a otro. Hay un único camino
  gobernado de EJECUTAR.
- **Cada cambio se compara con su intención después de ejecutarse.** Cada elemento queda como confirmado, falló o no verificado. Un código
  de salida exitoso ya no se llama éxito funcional.
- **La Fábrica muestra sus etapas reales,** con el agente actual y los tiempos reales.

## 0.36.0 — 2026-09-21 · Publicada
- **Proyectos aislados en el cockpit.** Los bloques de comando, las conversaciones y las lecciones pertenecen a un proyecto.

## 0.35.0 — 2026-08-13 · Publicada
- **Se puede definir un modelo para cada agente,** con un cambio auditable cuando falla un proveedor.
- **El ciclo de lecciones lo cura una persona.**

## 0.33.0 – 0.34.0 — 2026-07-25 a 2026-07-28 · Publicadas
- **Refuerzo de seguridad de credenciales y secretos.** Se eliminaron alternativas inseguras. Se ensayó y luego se realizó un cambio
  completo de secretos.

## 0.2.0 – 0.32.8 — 2026-06-30 a 2026-07-03 · Publicadas
- **El cockpit pasó a una capa de componentes React,** con tarjetas de agentes en vivo y costo por ejecución.
- **La versión que muestra el cockpit se lee de este historial.**

## 0.1.0 — 2026-06-19 · Publicada
- **Primera versión:** un cockpit multi-IA autoalojado, con aprobación humana antes de la ejecución.

---

## Planificado
Todavía no son funcionalidades. Consulta el [roadmap](docs/roadmap-es.md).
- Recuperación completa en un servidor limpio.
- Un instalador guiado: un comando y un asistente de configuración.
- Más stacks y bases de datos.
