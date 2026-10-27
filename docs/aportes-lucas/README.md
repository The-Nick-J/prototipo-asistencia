# Integración de los aportes de Lucas Ahumada

Esta entrega desarrolla los issues [18](https://github.com/The-Nick-J/prototipo-asistencia/issues/18), [19](https://github.com/The-Nick-J/prototipo-asistencia/issues/19) y [25](https://github.com/The-Nick-J/prototipo-asistencia/issues/25). Es una propuesta documental para revisar e incorporar al informe compartido.

## Ubicación de cada aporte

1. Incorporar `01-perfiles-y-necesidades.md` en «Análisis de requerimientos».
2. Incorporar `02-requerimientos-funcionales.md` a continuación de los perfiles. Contiene 22 requerimientos y 10 reglas de consistencia.
3. Incorporar `03-casos-de-uso-apoderados.md` en «BPMN y casos de uso», junto con las especificaciones de los otros perfiles.
4. Integrar `04-referencias.md` en la bibliografía general, armonizando las letras de las citas de Matus.

La [versión Word](Aporte_Lucas_Perfiles_Requerimientos_Casos_de_Uso.docx) reúne estos mismos aportes para facilitar su incorporación. El informe original del equipo y el documento compartido de Google Docs no se han sobrescrito.

## Decisiones a resolver antes de aprobar esta base

- **Asignaciones de inspectoría:** RF-03 a RF-07 permiten registrar a docentes e inspectoría según los cursos habilitados. Confirmar quién mantendrá esas asignaciones al implementar el sistema; en el prototipo estarán precargadas.
- **Unidad de asistencia:** se propone curso y fecha; confirmar si se requiere jornada o bloque horario.
- **Correcciones docentes:** la propuesta concentra la modificación posterior en administración/inspectoría; confirmar si habrá un plazo de edición docente.
- **Calendario y vínculos:** se asumen precargados y validados por el establecimiento para el prototipo.
- **Conectividad rural:** el trabajo sin conexión queda pendiente de análisis; no se promete como capacidad del prototipo.

## Coordinación con los otros issues

- El diagrama de casos de uso debe conservar los límites de acceso y las funciones RF.
- El BPMN debe diferenciar una ausencia de un registro faltante y ubicar la justificación en administración/inspectoría.
- Los requerimientos no funcionales deben precisar seguridad, usabilidad y rendimiento sin duplicar servicios.
- El plan de pruebas puede reutilizar los criterios de aceptación; la simulación en Figma no verifica controles reales de acceso ni persistencia.
- El equipo de Figma puede usar los identificadores AP para enlazar vistas y funciones. No se presupone que esas vistas ya estén creadas.

## Comprobación por issue

| Issue | Evidencia preparada | Pendiente para su cierre |
| --- | --- | --- |
| 18 Perfiles y necesidades | Tres perfiles, necesidades, permisos, límite de consulta de apoderados y fuentes | Acordar decisiones de alcance e integrar el texto en el informe |
| 19 Requerimientos funcionales | 22 RF numerados con actor, resultado esperado y criterio de aceptación | Validar reglas con el equipo e integrar el catálogo |
| 25 Casos de uso de apoderados | Seis especificaciones con actor, flujo, precondiciones, postcondiciones y alternativas | Alinear diagrama y mockups e integrar las especificaciones |

Las casillas de los issues deben marcarse cuando el material esté revisado e incorporado al informe. No se declara realizada una implementación, una entrevista ni una prueba con usuarios.
