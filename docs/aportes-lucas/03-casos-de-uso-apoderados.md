# Casos de uso de apoderados

## Propósito y notación

Estos casos describen objetivos de consulta del apoderado y la respuesta esperada del sistema. Los casos de acceso y salida son comunes a otros perfiles, pero se incluyen desde la perspectiva del apoderado para documentar su recorrido completo. La selección de un hijo establece el contexto de las consultas de historial, detalle y resumen; no se utiliza aquí una relación UML «include» o «extend» para imponer un diseño al diagrama principal.

La estructura se apoya en el ejemplo de especificación presentado en la asignatura, que distingue actor, condiciones previas, escenario y condiciones posteriores (Matus, 2026b, diapositiva 32). Se agregan flujos alternativos para evitar que una consulta vacía, un vínculo no autorizado o una falla se interpreten como asistencia registrada.

## CU-AP-01 Acceder a la consulta de asistencia

**Objetivo:** Ingresar al espacio de consulta para acceder a la información habilitada del apoderado.

**Actor y participantes:** Apoderado como actor principal. El sistema verifica las credenciales y habilita el espacio del perfil.

**Disparador:** El apoderado elige iniciar sesión.

### Precondiciones

- Existe una cuenta habilitada de apoderado.
- El servicio de acceso está disponible; para la demostración se utilizará una cuenta ficticia.

### Flujo principal de eventos

1. El apoderado abre la pantalla de acceso.
2. El sistema solicita sus credenciales.
3. El apoderado las ingresa y confirma la solicitud.
4. El sistema valida las credenciales y determina el perfil de la cuenta.
5. El sistema abre el espacio de apoderado y ofrece la consulta de los hijos vinculados.

### Flujos alternativos y excepciones

**A1 Credenciales inválidas, paso 4.** El sistema informa que no es posible iniciar sesión, sin mostrar datos de asistencia, y permite reintentar.

**A2 Cuenta no habilitada, paso 4.** El sistema no abre la sesión e indica que debe utilizar el canal de soporte del establecimiento.

**A3 Sin hijos vinculados, paso 5.** Se abre el espacio de apoderado, pero se informa que no tiene estudiantes habilitados y no se muestra información de otros alumnos.

### Postcondiciones

- La sesión corresponde a la cuenta y al perfil de apoderado autenticados.
- El acceso al espacio no habilita por sí solo la consulta de estudiantes no vinculados.

**Si el objetivo no se completa:** No se abre una sesión ante credenciales inválidas o cuenta no habilitada y no se divulgan datos de asistencia.

**Requerimientos relacionados:** RF-01, RF-16, RF-22.

**Reglas relacionadas:** RN-01, RN-09.

**Pantallas propuestas para el equipo de Figma:** AP-01 Acceso; AP-02 Hijos vinculados.

### Escenarios de aceptación propuestos

- Cuenta ficticia válida: muestra el espacio de apoderado.
- Credenciales inválidas: no abre el espacio.
- Cuenta sin vínculos: muestra un mensaje sin datos de terceros.

## CU-AP-02 Seleccionar un hijo vinculado

**Objetivo:** Elegir el estudiante al que corresponderán las consultas.

**Actor y participantes:** Apoderado como actor principal.

**Disparador:** El apoderado abre la lista de hijos vinculados.

### Precondiciones

- El apoderado ha iniciado sesión.
- El establecimiento mantiene los vínculos de consulta validados; puede haber cero, uno o varios.

### Flujo principal de eventos

1. El sistema obtiene los estudiantes vinculados a la cuenta.
2. El sistema muestra únicamente los nombres de esos estudiantes y el curso que corresponda al contexto de consulta.
3. El apoderado selecciona a uno de sus hijos.
4. El sistema verifica nuevamente que el vínculo autoriza el acceso.
5. El sistema abre el espacio del estudiante e identifica de manera visible al hijo seleccionado.

### Flujos alternativos y excepciones

**A1 Sin vínculos, paso 1.** El sistema informa que no hay estudiantes habilitados y no ofrece acceso a nóminas o buscadores generales de alumnos.

**A2 Vínculo ya no autorizado, paso 4.** El sistema rechaza la selección y actualiza la lista sin mostrar datos de asistencia del estudiante.

**A3 Cambio de hijo, después del paso 5.** El apoderado vuelve a su lista, elige otro hijo autorizado y el sistema reemplaza el contexto y los resultados anteriores.

### Postcondiciones

- Queda seleccionado un hijo autorizado y visible en el encabezado.
- Las consultas posteriores quedan delimitadas a ese estudiante.

**Si el objetivo no se completa:** No se selecciona ni se revela asistencia de un estudiante no autorizado.

**Requerimientos relacionados:** RF-16, RF-22.

**Reglas relacionadas:** RN-01, RN-09.

**Pantallas propuestas para el equipo de Figma:** AP-02 Hijos vinculados; AP-03 Historial del hijo.

### Escenarios de aceptación propuestos

- Cuenta con dos hijos: permite elegir ambos de forma separada.
- Cuenta con un hijo: no muestra alumnos ajenos.
- Vínculo retirado: impide continuar con ese estudiante.

## CU-AP-03 Consultar asistencia por período

**Objetivo:** Revisar fechas y estados de asistencia de un hijo durante un intervalo.

**Actor y participantes:** Apoderado como actor principal.

**Disparador:** El apoderado solicita consultar el historial del hijo seleccionado.

### Precondiciones

- Existe una sesión de apoderado.
- Hay un hijo seleccionado con vínculo vigente.
- El calendario y los datos de matrícula necesarios están disponibles como datos de base.

### Flujo principal de eventos

1. El sistema muestra el nombre del hijo y solicita las fechas inicial y final.
2. El apoderado ingresa el intervalo y solicita la consulta.
3. El sistema valida el orden de las fechas y la autorización sobre el estudiante.
4. El sistema obtiene los registros que corresponden a ese hijo y al período.
5. El sistema muestra las fechas y sus estados, diferenciando presente, ausente y ausencia justificada.
6. El sistema distingue las jornadas sin registro cuando corresponda, sin convertirlas en ausencias.

### Flujos alternativos y excepciones

**A1 Intervalo inválido, paso 3.** El sistema indica que la fecha inicial no puede superar a la final y permite corregir el intervalo sin consultar otro período.

**A2 Período sin registros, paso 4.** El sistema informa «Sin registros para el período». No atribuye ausencias ni presenta información anterior como si fuera el resultado actual.

**A3 Autorización no vigente, paso 3.** El sistema rechaza la consulta sin devolver registros.

**A4 Falla de consulta, paso 4.** El sistema informa que no pudo obtener los datos y ofrece reintentar. Una falla no se presenta como una consulta vacía exitosa.

### Postcondiciones

- Se muestra únicamente el historial del hijo y período autorizados.
- Los estados confirmados y la falta de registro se distinguen.

**Si el objetivo no se completa:** No se muestran datos de terceros ni resultados incorrectos ante un intervalo inválido, falta de autorización o falla de consulta.

**Requerimientos relacionados:** RF-17, RF-19, RF-21, RF-22.

**Reglas relacionadas:** RN-01, RN-03, RN-04, RN-07, RN-09.

**Pantallas propuestas para el equipo de Figma:** AP-03 Historial del hijo; AP-03A Intervalo inválido; AP-03B Sin registros; AP-03C Error de consulta.

### Escenarios de aceptación propuestos

- Período con estados mixtos: muestra los registros del intervalo y estudiante correctos.
- Fechas invertidas: solicita corrección.
- Período vacío: informa falta de registros, sin asignar ausencias.

## CU-AP-04 Consultar el detalle de una fecha

**Objetivo:** Comprender la asistencia registrada de su hijo en una fecha determinada.

**Actor y participantes:** Apoderado como actor principal.

**Disparador:** El apoderado elige una fecha desde el historial.

### Precondiciones

- El apoderado mantiene sesión y vínculo autorizado.
- Existe un hijo seleccionado y una fecha consultable dentro de su contexto de matrícula.

### Flujo principal de eventos

1. El apoderado selecciona una fecha.
2. El sistema valida el permiso de consulta sobre el estudiante y recupera el registro de esa fecha.
3. El sistema muestra nombre del hijo, fecha y estado de asistencia.
4. Si el estado es ausencia justificada, el sistema lo identifica expresamente.
5. El apoderado vuelve al historial conservando la selección de hijo y período.

### Flujos alternativos y excepciones

**A1 Fecha sin registro, paso 2.** El sistema informa «Sin registro para esta fecha», en lugar de mostrar una ausencia.

**A2 Dato regularizado, paso 2.** Se muestra el estado vigente; el motivo administrativo y el historial de cambios no se exponen al apoderado.

**A3 Estudiante no autorizado, paso 2.** El sistema rechaza la consulta sin entregar la identidad ni la asistencia del recurso solicitado.

**A4 Fecha no lectiva, paso 2.** Si el calendario de base la identifica como no lectiva, se informa esa condición y no se inventa un registro.

### Postcondiciones

- Se muestra el estado vigente de la fecha seleccionada sin datos administrativos reservados.
- La consulta no modifica la asistencia.

**Si el objetivo no se completa:** Una consulta no autorizada no revela información y una fecha sin registro no genera una ausencia.

**Requerimientos relacionados:** RF-18, RF-19, RF-21, RF-22.

**Reglas relacionadas:** RN-01, RN-03, RN-04, RN-05, RN-09.

**Pantallas propuestas para el equipo de Figma:** AP-04 Detalle de asistencia; AP-04A Sin registro.

### Escenarios de aceptación propuestos

- Ausencia justificada: se muestra su estado sin motivo interno.
- Fecha sin registro: no se muestra ausente.
- Acceso no autorizado: se rechaza sin revelar datos.

## CU-AP-05 Consultar el resumen de asistencia

**Objetivo:** Conocer los totales de asistencia del hijo seleccionado en un período.

**Actor y participantes:** Apoderado como actor principal.

**Disparador:** El apoderado abre la opción de resumen.

### Precondiciones

- Existe sesión y vínculo vigente con el hijo seleccionado.
- El intervalo tiene fecha inicial no posterior a la final.

### Flujo principal de eventos

1. El apoderado selecciona el hijo autorizado y el período.
2. El sistema valida la autorización y el intervalo.
3. El sistema obtiene los registros confirmados de ese alcance.
4. El sistema agrupa cada registro en una sola categoría: presente, ausente o ausencia justificada.
5. El sistema muestra los totales e identifica aparte las jornadas sin registro cuando corresponda.
6. El apoderado puede volver al historial para revisar las fechas que explican los totales.

### Flujos alternativos y excepciones

**A1 Sin registros confirmados, paso 3.** El sistema informa que no hay registros para el período y no presenta un porcentaje o conclusión de asistencia inferido de esa falta de datos.

**A2 Cambio de período o hijo, paso 1.** Se recalculan los totales con la nueva selección; no se mantienen los totales anteriores como si correspondieran al nuevo contexto.

**A3 Intervalo o autorización inválidos, paso 2.** Se rechaza la consulta y se indica la acción aplicable, sin devolver datos de otro estudiante.

### Postcondiciones

- Cada total corresponde al hijo y período seleccionados.
- La suma de presentes, ausentes y justificadas coincide con el número de registros confirmados; los faltantes quedan separados.

**Si el objetivo no se completa:** No se generan totales basados en un hijo no autorizado ni se interpreta la falta de registros como asistencia o ausencia.

**Requerimientos relacionados:** RF-20, RF-21, RF-22.

**Reglas relacionadas:** RN-01, RN-04, RN-07, RN-08, RN-09.

**Pantallas propuestas para el equipo de Figma:** AP-05 Resumen por período.

### Escenarios de aceptación propuestos

- Datos de prueba: 6 presentes, 2 ausentes y 1 justificada producen totales 6, 2 y 1.
- Un día sin registro se muestra separado y no eleva el total de ausentes.
- Cambio de hijo: los resultados se recalculan para el nuevo seleccionado.

## CU-AP-06 Cerrar la sesión de consulta

**Objetivo:** Finalizar el acceso a la información de asistencia desde el dispositivo utilizado.

**Actor y participantes:** Apoderado como actor principal.

**Disparador:** El apoderado elige cerrar sesión.

### Precondiciones

- Existe una sesión de apoderado iniciada.

### Flujo principal de eventos

1. El apoderado solicita cerrar sesión.
2. El sistema finaliza la sesión y retira el contexto del hijo seleccionado.
3. El sistema muestra la pantalla de acceso.
4. Una nueva consulta protegida requiere volver a iniciar sesión.

### Flujos alternativos y excepciones

**A1 Intento de volver mediante navegación anterior, después del paso 3.** El sistema no entrega información protegida sin una sesión válida.

**A2 Sesión ya finalizada, paso 1.** El sistema muestra la pantalla de acceso sin recuperar datos de asistencia.

### Postcondiciones

- La consulta protegida requiere una nueva autenticación.
- No queda abierto el espacio de consulta del hijo.

**Si el objetivo no se completa:** Si no puede completarse el cierre, se informa la falla sin afirmar que la sesión fue finalizada.

**Requerimientos relacionados:** RF-02, RF-22.

**Reglas relacionadas:** RN-01.

**Pantallas propuestas para el equipo de Figma:** AP-01 Acceso.

### Escenarios de aceptación propuestos

- Cerrar y volver a solicitar una vista protegida: requiere iniciar sesión.
- En Figma solo se comprueba la navegación de salida; el cierre real exige implementación.

## Trazabilidad para el diagrama y los mockups

| Caso de uso | Requerimientos funcionales | Vistas propuestas |
| --- | --- | --- |
| CU-AP-01 Acceder a la consulta de asistencia | RF-01, RF-16, RF-22 | AP-01 Acceso; AP-02 Hijos vinculados |
| CU-AP-02 Seleccionar un hijo vinculado | RF-16, RF-22 | AP-02 Hijos vinculados; AP-03 Historial del hijo |
| CU-AP-03 Consultar asistencia por período | RF-17, RF-19, RF-21, RF-22 | AP-03 Historial del hijo; AP-03A Intervalo inválido; AP-03B Sin registros; AP-03C Error de consulta |
| CU-AP-04 Consultar el detalle de una fecha | RF-18, RF-19, RF-21, RF-22 | AP-04 Detalle de asistencia; AP-04A Sin registro |
| CU-AP-05 Consultar el resumen de asistencia | RF-20, RF-21, RF-22 | AP-05 Resumen por período |
| CU-AP-06 Cerrar la sesión de consulta | RF-02, RF-22 | AP-01 Acceso |

Los identificadores de pantallas son propuestas de coordinación para los issues de mockups y prototipo. No describen pantallas existentes verificadas en Figma. Los criterios anteriores son escenarios por ejecutar; no son resultados de pruebas realizadas con usuarios.
