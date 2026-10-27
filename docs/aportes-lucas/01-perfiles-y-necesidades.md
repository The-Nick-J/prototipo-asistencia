# Perfiles de usuario y sus necesidades

## Alcance del análisis

El sistema propuesto permitirá registrar y consultar la asistencia escolar mediante tres perfiles: docentes, administración e inspectoría, y apoderados. El objetivo es que cada persona disponga de las funciones y de la información necesarias para su tarea, conservando una delimitación explícita de los datos que puede consultar o modificar. Los perfiles se derivan del caso de estudio y de la descripción del proyecto; constituyen una propuesta de análisis que deberá validarse con representantes del establecimiento.

La asignatura distingue los requerimientos del usuario, comprensibles para quienes utilizarán el sistema, de los requerimientos del sistema, que detallan los servicios y sus restricciones. También exige especificaciones correctas, completas, consistentes, claras, realistas y verificables (Matus, 2026a, diapositivas 8–9 y 20). Por ello, las necesidades que siguen se expresan primero como objetivos de cada perfil y luego se relacionan con requerimientos identificados.

## Docentes

El docente necesita registrar la asistencia de los estudiantes de los cursos que tiene asignados y consultar posteriormente lo que registró. En el contexto propuesto, utiliza el sistema durante la jornada de clases; por ello, debe reconocer el curso y la fecha antes de ingresar información y distinguir con claridad un registro confirmado de uno que todavía no se ha guardado.

- **N-D01. Identificar el curso correcto:** visualizar sus cursos asignados y la nómina correspondiente a la fecha de registro.
- **N-D02. Registrar la asistencia completa:** asignar a cada estudiante el estado observado y recibir confirmación del registro.
- **N-D03. Consultar antecedentes:** revisar la asistencia de los cursos asignados por fecha o intervalo.
- **N-D04. Detectar equivocaciones:** reconocer el estado guardado y disponer de un procedimiento para solicitar su corrección a administración o inspectoría.

El docente podrá consultar la identidad de los estudiantes de sus cursos, los estados de asistencia y sus fechas. La propuesta limita su registro a cursos asignados. Después de confirmar una nómina, las correcciones se canalizarán a administración o inspectoría para conservar su trazabilidad. Esta distribución es una decisión propuesta para el proyecto y requiere acuerdo del equipo.

## Administración e inspectoría

Este perfil necesita revisar los registros del establecimiento, identificar nóminas que aún no se han completado y atender errores o justificaciones. A diferencia del docente, su responsabilidad abarca la supervisión de varios cursos y la regularización de antecedentes. Debe poder distinguir entre una inasistencia registrada y la falta de un registro, porque estas situaciones requieren acciones diferentes.

- **N-A01. Supervisar el registro diario:** identificar qué cursos tienen asistencia confirmada y cuáles siguen pendientes.
- **N-A02. Consultar información del establecimiento:** revisar la asistencia de un curso o de un estudiante para un período definido.
- **N-A03. Regularizar errores:** corregir un estado con un motivo y conservar quién lo modificó, cuándo y cuál era el valor anterior.
- **N-A04. Gestionar justificaciones:** registrar la aceptación de una justificación y distinguirla de una ausencia sin justificar.
- **N-A05. Obtener información consolidada:** consultar totales por estado, sin transformar automáticamente los días sin registro en ausencias.
- **N-A06. Registrar desde inspectoría:** registrar una nómina inicial de los cursos para los que inspectoría esté habilitada, siguiendo las mismas reglas de confirmación que los docentes.

Podrá consultar las nóminas, estados de asistencia, cursos, fechas y el historial de cambios de los registros del establecimiento. El motivo interno de una corrección o justificación estará reservado al personal autorizado. En concordancia con el README, inspectoría también podrá registrar nóminas iniciales de cursos habilitados. Dentro de este perfil agrupado, la función de registro se asignará al personal de inspectoría y no se extenderá automáticamente a toda cuenta administrativa. La supervisión y regularización corresponderán al personal autorizado de administración e inspectoría.

## Apoderados

El apoderado necesita consultar la asistencia de sus hijos sin depender de la disponibilidad del libro físico ni acceder a antecedentes de otros estudiantes. Puede tener más de un hijo vinculado a su cuenta, por lo que necesita identificar a cuál corresponde la información que está viendo.

- **N-P01. Identificar a sus hijos vinculados:** acceder a una lista limitada a los estudiantes asociados a su cuenta por el establecimiento.
- **N-P02. Revisar un período:** consultar las fechas y los estados de asistencia de un hijo seleccionado.
- **N-P03. Comprender una jornada:** revisar el detalle de una fecha y reconocer si existe una ausencia justificada.
- **N-P04. Obtener un resumen:** consultar totales de asistencia e inasistencia del período mostrado.
- **N-P05. Comprender la falta de información:** distinguir entre ausencia, jornada sin registro y ausencia de resultados en una consulta.

**Los apoderados solo podrán consultar la asistencia de sus hijos vinculados mediante una relación vigente y validada por el establecimiento.** No podrán acceder a nóminas completas del curso, registros de otros estudiantes, motivos internos de regularización ni al historial administrativo de cambios. Tampoco podrán registrar, corregir o justificar asistencia desde este alcance. La justificación seguirá el canal definido por el establecimiento; su aceptación será ingresada por administración o inspectoría.

## Matriz de permisos

| Operación o información | Docente | Administración e inspectoría | Apoderado |
| --- | --- | --- | --- |
| Consultar cursos y nóminas | Solo cursos asignados | Cursos del establecimiento | Sin acceso a nóminas |
| Registrar nómina inicial | Cursos asignados | Inspectoría: cursos habilitados; administración: sin permiso automático | Sin permiso |
| Consultar asistencia por estudiante | Estudiantes de cursos asignados | Estudiantes del establecimiento | Solo hijos vinculados |
| Consultar asistencia por curso | Cursos asignados | Cursos del establecimiento | Sin permiso |
| Corregir registros confirmados | Solicitar por canal del establecimiento | Sí, con motivo e historial | Sin permiso |
| Registrar justificación aceptada | Sin permiso en esta propuesta | Sí, sobre una ausencia registrada | Sin permiso |
| Consultar totales | Cursos asignados | Cursos y estudiantes del establecimiento | Solo del hijo seleccionado |
| Consultar historial administrativo y motivos internos | Sin permiso en esta propuesta | Sí | Sin permiso |
| Cambiar vínculos apoderado–estudiante | Fuera del alcance funcional de esta entrega | Datos preconfigurados para el prototipo | Sin permiso |

La identificación de una cuenta y la autorización de una operación se tratarán como decisiones diferentes. Se propone validar el permiso sobre cada estudiante o curso solicitado y rechazar accesos fuera de su ámbito. Esta decisión aplica los principios de mínimo privilegio y denegación por defecto descritos por OWASP Foundation (s. f.).

## Decisiones que delimitan esta propuesta

1. **Unidad de asistencia:** se propone una nómina por curso y fecha, con un estado por estudiante. Debe confirmarse si el establecimiento requiere jornada o bloque horario adicional.
2. **Estados:** presente, ausente y ausencia justificada. «Sin registro» describe falta de información; no equivale a una ausencia ni a un estado confirmado.
3. **Correcciones:** solo administración e inspectoría modifican información confirmada en esta propuesta. El registro inicial de inspectoría se limita a cursos habilitados. Si se habilita edición posterior para docentes, deberá modificarse esta base de permisos.
4. **Datos de base:** cuentas, roles, matrícula, cursos, asignaciones docentes y vínculos apoderado–estudiante estarán precargados en el prototipo. Su administración completa no se incorpora a estos issues.
5. **Conectividad:** el prototipo representa consultas y registros con conexión. No se declara resuelto el trabajo sin conexión en sectores rurales.

Estas decisiones permiten construir una base coherente para revisión. No representan entrevistas realizadas ni políticas ya aprobadas por un establecimiento.
