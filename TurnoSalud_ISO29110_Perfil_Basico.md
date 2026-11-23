# Ejercicio · El caso «TurnoSalud»
### Aplicación de la norma ISO/IEC 29110 (Perfil Básico) 

| Campo | Valor |
|---|---|
| Proyecto | TurnoSalud: aplicación web de agendamiento de turnos |
| Cliente (CL) | Clínica privada, Sangolquí (nombre por confirmar) |
| Proveedor | VSE de Sangolquí |
| Equipo | Domenica Villagómez · Saray Canarte · Danny Ayuquina · Jeancarlo Santi|
| Norma de referencia | ISO/IEC 29110-4-1 (requisitos del perfil) e ISO/IEC 29110-5-1-2 (guía de gestión e ingeniería, Perfil Básico) |
| Versión del documento | 1.0 |
| Fecha | 18/11/2026 |

## Datos de entrada del caso

| Variable | Valor del enunciado |
|---|---|
| Tamaño de la VSE | 6 personas (1 gestora, 1 líder técnico, 1 analista-diseñadora, 2 programadores, 1 responsable de pruebas) |
| Cliente | Clínica privada que necesita una app web de agendamiento de turnos |
| Plazo | 12 semanas |
| Presupuesto | US$ 18 000 |
| Proyectos simultáneos | 1 (solo ejecuta este proyecto en este periodo) |
| Criticidad | El producto **no** es crítico para la seguridad |

# 1. Elección del perfil

## 1.1 Variables

| Símbolo | Significado | Valor |
|---|---|---|
| N | Número de personas en el proyecto | 6 (caso) / 4 (nuestro equipo) |
| S | Duración en semanas | 12 |
| D | Duración en meses = S / 4,33 | 12 / 4,33 = **2,77 meses** |
| f | Dedicación promedio (fracción de jornada completa) | 1,00 (caso) / 0,90 (nuestro equipo, ver §3.8) |
| E | Esfuerzo en personas-mes = N · D · f | se calcula abajo |
| — | Equivalencia usada: 1 persona-mes = 4,33 semanas × 40 h | **173,2 h** |
| P | Proyectos ejecutados en paralelo | 1 |
| C | Criticidad del software (0 = no crítico, 1 = crítico para la seguridad) | 0 |
| G | Objetivo de crecimiento y gestión de negocio (0 = no, 1 = sí) | 0 (el caso no lo menciona) |

## 1.2 Ecuación de decisión

**Condición previa (¿aplica la ISO/IEC 29110 al grupo genérico?)**

$$
\text{Aplica} \iff (N \le 25) \;\land\; (C = 0)
$$

**Función de selección del perfil**

$$
\text{Perfil}(E, P, G) =
\begin{cases}
\text{Entrada} & \text{si } E \le 6 \text{ personas-mes} \\
\text{Básico} & \text{si } E > 6 \;\land\; P = 1 \\
\text{Intermedio} & \text{si } P > 1 \;\land\; G = 0 \\
\text{Avanzado} & \text{si } P > 1 \;\land\; G = 1
\end{cases}
$$

## 1.3 Sustitución de valores

**Condición previa**

- N = 6 ≤ 25 ✔ (con 4 personas también ✔)
- C = 0, el producto no es crítico para la seguridad ✔
- **Aplica la ISO/IEC 29110, grupo de perfiles genéricos.**

**Esfuerzo**

| Escenario | Cálculo | E (personas-mes) | ¿E ≤ 6? |
|---|---|---|---|
| Caso original (6 personas) | E = 6 × 2,77 × 1,00 | **16,6** | No (2,77 veces el límite) |
| Nuestro equipo (4 personas) | E = 4 × 2,77 × 0,90 = 1 728 h ÷ 173,2 h (ver §3.8) | **10,0** | No (1,7 veces el límite) |

**Proyectos en paralelo:** P = 1, así que se descartan Intermedio y Avanzado.

**Resultado:**

$$
E_{caso} = 16{,}6 > 6 \;\;\land\;\; E_{equipo} = 10{,}0 > 6 \;\;\land\;\; P = 1 \;\Rightarrow\; \boxed{\text{Perfil Básico}}
$$

## 1.4 Análisis de sensibilidad (¿cuándo cambiaría el perfil?)

- **Para que fuera Entrada** (E ≤ 6), el proyecto tendría que durar como máximo:
  - con 6 personas: D ≤ 6 / (6 × 1,00) = 1 mes ≈ **4,3 semanas**
  - con 4 personas: D ≤ 6 / (4 × 0,90) = 1,67 meses ≈ **7,2 semanas**

  Con 12 semanas ninguno de los dos escenarios entra.
- **Para que fuera Intermedio**, la VSE tendría que tomar un segundo proyecto en paralelo (P ≥ 2), y el enunciado lo descarta de forma explícita.
- **Para que fuera Avanzado**, además de P ≥ 2 haría falta un objetivo de crecimiento como empresa (G = 1). No hay evidencia de eso.

## 1.5 Matriz de verificación

| Criterio | Entrada | **Básico** | Intermedio | Avanzado |
|---|:---:|:---:|:---:|:---:|
| N ≤ 25 y software no crítico | ✔ | ✔ | ✔ | ✔ |
| Esfuerzo E ≤ 6 personas-mes | ✘ | n/a | n/a | n/a |
| Un solo proyecto (P = 1) | ✔ | ✔ | ✘ | ✘ |
| Gestión de varios proyectos | n/a | n/a | ✘ | ✘ |
| Objetivo de crecimiento empresarial | n/a | n/a | n/a | ✘ |
| **¿Cumple todos?** | ✘ | **✔** | ✘ | ✘ |

### Decisión: **Perfil Básico** (ISO/IEC 29110-4-1 / 29110-5-1-2)

Con este perfil se aplican dos procesos:

- **Gestión del Proyecto (GP):** GP.1 Planificación · GP.2 Ejecución del plan · GP.3 Evaluación y control · GP.4 Cierre
- **Implementación de Software (IS):** IS.1 Inicio · IS.2 Requisitos · IS.3 Arquitectura y diseño · IS.4 Construcción · IS.5 Integración y pruebas · IS.6 Entrega

# 2. Plan del Proyecto (salida de GP.1)

## 2.1 Tareas de GP.1 Planificación y quién las hace

| Tarea | Descripción | Responsable | Participa | Producto |
|---|---|---|---|---|
| GP.1.1 | Revisar el Enunciado del Trabajo | Domenica (GP) | Danny (LT), CL | Enunciado revisado (§2) |
| GP.1.2 | Definir con el cliente las instrucciones de entrega | Domenica (GP) | CL | §3.5 |
| GP.1.3 | Identificar las tareas, incluidas verificación, validación y revisiones | Domenica (GP) | Danny (LT), ET | §3.7 |
| GP.1.4 | Estimar la duración | Domenica (GP) | Danny (LT) | §3.7 |
| GP.1.5 | Identificar los recursos | Domenica (GP) | Danny (LT) | §3.9 |
| GP.1.6 | Definir la composición del equipo | Domenica (GP) | — | §3.6 |
| GP.1.7 | Asignar fechas de inicio y fin (calendario) | Domenica (GP) | Danny (LT) | §3.7 |
| GP.1.8 | Estimar esfuerzo y costo | Domenica (GP) | Danny (LT) | §3.8 |
| GP.1.9 | Identificar y documentar los riesgos | Domenica (GP) | ET | §3.10 |
| GP.1.10 | Definir la estrategia de control de versiones | Danny (LT) | Domenica (GP) | §3.11 |
| GP.1.11–12 | Generar el Plan del Proyecto con producto, alcance, objetivos y entregables | Domenica (GP) | — | Este documento |
| GP.1.13 | Verificar el Plan del Proyecto | Danny (LT) | Domenica (GP) | Lista de verificación §3.13 |
| GP.1.14 | Revisar y aceptar el plan con el cliente | Domenica (GP) | CL | Acta de reunión §3.14 |
| GP.1.15 | Crear el repositorio del proyecto | Danny (LT) | Domenica (GP) | Repositorio §3.12 |

## 2.2 Descripción del producto

Ver el propósito, la descripción y los requisitos generales en §2.1.

*Arquitectura preliminar* (la confirma el LT en IS.3): cliente web SPA (React), API REST (Node.js con Express), base de datos PostgreSQL, servicio de correo transaccional y despliegue en un servidor en la nube con HTTPS.

## 2.3 Alcance y objetivos

Ver §2.1. Cualquier cambio de alcance se canaliza con una *Solicitud de Cambio*, que se registra, se analiza su impacto en plazo, costo y documentación, se aprueba o rechaza con el cliente y se gestiona en GP.3.

## 2.4 Entregables

| # | Entregable | Destinatario | Semana |
|---|---|---|---|
| E1 | Plan del Proyecto aprobado | CL | 1 |
| E2 | Especificación de Requisitos validada, con prototipo de interfaz | CL | 3 |
| E3 | Diseño de software (arquitectura y modelo de datos) | Interno / CL (informativo) | 4 |
| E4 | Incrementos funcionales 1, 2 y 3, con demostración | CL | 6, 8, 9 |
| E5 | Reporte de pruebas (casos ejecutados y resultados) | CL | 11 |
| E6 | Software en producción (código fuente y ejecutable desplegado) | CL | 12 |
| E7 | Manual de usuario (paciente, recepción y médico) | CL | 12 |
| E8 | Manual de operación (instalación, respaldo y restauración) | CL | 12 |
| E9 | Documentación de mantenimiento | CL | 12 |
| E10 | Acta de aceptación y cierre | CL | 12 |

## 2.5 Instrucciones de entrega (GP.1.2)

| Entregable | Formato | Medio | Criterio de aceptación |
|---|---|---|---|
| Documentos (E1, E2, E3, E5, E7–E9) | PDF y fuente en Markdown | Carpeta compartida con el cliente y repositorio /docs | Revisados y firmados en acta por el representante del CL |
| Incrementos (E4) | Versión desplegada en el ambiente de pruebas | URL de staging | Demostración aprobada en la revisión del incremento |
| Software (E6) | Código fuente con etiqueta v1.0.0 y aplicación desplegada | Repositorio privado transferido al CL y URL de producción | 100 % de los casos de aceptación Must aprobados y ningún defecto crítico abierto |
| Credenciales | Documento cifrado | Entrega en persona | Recepción confirmada en acta |

## 2.6 Composición del equipo y roles (GP.1.6)

| Integrante | Rol 1 | Rol 2 | Equivalente en el caso | Responsabilidades principales |
|---|---|---|---|---|
| *Domenica* | *Gestora del Proyecto (GP)* | — | Gestora | Planificar, dar seguimiento, controlar riesgos y cambios, ser el enlace con el cliente, redactar actas e informes de avance, y hacer el cierre |
| *Saray* | *Analista (AN)* | *Diseñadora (DIS)* | Analista-diseñadora | Levantar y especificar requisitos, hacer el prototipo de interfaz y el diseño detallado, redactar los manuales de usuario y verificar requisitos |
| *Danny* | *Líder Técnico (LT)* | *Programador (PR)* | Líder técnico + programador 1 | Definir la arquitectura, verificar el plan y el diseño, gestionar el repositorio y el control de versiones, programar el backend e integrar |
| *Jeancarlo* | *Programador (PR)* | *Responsable de pruebas* (dentro del ET) | Programador 2 + responsable de pruebas | Programar el frontend, escribir casos y procedimientos de prueba, ejecutar las pruebas y redactar el reporte de pruebas |
| Representante de la clínica | *Cliente (CL)* | — | Cliente | Validar requisitos, aprobar el plan y los cambios, y aceptar los entregables |

*Equipo de Trabajo (ET):* Domenica, Saray, Danny y Jeancarlo.

*Control para mantener la independencia de las pruebas:* Jeancarlo prueba los módulos que programa Danny, y Saray verifica contra los requisitos los módulos de Jeancarlo. Así nadie aprueba su propio código.

*Consolidación de 6 a 4 personas:* el segundo programador del caso se absorbe en Danny (LT + PR), y el responsable de pruebas en Jeancarlo (PR + pruebas). Domenica tiene un solo rol porque la gestión, los registros que exige la 29110 y la relación con el cliente ocupan su dedicación (60 %).

## 2.7 Tareas, duración y calendario (GP.1.3, GP.1.4, GP.1.7)

*Fecha de inicio supuesta:* lunes 23/11/2026. *Fin:* viernes 12/02/2027.

| Sem. | Fechas | Proceso / actividad | Responsable | Hito |
|---|---|---|---|---|
| 1 | 23/11 – 27/11 | GP.1 Planificación · IS.1 Inicio (revisar el plan con el equipo, crear repositorio y entornos) | Domenica / Danny | *H1: Plan aprobado* |
| 2 | 30/11 – 04/12 | IS.2 Requisitos: entrevistas, especificación, prototipo de interfaz | Saray | — |
| 3 | 07/12 – 11/12 | IS.2 Validación de requisitos con el cliente · borrador de casos de prueba | Saray / Jeancarlo | *H2: Requisitos validados* |
| 4 | 14/12 – 18/12 | IS.3 Arquitectura y diseño detallado · casos y procedimientos de prueba | Danny / Saray / Jeancarlo | *H3: Diseño verificado* |
| 5–6 | 21/12 – 01/01 | IS.4 Incremento 1: autenticación, pacientes, médicos, especialidades y horarios | Danny / Jeancarlo | *H4a: Demo Inc. 1* |
| 7–8 | 04/01 – 15/01 | IS.4 Incremento 2: reservar, cancelar y reprogramar turnos, agenda del médico | Danny / Jeancarlo | *H4b: Demo Inc. 2* |
| 9 | 18/01 – 22/01 | IS.4 Incremento 3: recordatorios, agendamiento por recepción, reportes | Danny / Jeancarlo | *H4c: Demo Inc. 3* |
| 10 | 25/01 – 29/01 | IS.5 Integración y pruebas del sistema · corrección de defectos | Jeancarlo / Danny | — |
| 11 | 01/02 – 05/02 | IS.5 Pruebas de aceptación con el cliente · manuales | Jeancarlo / Saray / CL | *H5: Aceptación* |
| 12 | 08/02 – 12/02 | IS.6 Entrega (despliegue, capacitación) · GP.4 Cierre | Domenica / Danny | *H6: Entrega y cierre* |
| 1–12 | Todo el proyecto | GP.2 Ejecución (reuniones semanales, reporte de avance, respaldo) · GP.3 Evaluación y control (avance frente al plan, cambios, riesgos) | Domenica | Reporte semanal |

| Práctica | Frecuencia | Relación con la ISO/IEC 29110 |
|---|---|---|
| Planificación del incremento | Al inicio de cada incremento | GP.1 / GP.2 |
| Reunión diaria (15 min) | Diaria | GP.2 seguimiento |
| Revisión del incremento con el CL | Semanas 6, 8 y 9 | GP.2 revisión con el cliente · acta |
| Retrospectiva | Al cierre de cada incremento | GP.3 acciones correctivas |
| Reporte de avance | Semanal | GP.2 / GP.3 |

## 2.8 Esfuerzo y costo estimados (GP.1.8)

*Esfuerzo por persona*

| Integrante | Dedicación | Horas/semana | Horas totales (12 sem.) |
|---|---|---|---|
| Domenica | 60 % | 24 | 288 |
| Saray | 100 % | 40 | 480 |
| Danny | 100 % | 40 | 480 |
| Jeancarlo | 100 % | 40 | 480 |
| *Total* | *90 % promedio* | — | *1 728 h ≈ 10,0 personas-mes* |

*Esfuerzo por proceso*

| Proceso | Horas | % |
|---|---|---|
| GP (planificación, seguimiento, control y cierre) | 288 | 16,7 % |
| IS.1 Inicio | 40 | 2,3 % |
| IS.2 Requisitos | 200 | 11,6 % |
| IS.3 Arquitectura y diseño | 200 | 11,6 % |
| IS.4 Construcción | 640 | 37,0 % |
| IS.5 Integración y pruebas | 280 | 16,2 % |
| IS.6 Entrega | 80 | 4,6 % |
| *Total* | *1 728* | *100 %* |

*Presupuesto* (tarifa referencial uniforme: US$ 8,75/h)

| Rubro | Detalle | US$ | % |
|---|---|---:|---:|
| Personal | 1 728 h × 8,75 | 15 120 | 84,0 % |
| Infraestructura y herramientas | Servidor y base de datos en la nube por 6 meses (300), dominio (30), correo transaccional (150), planes de herramientas de gestión y diseño (220) | 700 | 3,9 % |
| Capacitación | Curso corto de ISO/IEC 29110 y protección de datos personales | 200 | 1,1 % |
| Reserva de contingencia | Para riesgos y cambios aprobados | 1 980 | 11,0 % |
| *Total* | | *18 000* | *100 %* |

*Comprobación:* 15 120 + 700 + 200 + 1 980 = *US$ 18 000*, así que el plan está dentro del presupuesto.

*Indicador de retrabajo* (se mide semanalmente en GP.3):

$$
\%\,\text{Retrabajo} = \frac{\text{Horas de retrabajo}}{\text{Horas totales registradas}} \times 100 \qquad \text{Meta: } \le 15\,\%
$$

## 2.9 Recursos (GP.1.5)

| Tipo | Recurso |
|---|---|
| Humanos | 4 integrantes (§3.6) y el representante del cliente |
| Equipos | Laptops propias del equipo, un celular Android y uno iOS para pruebas responsivas |
| Herramientas | Git + GitHub (repositorio privado), Trello o Jira (tareas), Figma (prototipos), VS Code, Postman (API), Google Drive (respaldo y documentos compartidos) |
| Infraestructura | Servidor en la nube con ambientes de staging y producción, PostgreSQL, certificado HTTPS (Let's Encrypt) |
| Capacitación | ISO/IEC 29110 Perfil Básico; protección de datos personales en salud |

## 2.10 Riesgos (GP.1.9)

Escala: Probabilidad (P) e Impacto (I) de 1 (bajo) a 3 (alto). *Exposición = P × I* (≥ 6 es alta).

| ID | Riesgo | P | I | Exp. | Respuesta | Dueño |
|---|---|:-:|:-:|:-:|---|---|
| R1 | Requisitos que cambian o están mal entendidos | 3 | 3 | *9* | Prototipo temprano, validación formal en la semana 3, solicitudes de cambio por GP.3 | Saray |
| R2 | Sobrecarga del equipo reducido (4 personas en lugar de 6) | 3 | 3 | *9* | Priorización MoSCoW (los Could se sacrifican primero) y seguimiento semanal de horas | Domenica |
| R3 | Feriados (25/12, 01/01, Carnaval 8–9/02) reducen la capacidad | 3 | 2 | *6* | Versión candidata en la semana 11 y semana 12 solo para entrega | Domenica |
| R4 | Incumplir la protección de datos de salud | 2 | 3 | *6* | Consentimiento informado, cifrado, roles y revisión de seguridad en IS.5 | Danny |
| R5 | El cliente no está disponible para validar | 2 | 3 | *6* | Calendario de reuniones acordado en el acta de aprobación del plan | Domenica |
| R6 | Fallas o costo del servicio de notificaciones | 2 | 2 | 4 | Usar correo como canal base y dejar SMS/WhatsApp como opcional | Danny |
| R7 | Poca experiencia con el stack tecnológico | 2 | 2 | 4 | Capacitación en la semana 1 y pruebas de concepto en IS.3 | Danny |
| R8 | Pérdida de código o documentos | 1 | 3 | 3 | Repositorio remoto y respaldo semanal (§3.11) | Danny |

## 2.11 Estrategia de control de versiones (GP.1.10)

| Aspecto | Definición |
|---|---|
| Herramienta | Git con repositorio privado en GitHub |
| Ramas | main (producción) · develop (integración) · feature/<id-requisito> · hotfix/<id> |
| Integración | Pull request con revisión obligatoria de otro integrante antes de unir a develop |
| Versiones | Versionado semántico: v0.1 (Inc. 1), v0.2 (Inc. 2), v0.3 (Inc. 3), v1.0.0-rc (sem. 11), v1.0.0 (entrega) |
| Líneas base | LB1 Plan aprobado · LB2 Requisitos validados · LB3 Diseño verificado · LB4 Producto aceptado |
| Nombres de documentos | TS-<TIPO>-<NN>_v<X.Y>.md (por ejemplo, TS-PLAN-01_v1.0.md, TS-ACTA-03_v1.0.md) |
| Respaldo | Cada viernes se exporta el repositorio a Google Drive y el GP lo registra en el reporte de avance |
| Acceso | Danny (LT): administrador · ET: escritura · CL: lectura de /docs/entregables |

## 2.12 Estructura del repositorio (GP.1.15)

```
turnosalud/
├── docs/
│   ├── gestion/          # Plan, reportes de avance, actas, solicitudes de cambio, riesgos
│   ├── requisitos/       # Especificación de requisitos, prototipos
│   ├── diseno/           # Arquitectura, modelo de datos
│   ├── pruebas/          # Casos y procedimientos de prueba, reporte de pruebas
│   └── entregables/      # Manuales y versiones aprobadas para el cliente
├── frontend/
├── backend/
├── db/                   # Scripts y migraciones
└── README.md
```
# 3. Validar requisitos con el cliente (IS.2)

## 3.1 Cómo se trabajó la actividad
 
La actividad IS.2 Análisis de requisitos convierte los requisitos generales del Enunciado del Trabajo en una **Especificación de Requisitos** concreta, verificable y aprobada por el cliente. La norma distingue dos revisiones que a veces se confunden. La **verificación** la hace el propio equipo y responde a la pregunta "¿está bien escrito el requisito?", es decir, si es claro, no se contradice con otros y se puede probar. La **validación** la hace el cliente y responde a "¿es esto lo que necesitamos?". Las dos dejan evidencia: el Resultado de verificación y el Resultado de validación.
 
Durante la semana 2, Saray (AN) será la encargada de entrevistar a la administradora y a una recepcionista de la clínica, revisar cómo se lleva hoy la agenda en papel y en una hoja de cálculo, y redactar la primera versión de la especificación junto con un prototipo navegable en Figma. Hecha la verificación interna, se presenta el prototipo al cliente en la semana 3 debido a que ver las pantallas resulta mucho más útil que leer una lista de requisitos, en esta fase el cliente es capaz de detectar en minutos detalles que en el documento habían pasado desapercibidos.

El orden de las tareas siguió la guía del Perfil Básico:
 
1. Domenica (GP) asignó las tareas de requisitos según los roles del plan.
2. Saray (AN) documentó la Especificación de Requisitos a partir del Enunciado del Trabajo y de las entrevistas.
3. Danny (LT) y Jeancarlo (responsable de pruebas) la **verificaron**. Jeancarlo revisó en particular que cada requisito pudiera convertirse en un caso de prueba.
4. Saray y Domenica la **validaron** con el cliente en una reunión con el prototipo.
5. Saray redactó el borrador del manual de usuario a partir de las pantallas validadas.
6. Danny incorporó la especificación aprobada al repositorio como **línea base LB2**.

## 3.2 Especificación de Requisitos (v1.0, validada)
 
Cada requisito funcional tiene un identificador único, su origen en el Enunciado del Trabajo (trazabilidad) y un criterio de aceptación que después se transforma en caso de prueba. La tabla ya incluye los ajustes que pidió el cliente en la validación (§4.4).
 
| ID | Requisito funcional | Origen | Prioridad | Criterio de aceptación |
|---|---|---|---|---|
| RF-01 | Registrar paciente con cédula, nombres, correo, teléfono, fecha de nacimiento y aceptación del consentimiento de datos | RG-01 | Must | No acepta cédulas duplicadas ni inválidas (valida el dígito verificador) y no guarda nada sin consentimiento |
| RF-02 | Iniciar sesión y recuperar la contraseña por correo | RG-01 | Must | El enlace de recuperación caduca en 30 minutos |
| RF-03 | Consultar horarios libres por especialidad, médico y fecha | RG-02 | Must | Solo muestra franjas libres de los próximos 30 días |
| RF-04 | Reservar un turno | RG-03 | Must | Confirmación en pantalla y por correo; un paciente no puede tener dos turnos en la misma franja |
| RF-05 | Cancelar un turno | RG-04 | Must | Permitido hasta **12 h** antes; la franja vuelve a quedar libre |
| RF-06 | Reprogramar un turno | RG-04 | Must | Misma regla de 12 h; el turno anterior se libera |
| RF-07 | Administrar médicos y especialidades | RG-05 | Must | Crear, editar y desactivar sin borrar el historial de turnos |
| RF-08 | Configurar horarios, **duración de la cita por especialidad** y bloqueos | RG-05 | Must | Un bloqueo oculta las franjas afectadas a los pacientes |
| RF-09 | Agenda diaria del médico, con marca de **"atendido" o "no asistió"** | RG-06 | Must | El médico ve solo su agenda; recepción ve todas |
| RF-10 | Recepción agenda en nombre de un paciente | RG-07 | Should | Puede registrar un paciente nuevo con datos mínimos |
| RF-11 | Recordatorio automático por correo 24 h antes | RG-08 | Should | El envío queda registrado; si falla, se reintenta |
| RF-12 | Reportes de turnos y ausentismo con **exportación a CSV** | RG-09 | Could | Filtra por rango de fechas, médico y especialidad |
 
| ID | Requisito no funcional | Criterio medible |
|---|---|---|
| RNF-01 | Usabilidad y diseño responsivo | Funciona de 360 px (celular) a escritorio en Chrome, Edge, Firefox y Safari |
| RNF-02 | Seguridad | HTTPS obligatorio, contraseñas con hash (bcrypt), acceso por rol: paciente, recepción, médico y administrador |
| RNF-03 | Protección de datos personales | Consentimiento explícito; no se guarda información clínica, solo datos de contacto y de la cita |
| RNF-04 | Rendimiento | Consulta y reserva en menos de 3 s con 50 usuarios simultáneos |
| RNF-05 | Respaldo | Copia diaria automática de la base de datos, con restauración probada |
