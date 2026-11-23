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
| f | Dedicación promedio (fracción de jornada completa) | 1,00 (caso) / 0,90 (nuestro equipo, ver §2.8) |
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
| Nuestro equipo (4 personas) | E = 4 × 2,77 × 0,90 = 1 728 h ÷ 173,2 h (ver §2.8) | **10,0** | No (1,7 veces el límite) |

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
| GP.1.1 | Revisar el Enunciado del Trabajo | Domenica (GP) | Danny (LT), CL | Enunciado del Trabajo revisado |
| GP.1.2 | Definir con el cliente las instrucciones de entrega | Domenica (GP) | CL | §2.5 |
| GP.1.3 | Identificar las tareas, incluidas verificación, validación y revisiones | Domenica (GP) | Danny (LT), ET | §2.7 |
| GP.1.4 | Estimar la duración | Domenica (GP) | Danny (LT) | §2.7 |
| GP.1.5 | Identificar los recursos | Domenica (GP) | Danny (LT) | §2.9 |
| GP.1.6 | Definir la composición del equipo | Domenica (GP) | — | §2.6 |
| GP.1.7 | Asignar fechas de inicio y fin (calendario) | Domenica (GP) | Danny (LT) | §2.7 |
| GP.1.8 | Estimar esfuerzo y costo | Domenica (GP) | Danny (LT) | §2.8 |
| GP.1.9 | Identificar y documentar los riesgos | Domenica (GP) | ET | §2.10 |
| GP.1.10 | Definir la estrategia de control de versiones | Danny (LT) | Domenica (GP) | §2.11 |
| GP.1.11–12 | Generar el Plan del Proyecto con producto, alcance, objetivos y entregables | Domenica (GP) | — | Este documento |
| GP.1.13 | Verificar el Plan del Proyecto | Danny (LT) | Domenica (GP) | Lista de verificación del plan |
| GP.1.14 | Revisar y aceptar el plan con el cliente | Domenica (GP) | CL | Acta de reunión |
| GP.1.15 | Crear el repositorio del proyecto | Danny (LT) | Domenica (GP) | Repositorio §2.12 |

## 2.2 Descripción del producto

El propósito, la descripción y los requisitos generales del producto se toman del Enunciado del Trabajo revisado (GP.1.1).

*Arquitectura preliminar* (la confirma el LT en IS.3): cliente web SPA (React), API REST (Node.js con Express), base de datos PostgreSQL, servicio de correo transaccional y despliegue en un servidor en la nube con HTTPS.

## 2.3 Alcance y objetivos

El alcance y los objetivos son los acordados en el Enunciado del Trabajo revisado (GP.1.1). Cualquier cambio de alcance se canaliza con una *Solicitud de Cambio*, que se registra, se analiza su impacto en plazo, costo y documentación, se aprueba o rechaza con el cliente y se gestiona en GP.3.

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
| Humanos | 4 integrantes (§2.6) y el representante del cliente |
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
| R8 | Pérdida de código o documentos | 1 | 3 | 3 | Repositorio remoto y respaldo semanal (§2.11) | Danny |

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
 
Durante la semana 2, Saray (AN) entrevistó a la administradora y a una recepcionista de la clínica, revisó cómo se lleva hoy la agenda en papel y en una hoja de cálculo, y redactó la primera versión de la especificación junto con un prototipo navegable en Figma. Hecha la verificación interna, se presentó el prototipo al cliente en la semana 3, porque ver las pantallas resulta mucho más útil que leer una lista de requisitos: en esta fase el cliente detectó en minutos detalles que en el documento habían pasado desapercibidos.

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

## 3.3 Resultado de verificación (TS-VER-01)
La verificación se hizo sobre la versión 0.2 de la especificación. Danny la revisó desde el punto de vista técnico (si cada requisito se puede construir y si hay contradicciones) y Jeancarlo desde las pruebas (si cada requisito tiene un criterio que se pueda comprobar). Encontraron seis defectos, que Saray corrigió en la versión 0.3 antes de mostrarla al cliente:

| # | Defecto encontrado | Tipo | Corrección |
|---|---|---|---|
| V1 | "El sistema debe ser rápido" | Ambiguo, no se puede probar | Se cuantificó en RNF-04 (< 3 s con 50 usuarios) |
| V2 | "Se puede cancelar con anticipación" | Ambiguo | Se fijó un plazo en horas (luego ajustado por el cliente) |
| V3 | Faltaba la recuperación de contraseña | Omisión | Se agregó a RF-02 |
| V4 | Reservar y consultar estaban descritos dos veces con reglas distintas | Inconsistencia | Se unificaron en RF-03 y RF-04 |
| V5 | No se decía qué pasa con los turnos de un médico desactivado | Omisión | Se aclaró en RF-07 |
| V6 | El rol "médico" podía ver la agenda de otros médicos | Riesgo de privacidad | Se restringió en RF-09 y RNF-02 |

## 3.4 Resultado de validación (TS-VAL-01)

La reunión de validación fue con la administradora (representante del cliente), Domenica y Saray. Se recorrió el prototipo pantalla por pantalla, simulando una reserva, una cancelación y la agenda de un día de un médico. El cliente estuvo de acuerdo con la estructura general, pero hizo cinco observaciones que se aplicaron en la versión 1.0:

| # | Observación del cliente | Decisión | Requisito afectado |
|---|---|---|---|
| O1 | La política real de cancelación es de 12 h, no de 24 h | Se ajusta | RF-05, RF-06 |
| O2 | Medicina general dura 20 minutos y los especialistas 30 | Se ajusta | RF-08 |
| O3 | Recepción necesita marcar "no asistió" para medir el ausentismo | Se agrega | RF-09 |
| O4 | El SMS o WhatsApp es caro por ahora; basta con correo | RG-10 sale del alcance de esta versión | — |
| O5 | Los reportes deben poder abrirse en Excel | Se agrega exportación a CSV | RF-12 |

Con esos cambios, el cliente **aprobó la Especificación de Requisitos v1.0**. Ese mismo día Danny etiquetó la versión en el repositorio como línea base **LB2**. Desde ese momento, cualquier modificación a estos requisitos ya no se trata como un ajuste informal, sino como una solicitud de cambio, que es lo que muestra la sección siguiente.

Vale la pena notar que las observaciones O1, O2 y O3 se habrían descubierto, en el mejor de los casos, en la demostración del incremento 2, con el código ya escrito. Haberlas encontrado con un prototipo costó unas pocas horas de ajuste en lugar de rehacer módulos completos, y es la razón principal por la que el retrabajo en requisitos se mantuvo bajo.

# 4. Gestionar una solicitud de cambio (GP.2.2 / GP.3)

## 4.1 Procedimiento acordado

Una **Solicitud de Cambio** es el pedido formal para modificar el software o su documentación, ya sea para corregir un problema o para agregar una mejora. Puede venir del cliente o del propio equipo. En el Perfil Básico, la gestora analiza el impacto en costo, plazo y aspectos técnicos (GP.2.2), y en GP.3 se controla que el cambio aprobado se implemente y se cierre. Si el cambio altera lo acordado con el cliente (alcance, plazo o costo), tienen que aprobarlo ambas partes. Si no lo altera, basta con actualizar el plan.

Cada solicitud pasa por los estados **Registrada → En análisis → Aceptada o Rechazada → Implementada → Verificada → Cerrada**, y se guarda en `docs/gestion/` con el nombre `TS-SC-<NN>`. Durante el proyecto se tramitaron dos solicitudes: una aceptada y una rechazada.

## 4.2 Solicitud de cambio SC-01: lista de espera

Después de la demostración del incremento 1, sea notó un problema que el equipo no había previsto. Cuando un paciente cancela, la franja queda libre, pero nadie se entera, y la clínica pierde esa consulta. Por eso pidió una **lista de espera**: que un paciente pueda anotarse en un día sin cupos y que, si alguien cancela, el sistema avise al primero de la lista.

| Campo | Contenido |
|---|---|
| Código | TS-SC-01 |
| Fecha de registro | 05/01/2027 |
| Solicitante | Administradora de la clínica (representante del CL), correo y teléfono en el expediente |
| Propósito del cambio | Recuperar las consultas que se pierden por cancelaciones avisando a pacientes en lista de espera |
| Tipo | Mejora (nuevo requisito RF-13) |
| Sistemas y componentes afectados | Módulo de turnos (cancelar y reprogramar), módulo de notificaciones, base de datos (nueva tabla de lista de espera), pantallas del paciente |
| Impacto en la operación de lo existente | RF-05 y RF-06 deben disparar el aviso a la lista de espera; RF-11 reutiliza el servicio de correo |
| Impacto en la documentación | Especificación de requisitos v1.1, diseño (modelo de datos), casos de prueba, manual de usuario y plan del proyecto v1.1 |
| Criticidad | Media: aporta valor de negocio, pero el sistema funciona sin el cambio |
| Fecha requerida | Antes de la entrega (12/02/2027) |
| Estado | Registrada → En análisis → **Aceptada (07/01/2027)** → Implementada → Verificada → **Cerrada (25/01/2027)** |

## 4.3 Análisis de impacto y decisión

Se realiza un análisis de la solicitud (Danny y Doménica) para determinar la estimación de esfuerzo, por ejemplo:

| Rol | Trabajo | Horas |
|---|---|---:|
| AN (Saray) | Especificar RF-13 y actualizar la especificación | 6 |
| DIS (Saray) | Pantalla de lista de espera y cambio en el modelo de datos | 4 |
| PR (Danny) | Lógica de la lista y el aviso al cancelar (backend) | 16 |
| PR (Jeancarlo) | Pantallas del paciente (frontend) | 10 |
| Pruebas (Jeancarlo) | Casos de prueba nuevos y regresión de RF-05 y RF-06 | 8 |
| GP (Domenica) | Análisis, actualización del plan y reunión con el cliente | 2 |
| **Total** | | **46 h × US$ 8,75 = US$ 402,50** |

En cuanto al **costo**, los US$ 402,50 se cubren con la reserva de contingencia, que pasa de US$ 1 980 a US$ 1 577,50 sin tocar el precio acordado. En cuanto al **plazo**, el cambio se puede repartir entre el incremento 2 (semanas 7 y 8) y el incremento 3 (semana 9). El análisis anticipó que la demostración del incremento 3 podía retrasarse un día, pero que la fecha de entrega no se movía. En lo **técnico**, el riesgo era bajo: el servicio de correo ya existía y la lógica de cancelación estaba aislada en un solo módulo.

Como el cambio modifica el alcance acordado, aunque no el precio ni la fecha, se debe llevar a cabo una reunión con el cliente para la debida aceptación. A partir de ahí Domenica actualiza el plan a la versión 1.1 y Saray la especificación a la 1.1 con el nuevo **RF-13**. Las horas de este cambio se registraron como trabajo de *producción* y no como retrabajo: no se estaba corrigiendo un error, sino construyendo algo nuevo que el cliente pidió y aprobó. La distinción importa para calcular bien el indicador de la sección 5.

## 4.4 Solicitud de cambio SC-02: pagos en línea (rechazada)

El cliente pidió además que los pacientes pudieran pagar la consulta al reservar. Domenica estimó al menos 120 horas (unos US$ 1 050) por la integración con una pasarela de pagos, las pruebas con transacciones reales, las comisiones por transacción y las exigencias de seguridad que implica manejar tarjetas. Eso no cabía en la reserva que quedaba ni en el calendario sin mover la entrega una semana. Además, los pagos en línea estaban **excluidos de forma explícita** en el alcance del Enunciado del Trabajo.

Se explica el análisis al cliente y la solicitud quedó **rechazada para esta versión**, con el acuerdo de registrarla como propuesta para una segunda fase con su propio presupuesto. Rechazar un cambio también es gestionarlo bien: lo que la norma exige es que la decisión se tome con un análisis de impacto y quede documentada, no que se diga que sí a todo.

| Campo | TS-SC-02 |
|---|---|
| Propósito | Cobrar la consulta en línea al reservar |
| Impacto estimado | ≥ 120 h, ≥ US$ 1 050, +1 semana de plazo, nuevos requisitos de seguridad |
| Criticidad | Baja para esta versión |
| Decisión | **Rechazada** (21/01/2027): fuera del alcance acordado; pasa a una futura fase 2 |

# 5. Medir el retrabajo y cerrar (GP.3, GP.4, IS.6)

## 5.1 Cómo se registraron las horas

Desde la primera semana, cada integrante anotó todos los días sus horas en una hoja de cálculo compartida, indicando la tarea del tablero Kanban y una de cuatro categorías. Clasificar bien cada hora fue la parte más difícil, así que el equipo acordó estas definiciones:

- **Gestión:** planificación, reuniones de seguimiento, reportes de avance, actas y análisis de solicitudes de cambio.
- **Producción:** trabajo nuevo, como especificar, diseñar, programar, redactar manuales o desplegar. Incluye los cambios aprobados, como SC-01.
- **Verificación y validación (V&V):** revisiones, pruebas unitarias, de integración y de aceptación, y reuniones de validación con el cliente.
- **Retrabajo:** cualquier hora dedicada a rehacer algo que ya se había dado por terminado, porque tenía un defecto o porque estaba mal entendido.

La regla práctica fue: *si la tarea existe porque algo anterior salió mal, es retrabajo; si existe porque alguien pidió algo nuevo, es producción.* Cada viernes Domenica consolidaba la hoja y la incluía en el reporte de avance semanal (GP.2).

## 5.2 Registro semanal de horas por categoría

| Sem. | Gestión | Producción | V&V | Retrabajo | Total | % retrabajo semana | % retrabajo acumulado |
|:-:|--:|--:|--:|--:|--:|--:|--:|
| 1 | 30 | 100 | 10 | 0 | 140 | 0,0 % | 0,0 % |
| 2 | 24 | 104 | 12 | 2 | 142 | 1,4 % | 0,7 % |
| 3 | 24 | 80 | 30 | 10 | 144 | 6,9 % | 2,8 % |
| 4 | 24 | 92 | 22 | 6 | 144 | 4,2 % | 3,2 % |
| 5 * | 20 | 80 | 12 | 4 | 116 | 3,4 % | 3,2 % |
| 6 * | 20 | 70 | 18 | 10 | 118 | 8,5 % | 4,0 % |
| 7 | 26 | 86 | 18 | 20 | 150 | 13,3 % | 5,5 % |
| 8 | 24 | 88 | 22 | 14 | 148 | 9,5 % | 6,0 % |
| 9 | 24 | 92 | 20 | 10 | 146 | 6,8 % | 6,1 % |
| 10 | 24 | 40 | 56 | 36 | 156 | **23,1 %** | 8,0 % |
| 11 | 24 | 40 | 60 | 24 | 148 | **16,2 %** | 8,8 % |
| 12 * | 30 | 40 | 12 | 4 | 86 | 4,7 % | 8,5 % |
| **Total** | **294** | **912** | **292** | **140** | **1 638** | | **8,5 %** |
| **%** | 17,9 % | 55,7 % | 17,8 % | 8,5 % | 100 % | | |

\* Semanas con feriados: 25/12/2026 (semana 5), 01/01/2027 (semana 6) y Carnaval 08 y 09/02/2027 (semana 12).

## 5.3 Cálculo y análisis del retrabajo

Con los totales del registro:

$$
\%\,\text{Retrabajo} = \frac{140\ \text{h}}{1\,638\ \text{h}} \times 100 = \mathbf{8{,}5\,\%} \qquad (\text{meta} \le 15\,\% \;\checkmark)
$$

El retrabajo costó 140 h × US$ 8,75 = **US$ 1 225**. Para dimensionar el resultado: si el proyecto hubiera tenido el 40 % de retrabajo típico de la industria, habrían sido unas 655 horas, casi cinco veces más, el equivalente a más de un mes de trabajo de todo el equipo.

Ahora bien, el promedio esconde dos semanas que superaron la meta. En la **semana 10** el retrabajo llegó al 23,1 %. Al integrar el frontend con el backend aparecieron muchos defectos de comunicación entre ambos: nombres de campos distintos, formatos de fecha y hora que no coincidían y validaciones que estaban en un lado pero no en el otro. Era un problema de método, no de un módulo en particular. Cada programador había trabajado con su propia idea del contrato de la API. En la revisión de GP.3 se registró la acción correctiva: documentar la API en un archivo OpenAPI compartido y agregar pruebas de integración automáticas a cada pull request. En la **semana 11** el retrabajo bajó al 16,2 %, todavía por encima de la meta porque incluía los cuatro casos que el cliente rechazó en la primera ronda de pruebas de aceptación. En la semana 12 ya estaba en 4,7 %.

El otro pico, de 13,3 % en la **semana 7**, vino de los defectos que el cliente encontró en la demostración del incremento 1. El más costoso fue un error de zona horaria que mostraba los turnos con una hora de diferencia en ciertos navegadores.

| Causa del retrabajo | Horas | % del retrabajo |
|---|--:|--:|
| Defectos de código detectados en pruebas internas | 64 | 45,7 % |
| Requisitos ambiguos u omitidos | 30 | 21,4 % |
| Defectos detectados por el cliente (demostraciones y aceptación) | 26 | 18,6 % |
| Errores de diseño | 12 | 8,6 % |
| Documentación | 8 | 5,7 % |
| **Total** | **140** | **100 %** |

La distribución por causa deja una lección clara. Casi la mitad del retrabajo fue código corregido después de las pruebas internas. Eso es esperable y, en cierto modo, es buena noticia: el defecto se encontró dentro del equipo y no lo vio el cliente. Las horas por requisitos (21,4 %) se concentraron en las semanas 3 y 4, cuando corregir costaba poco. Si esos mismos errores se hubieran descubierto en la semana 10, el impacto habría sido mucho mayor.

## 5.4 Reporte de avance final (plan frente a real)

| Indicador | Planificado | Real | Evaluación |
|---|---|---|---|
| Duración | 12 semanas | 12 semanas | ✔ En plazo |
| Esfuerzo | 1 728 h | 1 638 h (incluye las 46 h de SC-01) | ✔ −5,2 %, por los feriados |
| Costo total | US$ 18 000 (con reserva) | US$ 15 232,50 | ✔ 84,6 % del presupuesto |
| Hitos cumplidos en fecha | 8 | 7 de 8 | ⚠ H4c se demostró el 25/01 en lugar del 22/01, por SC-01 |
| Requisitos entregados | 12 RF + 5 RNF | 13 RF (con RF-13) + 5 RNF | ✔ |
| Casos de prueba de aceptación | 100 % aprobados | 38/42 en la 1.ª ronda; 42/42 en la 2.ª | ✔ |
| Defectos | — | 47 detectados (39 por el equipo, 8 por el cliente); 45 cerrados | ⚠ 2 defectos estéticos abiertos, cubiertos por la garantía |
| Retrabajo | ≤ 15 % | 8,5 % | ✔ |
| Solicitudes de cambio | — | 2 tramitadas: 1 aceptada, 1 rechazada | ✔ |

El costo real se compone de 1 638 h × US$ 8,75 = US$ 14 332,50 de personal, más US$ 700 de infraestructura y US$ 200 de capacitación. El esfuerzo quedó por debajo de lo planificado porque el plan se armó con la capacidad completa del equipo durante 12 semanas, y los cuatro días de feriado redujeron las horas disponibles. Que el proyecto igual terminara a tiempo se explica en buena parte porque RG-10 salió del alcance durante la validación y porque la semana 12 se había planificado solo para la entrega. Como el precio con el cliente es fijo, la diferencia de US$ 2 767,50 queda como margen de la VSE.
