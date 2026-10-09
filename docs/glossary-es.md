# Glosario — CBini OrquestrAI

🇪🇸 **Español** · 🇧🇷 [Português](glossary-br.md) · 🇺🇸 [English](glossary.md) · [README](../README-ES.md)

Definiciones en lenguaje claro de los términos usados en esta documentación.

| Término | Qué significa |
|---|---|
| **Cockpit** | La interfaz web donde trabaja el operador: proyectos, chat, propuestas, costos, estado. |
| **Operador** | La persona que usa OrquestrAI y toma las decisiones. |
| **Proyecto** | La unidad de trabajo y de aislamiento. Tiene sus propios archivos, conversación, memoria, ejecuciones, vistas previas y costos. Otros proyectos no lo ven. |
| **Chat** | Donde usted conversa con la IA sobre el proyecto activo. El chat lee y propone; nunca ejecuta. |
| **Modelo / proveedor** | El modelo de IA que responde (y la empresa que lo opera). Se puede cambiar de modelo; el contexto se queda con el proyecto. |
| **Agentes** | Funciones especializadas de IA (estrategia, arquitectura, código, revisión, pruebas, documentación), cada una asignada a un modelo. |
| **Malla de agentes / planificador** | El equipo de agentes de una tarea. El planificador decide cuáles necesita la tarea; los demás se omiten y no cuestan nada. |
| **Bloque de comando** (*BLOCO*) | Un cambio propuesto, mostrado primero como resumen humano (objetivo, datos, archivos, efecto) y después como código completo. Nada se ejecuta antes de aprobarse. |
| **LAVE** | La rutina de revisión de todo bloque: **L**eer (*Ler*), **A**valuar (*Avaliar*), **V**erificar, **E**jecutar (*Executar*). El nombre viene del portugués. |
| **Explicar** | Pide una explicación en lenguaje claro de un bloque sin ejecutar nada. |
| **Vetar** | Rechaza una versión de un bloque de forma definitiva; el motivo alimenta el siguiente plan. |
| **Ejecución** | Ejecutar un bloque aprobado, en un entorno aislado que solo ve ese proyecto. |
| **Revertir** | Deshacer un cambio soportado, después de mostrar qué se deshará. La reversión también queda registrada y puede rehacerse. |
| **Fábrica** | Convierte un brief corto en proyecto: Planificar → Construir → Revisar → Generar → Publicar, con el progreso visible para el operador. |
| **Sitio estático** | Proyecto en HTML, CSS y JavaScript, generado por la Fábrica y modificado mediante bloques de comando. |
| **Aplicación full stack** | Aplicación web con interfaz, API y base de datos SQLite, generada desde una plantilla probada, ejecutándose sin acceso a la red y evolucionando con cambios aditivos. |
| **Vista previa** | Donde se abre un sitio o aplicación generados, en un origen separado del cockpit. |
| **Publicación** | Poner en línea una versión nueva de una aplicación full stack; automática tras un cambio aprobado, manteniendo la versión anterior si la nueva falla. |
| **Cuarentena** | Adonde va un proyecto eliminado: sale de uso y de la lista, pero no se destruye. |
| **Lecciones** | Conocimiento que el sistema propone a partir de su propio trabajo; llega a los agentes solo después de que una persona lo aprueba. |
| **Plano de control / plano de ejecución** | Donde personas y agentes deciden (control) frente a donde los cambios ocurren de verdad (ejecución). |
| **Revisión independiente** | Auditoría técnica de solo lectura de cambios sensibles, hecha por un revisor que no los escribió. Un hallazgo bloqueante detiene la promoción. |
| **Puerta humana** | Punto de decisión que solo una persona puede liberar, como aprobar una ejecución o promover una capacidad. |
| **Disponible / Configurable / Planificado** | Etiquetas de madurez. *Disponible* significa demostrado por pruebas automáticas y por una persona en una instalación real. |
| **Autoalojado** | Instalado en infraestructura que la organización controla. El contenido enviado a proveedores de IA externos sigue sujeto a sus términos. |
