# Preguntas frecuentes — CBini OrquestrAI

🇪🇸 **Español** · 🇧🇷 [Português](faq-br.md) · 🇺🇸 [English](faq.md) · [README](../README-ES.md)

**¿OrquestrAI es una IA?**
No. Es una capa de ingeniería que coordina modelos y proveedores de IA, agentes especializados, contexto por proyecto, ejecución
supervisada, auditoría y reversibilidad, con una persona decidiendo los puntos donde un cambio se vuelve real.

**¿Reemplaza a un desarrollador?**
No. Organiza el trabajo de la IA para que un equipo pueda usarlo con gobernanza: alguien define la intención, revisa y aprueba.

**¿OrquestrAI es de código abierto?**
No. Este repositorio es la vitrina y la documentación pública. El código fuente del producto es privado; este proyecto no se distribuye
como software de código abierto y su modelo de licenciamiento está actualmente en definición.

**¿Este repositorio es el código fuente?**
No. Solo contiene documentación pública. El producto se desarrolla en un repositorio privado.

**¿Qué está disponible hoy?**
Vea la tabla de madurez en el [README](../README-ES.md#madurez-actual) y la [matriz de evidencia](evidence-es.md). *Disponible* significa
demostrado por pruebas automáticas y por un operador humano en una instalación real.

**¿La IA ejecuta cambios por su cuenta?**
No. El chat nunca ejecuta. Cada cambio concreto se convierte en un bloque de comando que solo corre después de que una persona lo revisa y
lo confirma.

**¿El contexto queda atado a un modelo? ¿Los proyectos comparten memoria?**
El contexto pertenece al proyecto: el operador puede cambiar de modelo y el siguiente recibe el mismo contexto. Otro proyecto parte de su
propio contexto y no hereda el primero.

**¿Qué significa "reversible" aquí?**
En los cambios soportados, el sistema registra lo que un cambio puede tocar y mide lo que realmente cambió; deshacerlo muestra antes qué se
revertirá. Los datos escritos por una aplicación en ejecución quedan fuera de este mecanismo por diseño; los protege el respaldo diario.
Deshacer un cambio en una aplicación full stack restaura su código y vuelve a publicar la versión anterior; las columnas ya agregadas a la
base de datos se mantienen, así que no se pierde ningún dato.

**¿Mis datos se quedan en mi servidor?**
OrquestrAI se ejecuta en infraestructura que usted controla. Cuando se usan proveedores de IA externos, el contenido enviado a ellos queda
sujeto a sus servicios y políticas. Usted elige qué proveedores configurar. Detalles: [fronteras de confianza](trust-es.md).

**¿Qué proveedores de IA se admiten?**
Las rutas validadas de los agentes usan hoy modelos de Anthropic y OpenAI. Groq, Gemini, OpenRouter, Cerebras, Z.ai y APIs compatibles con
OpenAI pueden configurarse y probarse desde el panel.

**¿Puede construir aplicaciones completas?**
Sí, dentro de un camino soportado. Los sitios estáticos y el primer camino full stack (React + Vite + TypeScript, Express, SQLite)
funcionan de punta a punta hoy; una aplicación generada tiene un modelo de datos y evoluciona mediante cambios aditivos que usted aprueba.

**¿Puedo instalarlo yo mismo?**
Hoy la instalación sigue un procedimiento manual documentado. Hay un instalador guiado planificado.

**¿Cómo puedo dar mi opinión o participar de un piloto?**
Por las Discussions e Issues de este repositorio. No reporte problemas de seguridad en público: vea [SECURITY.md](../SECURITY.md).

[← Volver al README](../README-ES.md)
