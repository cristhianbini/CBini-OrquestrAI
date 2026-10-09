# Modelo de seguridad — CBini OrquestrAI

🇪🇸 **Español** · 🇧🇷 [Português](security-br.md) · 🇺🇸 [English](security.md) · [README](../README-ES.md) · [Arquitectura](arch-es.md) · [Fronteras de confianza](trust-es.md)

Esta página indica qué está diseñado para proteger OrquestrAI, qué está demostrado, qué sigue en validación, qué supone y qué no intenta
hacer. Es un resumen público; los detalles operativos se omiten a propósito. Reporte vulnerabilidades en privado, nunca en issues ni
discusiones públicas.

## Contra qué protege

- Que la salida de una IA cambie un sistema sin que una persona lo decida.
- Que los comandos, sesiones o datos de un proyecto afecten a otro.
- Cambios que no pueden explicarse, atribuirse ni deshacerse.
- La pérdida silenciosa del estado operativo.

## Propiedades demostradas

| Propiedad | Qué significa |
|---|---|
| Ejecución explícita | Ningún comando propuesto por la IA se ejecuta sin un paso de confirmación humana; el chat no puede ejecutar. El contenido generado por la Fábrica lo escriben generadores validados, no la ejecución de comandos escritos por la IA. |
| El veto es definitivo | Una versión vetada de un comando nunca puede ejecutarse. |
| Ejecución aislada | Los comandos aprobados se ejecutan en un entorno desechable sin red, con sistema de solo lectura, sin privilegios y solo con su propio proyecto montado. |
| Rechazar ante la duda | Los comandos cuyo efecto no puede analizarse con seguridad se rechazan antes de ejecutarse. |
| Inspección de solo lectura | La terminal del proyecto es de solo lectura y sin red, en un contenedor por conexión. |
| Confirmación reforzada para accesos sensibles | El inicio de sesión usa dos factores; las sesiones de terminal y administrativas exigen un segundo factor nuevo. |
| Evidencia a prueba de manipulación | Las ejecuciones se registran en un log encadenado por hash; las sesiones de terminal se sellan. |
| Cambios reversibles | Los cambios de archivos soportados se miden y pueden revertirse con vista previa de lo que se deshará. |
| Secretos en reposo | Las claves de los proveedores se cifran en el servidor y nunca se devuelven al navegador. |
| Orígenes separados | Las vistas previas de los proyectos se sirven desde un origen distinto al del cockpit. |
| Disciplina de recuperación | Respaldos cifrados diarios fuera del servidor, verificados automáticamente (completitud y secretos en claro); restauración demostrada en aislamiento. |
| Aplicaciones full stack | Cada aplicación generada se ejecuta en su propio entorno sin acceso a la red, a partir de versiones inmutables, alcanzable solo por el origen de vista previa; si una versión nueva falla, la anterior sigue en línea. |
| Datos de aplicación en los respaldos | Las bases de datos de las aplicaciones generadas entran en el respaldo diario mediante una instantánea consistente. |

"Demostrado" significa cubierto por pruebas automáticas y confirmado por un operador humano en una instalación real.

## En validación

- **Recuperación completa en un servidor nuevo.**

## Supuestos

- El servidor lo opera un administrador de confianza y se mantiene actualizado.
- Los operadores protegen sus propias credenciales y dispositivos de segundo factor.
- Los proveedores de IA procesan el contenido que reciben bajo sus propios términos.

## Límites y no objetivos

- **Frontera de datos.** Autoalojar mantiene el plano de control, los proyectos y los registros en su infraestructura. Cuando se usa un
  proveedor de IA en la nube, el contenido necesario para cada llamada (solicitudes, contexto y fragmentos de código) se envía a ese
  proveedor. OrquestrAI no lo impide; le permite elegir qué proveedores se configuran.
- **Alcance de revertir.** Revertir cubre archivos cambiados mediante bloques de comando. No deshace datos escritos por una aplicación en
  ejecución; esa es la función de los respaldos.
- **No es un sandbox para código arbitrario.** El aislamiento está pensado para cambios aprobados por el operador en sus propios proyectos,
  no para ejecutar cargas de terceros no confiables.
- **No se declara ninguna certificación de cumplimiento.**
- **Instalación de una sola organización.** El hosting multiinquilino no es un objetivo de la versión actual.

## Revisión independiente

Los cambios que afectan la ejecución, el aislamiento o la recuperación los revisa, antes de promoverse, un auditor independiente con acceso
de solo lectura. Un hallazgo que bloquea la promoción la detiene, sin importar el resultado de las pruebas funcionales. Ver
[evidencia de ingeniería](evidence-es.md).
