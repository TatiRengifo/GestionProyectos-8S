## Plantilla: Acta de Constitución del Proyecto — Monitoreo de Motores

| Acta de constitución |   |   |   |
| --- | --- | --- | --- |
| Nombre del proyecto: |   | Sistema IoT inteligente para el monitoreo y mantenimiento predictivo de motores eléctricos. |   |
| Patrocinador: | merge-conflicts | Gerente del proyecto: | Yulieth Tatiana Rengifo |
| Cliente: | Talleres, pequeñas industrias y laboratorios con motores eléctricos | Responsable: | merge-conflicts |
| Fecha de inicio esperada: | 15/09/2026 | Fecha de finalización esperada: | 15/12/2026 |

## Definición del problema

Los motores eléctricos son el corazón de la mayoría de procesos productivos y, a la vez, uno de los activos con mayor índice de fallas inesperadas: desbalance y desalineación (vibración), desgaste de rodamientos, sobrecalentamiento, sobrecorriente y sobrecarga. El mantenimiento actual suele ser correctivo (se actúa cuando el motor ya falló) o preventivo por calendario (se interviene aunque no sea necesario), lo que genera paradas no planificadas, costos de reparación elevados y consumo energético ineficiente. Los equipos de monitoreo industrial existentes son costosos, operan de forma aislada, no ofrecen notificaciones remotas en tiempo real y no integran inteligencia para anticipar fallas a partir de patrones de comportamiento.

| Definición de los objetivos |   |
| --- | --- |
| Objetivos | Criterios de evaluación de los objetivos |
| 1. Diseñar e implementar un prototipo físico IoT para monitorear el estado de un motor eléctrico. | Integración funcional de al menos 4 variables (vibración con acelerómetro MPU6050/ADXL345, temperatura con DS18B20 o termopar MAX6675, corriente con ACS712/SCT-013 y velocidad RPM con sensor óptico/encoder) con telemetría continua vía MQTT/HTTP hacia un servidor local o en la nube con latencia menor a 2 segundos. |
| 2. Desarrollar e integrar un modelo de Inteligencia Artificial para detección de anomalías y mantenimiento predictivo. | Despliegue de un modelo de clasificación (Random Forest / Isolation Forest o clasificador de series de tiempo) capaz de diferenciar operación normal vs. fallas incipientes (desbalance, sobrecalentamiento, sobrecarga, desgaste de rodamiento) con una precisión (accuracy) >= 88 %, reduciendo falsas alarmas. |
| 3. Proporcionar una interfaz de usuario (Dashboard Web/Móvil) para alertas y gestión. | Interfaz operativa que refleje el estado de los sensores en tiempo real, emita alertas push/correo ante anomalías y muestre el historial de eventos, el estado de salud del motor y las horas de operación. |


4. Cumplir con los hitos de entrega y documentación según el estándar PMI/académico.

## Alcance

## Dentro del alcance

- Diseño esquemático y prototipo funcional en protoboard/PCB con microcontrolador (ESP32 / Raspberry Pi Pico W).

- Calibración y lectura de sensores de vibración, temperatura, corriente y velocidad (RPM) sobre un motor de laboratorio de baja potencia.

- Módulo de comunicación inalámbrica (Wi-Fi) mediante protocolo MQTT o REST.

- Base de datos para persistencia de telemetría y lecturas históricas.

- Modelo de IA entrenado para clasificación de patrones de falla o estimación de la vida útil restante (RUL) del motor.

- Dashboard web responsivo para visualización y configuración de umbrales.

- Mecanismo de alerta local (buzzer + LED) y remota (notificación web/móvil).

## Suposiciones

- Se cuenta con conectividad Wi-Fi estable y suministro eléctrico adecuado (110V/5V) en el entorno de pruebas del laboratorio.

- Se dispone de un motor eléctrico de baja potencia (DC o AC monofásico) y de los elementos para simularle cargas y desbalances de forma segura.

- Los módulos sensores comerciales (MPU6050, DS18B20, ACS712, etc.) tienen la sensibilidad adecuada para operar a escala de prototipo.

- Se dispone de acceso a plataformas de almacenamiento o servidor local para desplegar el backend y el modelo de IA sin incurrir en costos elevados.

- El equipo de trabajo cuenta con las herramientas para programación de microcontroladores (IDE Arduino/PlatformIO), backend/IA (Python) y desarrollo web.

Entrega del 100 % de la documentación técnica, manual de arquitectura, código fuente versionado en Git y sustentación final dentro del calendario fijado.

## Fuera del alcance

- Comercialización, certificación industrial o sellos de seguridad (UL, RETIE, IEC).

- Monitoreo de motores de media/alta tensión o de potencias industriales elevadas (se trabajará con motores pequeños de laboratorio).

- Control de velocidad o arranque con variadores de frecuencia (VFD); el paro de emergencia se simulará mediante relé y testigo LED.

- Integración con sistemas SCADA/PLC industriales o ERP de mantenimiento.

- Provocar fallas mecánicas destructivas reales en el motor; las fallas se simularán (masas de desbalance, carga controlada, etc.).

- Desarrollo de hardware comercial final con carcasa inyectada (se utilizará caja prototipo o impresión 3D básica).

## Restricciones

- Tiempo: Plazo estricto de finalización supeditado al cierre del semestre académico (diciembre de 2026).

- Presupuesto: Límite de financiamiento asumido por los integrantes para la compra de sensores, microcontroladores, motor y componentes electrónicos.

- Habilidades técnicas: Curva de aprendizaje en procesamiento de señales de vibración (muestreo, FFT) y en la integración del protocolo IoT con el flujo de inferencia del modelo de IA.


- Seguridad física: Prohibición expresa de realizar pruebas con partes giratorias sin protección, sobrecargas que puedan causar incendio o tensiones superiores a las del laboratorio sin supervisión del docente/laboratorista.

## Factores generales de riesgo

| # | Riesgo | Consecuencia / Impacto | Dueño del plan de respuesta |
| --- | --- | --- | --- |
| 1 | Daño o defecto de fábrica en microcontrolador, sensores clave o en el motor de pruebas. | Retraso crítico en la recolección de datos y pruebas de hardware (Impacto Alto). | Responsable de Hardware (Adquisición de componentes de respaldo/stock crítico). |
| 2 | Insuficiencia o mala calidad de datos de vibración/corriente para entrenar el modelo de IA. | Desempeño deficiente o sobreajuste (overfitting) en la detección de fallas (Impacto Alto). | Responsable de IA / Datos (Uso de datasets públicos de monitoreo de motores y rodamientos + data augmentation). |
| 3 | Inestabilidad en la red Wi-Fi o pérdida de paquetes durante la telemetría. | Retardo o fallo en la activación de alertas tempranas (Impacto Medio). | Responsable de Firmware/IoT (Almacenamiento temporal en búfer local / SPIFFS en ESP32). |
| 4 | Desalineación de tiempos entre las entregas de ambas asignaturas (Gestión vs. Integrador). | Sobrecarga de trabajo en semanas de parciales/entregables (Impacto Medio). | Gerente del Proyecto (Cronograma sincronizado con entregables cruzados). |
| 5 | Ruido eléctrico y vibraciones externas que contaminan las lecturas de corriente y del acelerómetro (falsos positivos). | Pérdida de confianza en el sistema y alertas molestas (Impacto Alto). | Responsable de IA / Firmware (Filtrado de señales por ventana de tiempo, apantallamiento y ajuste de pesos en el modelo). |

## Interesados

- Docente de Proyecto Integrador II: Evalúa la viabilidad técnica, arquitectura del sistema, hardware e integración funcional de IoT e IA.

- Docente de Gestión de Proyectos: Evalúa la metodología, cronograma, gestión de costos, riesgos y cumplimiento del acta de constitución y planes subsidiarios.

- Gerente de Proyecto (Líder del equipo): Responsable del cumplimiento de objetivos, coordinación técnica y comunicación interna.

- Desarrollador de Hardware y Firmware: Encargado del diseño circuital, cableado, adquisición de datos de sensores y código en el microcontrolador.

- Ingeniero de Software e IA: Responsable del preprocesamiento de señales, entrenamiento del modelo, creación de APIs y despliegue del servicio inteligente.

- Desarrollador Frontend / UI: Diseña la interfaz para la visualización de métricas, alarmas e historial de salud del motor.


- Jefes de mantenimiento y operarios (Cliente / Usuario final): Personas que operan motores y requieren anticipar fallas y reducir paradas no planificadas.

- Monitores o laboratoristas de electrónica: Facilitan equipos de medición (osciloscopios, multímetros, tacómetros) y el banco de pruebas.

- Proveedores locales de componentes electrónicos: Entidades comerciales que suministran los módulos, sensores y cables a tiempo.

| Hitos principales |   |   |
| --- | --- | --- |
| Hito | Entregable principal | Fecha estimada (Semanas) |
| Hito 1: Aprobación del Acta y Requisitos | Acta de constitución firmada, EDT (WBS), historias de usuario y definición de arquitectura técnica. | Semana 2 - 3 |
| Hito 2: Prototipo Hardware & Telemetría IoT | Circuito ensamblado, lectura de variables (vibración, temperatura, corriente, RPM) validada y transmisión de datos vía MQTT a broker. | Semana 6 - 7 |
| Hito 3: Entrenamiento y Despliegue de IA | Modelo de detección de fallas entrenado, evaluado con métricas y servido mediante API. | Semana 10 - 11 |
| Hito 4: Integración Total (IoT + IA + Dashboard) | Plataforma conectada de extremo a extremo, pruebas de estrés y generación de alertas funcionales. | Semana 13 - 14 |
|   | Hito 5: Sustentación Final y Cierre Demostración en vivo, informe final de gestión y entrega de repositorio y manuales. | Semana 15 - 16 |

|   | Historias de usuario |   |   |
| --- | --- | --- | --- |
|   | ID Historia | Criterios de aceptación | Prioridad |
| HU- 01 | Como jefe de mantenimiento, quiero ver en tiempo real la temperatura, vibración, corriente y RPM del motor en un dashboard, para conocer su estado de operación sin acercarme a la máquina | • Los 4 valores se actualizan con latencia menor a 2 s. • Cada variable se muestra con su unidad y una gráfica de tendencia. • Se indica claramente si el motor está encendido o apagado. | Alta |
| HU- 02 | Como operario, quiero recibir una alerta sonora y visual local (buzzer + LED) cuando una variable supere su umbral crítico, para reaccionar de inmediato aunque no esté frente al dashboard | • La alerta se activa en menos de 2 s tras superar el umbral. • El LED distingue nivel de advertencia y nivel crítico. • La alarma local funciona aunque se pierda la conexión Wi-Fi. | Alta |


| HU- 03 | Como jefe de mantenimiento, quiero recibir notificaciones push o por correo ante una anomalía detectada, para enterarme de una posible falla estando fuera de la planta | • La notificación indica motor, variable afectada, valor y hora. • Se envía en menos de 10 s desde la detección. • No se repiten alertas idénticas dentro de una ventana configurable. | Alta |
| --- | --- | --- | --- |
| HU- 04 | Como ingeniero de mantenimiento, quiero que el sistema clasifique automáticamente el tipo de falla (desbalance, sobrecalentamiento, sobrecarga, desgaste de rodamiento), para saber qué intervención realizar | • El modelo alcanza accuracy >= 88 % sobre el conjunto de prueba. • El dashboard muestra la clase detectada y su nivel de confianza. • La tasa de falsas alarmas se reporta y es menor a la de un umbral fijo. | Alta |
| HU- 05 | Como jefe de mantenimiento, quiero configurar desde el dashboard los umbrales de temperatura, corriente y vibración de cada motor, para adaptar el monitoreo a motores de distintas características | • Los umbrales se editan y guardan sin reiniciar el dispositivo. • Se validan rangos permitidos y se rechazan valores inválidos. • Los cambios se reflejan en el firmware en menos de 5 s. | Media |
| HU- 06 | Como analista de mantenimiento, quiero consultar el historial de lecturas y eventos por rango de fechas, para identificar patrones y justificar decisiones de mantenimiento | • Se puede filtrar por fecha, variable y tipo de evento. • Se exporta el historial en formato CSV. • Los datos se conservan al menos durante el periodo del proyecto. | Media |
| HU- 07 | Como jefe de mantenimiento, quiero ver un indicador de "salud del motor" con una estimación de vida útil restante, para planificar el mantenimiento antes de que ocurra la falla | • El indicador se expresa en porcentaje o escala de colores (verde/amarillo/rojo). • Se actualiza con cada ventana de inferencia del modelo. • Se muestra la tendencia de salud de los últimos 7 días. | Media |
| HU- 08 | Como técnico de campo, quiero que el dispositivo guarde las lecturas localmente si se cae la red y las sincronice al reconectarse, para no perder datos ni eventos críticos durante cortes de conectividad | • El búfer local almacena como mínimo 30 min de telemetría. • Al restablecerse la conexión, los datos se envían en orden cronológico. • No se pierden eventos de alerta durante la desconexión. | Media |

## Firma

- Firmado por: 

- *Pedro José López Quiroz*

- Estudiante de la Universidad del Valle
- Codigo: 2359423
