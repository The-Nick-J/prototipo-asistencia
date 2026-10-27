# Requerimientos funcionales

## Criterio de especificación

Los siguientes requerimientos detallan funciones observables del sistema desde la perspectiva de un perfil. Se han organizado en acceso común, registro por docentes e inspectoría, supervisión administrativa y consulta de apoderados. Cada identificador RF es estable para relacionar el análisis con los casos de uso, las pantallas y las pruebas. Las condiciones de seguridad, usabilidad o rendimiento que describen calidad deberán desarrollarse en la sección de requerimientos no funcionales; aquí se especifican servicios y restricciones funcionales de acceso.

En la asignatura, los requerimientos funcionales describen servicios y respuestas del sistema, y deben buscar completitud y consistencia (Matus, 2026a, diapositivas 12–13). El ejercicio de metodologías y herramientas también plantea definir las funciones desde la perspectiva del usuario (Matus, 2026b, diapositiva 35). Aplicando estos criterios, se proponen 22 requerimientos con actor, resultado y comprobación.

## Catálogo de funciones

### RF-01 Iniciar sesión

**Actor:** Docente, administración/inspectoría o apoderado.

El sistema deberá permitir que una persona con cuenta habilitada inicie sesión mediante sus credenciales y acceda al espacio de su perfil.

**Criterio de aceptación:** Con credenciales válidas se presenta el espacio correspondiente; con credenciales inválidas no se abre una sesión.

**Necesidad relacionada:** Acceso común.

### RF-02 Cerrar sesión

**Actor:** Docente, administración/inspectoría o apoderado.

El sistema deberá permitir cerrar la sesión y devolver a la persona a la pantalla de acceso.

**Criterio de aceptación:** Después del cierre, intentar consultar una vista protegida solicita autenticación y no muestra datos de asistencia.

**Necesidad relacionada:** Acceso común.

### RF-03 Listar cursos asignados

**Actor:** Docente o personal de inspectoría habilitado para el curso.

El sistema deberá mostrar al docente o al personal de inspectoría los cursos para los que tiene habilitado el registro de asistencia.

**Criterio de aceptación:** Un docente con dos cursos asignados ve esos dos y no obtiene acceso a un tercer curso no asignado.

**Necesidad relacionada:** N-D01, N-A06.

### RF-04 Consultar nómina para registro

**Actor:** Docente o personal de inspectoría habilitado para el curso.

El sistema deberá presentar la nómina de estudiantes del curso asignado y de la fecha seleccionada, indicando el curso y la fecha de trabajo.

**Criterio de aceptación:** Al seleccionar un curso y fecha válidos se muestra su nómina; una asignación ajena o fecha fuera de la matrícula aplicable no habilita el registro.

**Necesidad relacionada:** N-D01, N-A06.

### RF-05 Marcar asistencia inicial

**Actor:** Docente o personal de inspectoría habilitado para el curso.

El sistema deberá permitir a quien registra la nómina asignar presente o ausente a cada estudiante de la nómina antes de confirmar el registro.

**Criterio de aceptación:** La persona habilitada puede revisar y cambiar las marcas aún no confirmadas; ningún estudiante queda presente o ausente por inferencia de una casilla vacía.

**Necesidad relacionada:** N-D02, N-A06.

### RF-06 Confirmar nómina completa

**Actor:** Docente o personal de inspectoría habilitado para el curso.

El sistema deberá permitir confirmar la asistencia del curso y fecha cuando todos los estudiantes de la nómina tengan una marca válida, e informar el resultado del guardado.

**Criterio de aceptación:** Con una marca faltante, no se confirma y se identifica qué falta. Con la nómina completa se confirma una sola versión, asociada al autor, curso y fecha.

**Necesidad relacionada:** N-D02, N-A06.

### RF-07 Recuperar nómina confirmada

**Actor:** Docente o personal de inspectoría habilitado para el curso.

El sistema deberá mostrar a quien registra la nómina la asistencia ya confirmada del curso y fecha seleccionados, en lugar de crear un segundo registro inicial.

**Criterio de aceptación:** Reabrir la misma combinación curso–fecha recupera los estados guardados y no permite duplicar la nómina.

**Necesidad relacionada:** N-D02, N-D04, N-A06.

### RF-08 Consultar historial del curso asignado

**Actor:** Docente.

El sistema deberá permitir al docente consultar la asistencia de un curso asignado para una fecha o intervalo, mostrando fechas, estudiantes, estados registrados y totales por estado.

**Criterio de aceptación:** La consulta devuelve solo información del curso asignado dentro del intervalo; un intervalo invertido se rechaza con una indicación para corregirlo. Los totales coinciden con los registros confirmados y no cuentan jornadas sin registro como ausencias.

**Necesidad relacionada:** N-D03.

### RF-09 Supervisar registro por curso

**Actor:** Administración e inspectoría.

El sistema deberá mostrar, para una fecha seleccionada, cuáles cursos del establecimiento tienen nómina confirmada y cuáles no tienen registro.

**Criterio de aceptación:** Con un curso confirmado y otro pendiente, ambos se identifican sin convertir la nómina pendiente en ausencias de sus estudiantes.

**Necesidad relacionada:** N-A01.

### RF-10 Consultar asistencia de un curso

**Actor:** Administración e inspectoría.

El sistema deberá permitir consultar los registros de asistencia de un curso del establecimiento por fecha o intervalo.

**Criterio de aceptación:** La consulta muestra únicamente el curso y período seleccionados; permite revisar los estados de sus estudiantes.

**Necesidad relacionada:** N-A02.

### RF-11 Consultar historial individual

**Actor:** Administración e inspectoría.

El sistema deberá permitir consultar la asistencia de un estudiante del establecimiento para un intervalo, identificando sus fechas y estados.

**Criterio de aceptación:** Al cambiar de estudiante o período se obtiene el historial correspondiente; no se conservan resultados de la selección anterior como si fueran del nuevo estudiante.

**Necesidad relacionada:** N-A02.

### RF-12 Corregir asistencia confirmada

**Actor:** Administración e inspectoría.

El sistema deberá permitir corregir un estado confirmado a presente o ausente, exigiendo un motivo de corrección.

**Criterio de aceptación:** Con motivo vacío no se aplica el cambio. Con motivo válido se conserva el estado anterior, el nuevo, la persona responsable y la fecha y hora de la corrección.

**Necesidad relacionada:** N-A03.

### RF-13 Registrar justificación aceptada

**Actor:** Administración e inspectoría.

El sistema deberá permitir transformar una ausencia registrada en ausencia justificada cuando el establecimiento acepte su justificación, registrando un motivo interno.

**Criterio de aceptación:** Una ausencia puede pasar a justificada con motivo y trazabilidad. Un presente no admite esta operación. El motivo interno no aparece en las consultas de apoderados.

**Necesidad relacionada:** N-A04.

### RF-14 Revisar historial de cambios

**Actor:** Administración e inspectoría.

El sistema deberá permitir consultar las correcciones y justificaciones de un registro, mostrando autor, fecha y hora, motivo y estados anterior y posterior.

**Criterio de aceptación:** Un registro con dos cambios muestra ambos en orden cronológico; esta consulta no está disponible para docentes o apoderados en la propuesta.

**Necesidad relacionada:** N-A03, N-A04.

### RF-15 Consultar totales del establecimiento

**Actor:** Administración e inspectoría.

El sistema deberá presentar totales de presentes, ausentes y ausencias justificadas para un curso o estudiante en el período elegido.

**Criterio de aceptación:** Los totales coinciden con los registros confirmados del período. Los días sin registro se identifican aparte y no incrementan las ausencias.

**Necesidad relacionada:** N-A05.

### RF-16 Listar hijos vinculados

**Actor:** Apoderado.

El sistema deberá mostrar al apoderado únicamente los estudiantes vinculados a su cuenta mediante una relación vigente validada por el establecimiento.

**Criterio de aceptación:** Una cuenta con dos hijos vinculados muestra solo esos dos; una cuenta sin vínculos muestra que no tiene estudiantes habilitados para consulta.

**Necesidad relacionada:** N-P01.

### RF-17 Consultar historial de un hijo

**Actor:** Apoderado.

El sistema deberá permitir al apoderado seleccionar un hijo vinculado y consultar sus fechas y estados de asistencia dentro de un intervalo válido.

**Criterio de aceptación:** El resultado contiene solo al hijo seleccionado y las fechas del intervalo; cambiar de hijo vuelve a obtener sus datos y no muestra los del anterior.

**Necesidad relacionada:** N-P02.

### RF-18 Consultar detalle de una fecha

**Actor:** Apoderado.

El sistema deberá permitir al apoderado consultar el detalle de asistencia de su hijo para una fecha seleccionada, indicando su identidad, fecha y estado registrado.

**Criterio de aceptación:** El detalle corresponde al hijo y fecha elegidos. Si no existe registro, se informa expresamente y no se presenta una ausencia ficticia.

**Necesidad relacionada:** N-P03, N-P05.

### RF-19 Reconocer ausencia justificada

**Actor:** Apoderado.

El sistema deberá mostrar el estado ausencia justificada cuando exista una justificación aceptada para el registro consultado, sin revelar el motivo administrativo interno.

**Criterio de aceptación:** Una ausencia justificada se distingue de una ausencia sin justificar. La vista no muestra motivos internos, documentos de otros estudiantes ni historial de cambios administrativo.

**Necesidad relacionada:** N-P03.

### RF-20 Consultar resumen de un hijo

**Actor:** Apoderado.

El sistema deberá presentar los totales de presentes, ausentes y ausencias justificadas del hijo seleccionado para el intervalo consultado.

**Criterio de aceptación:** Con seis presentes, dos ausentes y una ausencia justificada, el resumen muestra 6, 2 y 1. Las jornadas sin registro se muestran separadas y no se suman a esas ausencias.

**Necesidad relacionada:** N-P04.

### RF-21 Informar consultas sin datos

**Actor:** Docente, administración/inspectoría o apoderado, dentro de su ámbito.

El sistema deberá informar cuando no existan registros confirmados para la selección consultada, diferenciando esta situación de una inasistencia registrada.

**Criterio de aceptación:** Un período sin registros muestra «Sin registros para el período»; un registro ausente se muestra como ausente y nunca se sustituye por el mensaje de falta de datos.

**Necesidad relacionada:** N-D03, N-A01, N-P05.

### RF-22 Rechazar operaciones fuera del ámbito

**Actor:** Docente, administración/inspectoría o apoderado.

El sistema deberá rechazar una solicitud de consulta o modificación que no esté autorizada por el perfil y su relación con el curso o estudiante, sin devolver datos del recurso solicitado.

**Criterio de aceptación:** Un apoderado que solicita un estudiante no vinculado no obtiene sus datos; un docente no accede a un curso ajeno; un apoderado no puede modificar ningún registro.

**Necesidad relacionada:** Restricción transversal.

## Reglas de negocio y consistencia

**RN-01 Ámbito de consulta.** El rol habilita operaciones y la asignación al curso o el vínculo con el estudiante delimita los datos. Ser apoderado no concede acceso a todos los estudiantes.

**RN-02 Registro único.** Se propone un registro inicial por estudiante, curso y fecha. Reabrir una nómina confirmada recupera ese registro.

**RN-03 Estados excluyentes.** Un registro confirmado tiene exactamente un estado: presente, ausente o ausencia justificada. No puede tener dos estados simultáneos.

**RN-04 Información faltante.** La ausencia de registro no prueba una inasistencia. Las consultas deben distinguir falta de datos, ausencia registrada y fecha sin jornada lectiva cuando esta esté definida en el calendario precargado.

**RN-05 Justificación.** Solo administración e inspectoría registran la aceptación de una justificación sobre una ausencia existente. El apoderado la consulta; no la aprueba ni la registra en este alcance.

**RN-06 Trazabilidad de cambios.** Las correcciones y justificaciones conservan autor, momento, motivo y estados anterior y posterior; no se sustituyen silenciosamente los antecedentes.

**RN-07 Períodos.** La fecha inicial no supera a la final. Las consultas solo muestran registros del intervalo y del estudiante o curso autorizado seleccionado.

**RN-08 Resumen.** Los tres totales de estados confirmados son excluyentes. Una ausencia justificada se cuenta en su propia categoría, sin volver a contarse en ausente. La suma coincide con los registros confirmados del alcance consultado.

**RN-09 Vínculos.** Los vínculos apoderado–estudiante son datos validados por el establecimiento. El apoderado no puede agregarse estudiantes por conocer su identificador.

**RN-10 Confirmación y falla.** Solo una operación confirmada se comunica como guardada. Si falla el guardado, se informa el error y no se presenta una confirmación falsa. La persistencia real deberá probarse en una implementación.

## Cobertura del prototipo

El prototipo de Figma podrá representar la navegación de los perfiles, las selecciones de curso, estudiante y período, las marcas de asistencia, las confirmaciones y los mensajes alternativos. Las cuentas y los datos deberán ser ficticios. La selección de un rol o la navegación entre pantallas solo simula la experiencia: no demuestra autenticación, autorización, persistencia, auditoría o sincronización reales.

Los criterios que exigen persistencia, rechazo de solicitudes directas, validación de vínculos o cierre efectivo de sesión requerirán posteriormente una implementación y pruebas. En esta entrega se podrán revisar sus reglas mediante escenarios y pantallas; no se declararán esas comprobaciones técnicas como ejecutadas.

No se incluyen notificaciones automáticas, registro sin conexión, biometría, gestión de calificaciones, matrícula completa, carga de documentos médicos, envío de justificaciones por apoderados ni exportaciones oficiales. Incorporarlas requerirá nuevos requerimientos y acuerdo sobre el alcance.
