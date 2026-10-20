# Acta de Constitución del Proyecto — Monitoreo de Motores

## Información General del Proyecto

| Campo | Detalle |
| :--- | :--- |
| **Nombre del proyecto** | Monitoreo inteligente de motores (pendiente por nombre) |
| **Patrocinador** | merge-conflicts |
| **Gerente del proyecto** | Yulieth Tatiana Rengifo |
| **Cliente** | Talleres, pequeñas industrias y laboratorios con motores eléctricos |
| **Responsable** | merge-conflicts |
| **Fecha de inicio esperada** | 15/09/2026 |
| **Fecha de finalización esperada** | 15/12/2026 |

## Definición del Problema

| Definición del problema |
| :--- |
| Los motores eléctricos son el corazón de la mayoría de procesos productivos y, a la vez, uno de los activos con mayor índice de fallas inesperadas: desbalance y desalineación (vibración), desgaste de rodamientos, sobrecalentamiento, sobrecorriente y sobrecarga. El mantenimiento actual suele ser correctivo (se actúa cuando el motor ya falló) o preventivo por calendario (se interviene aunque no sea necesario), lo que genera paradas no planificadas, costos de reparación elevados y consumo energético ineficiente. Los equipos de monitoreo industrial existentes son costosos, operan de forma aislada, no ofrecen notificaciones remotas en tiempo real y no integran inteligencia para anticipar fallas a partir de patrones de comportamiento. |

## Definición de los Objetivos

| Objetivos | Criterios de evaluación de los objetivos |
| :--- | :--- |
| **1. Diseñar e implementar un prototipo físico IoT para monitorear el estado de un motor eléctrico.** | Integración funcional de al menos 4 variables (vibración con acelerómetro MPU6050/ADXL345, temperatura con DS18B20 o termopar MAX6675, corriente con ACS712/SCT-013 y velocidad RPM con sensor óptico/encoder) con telemetría continua vía MQTT/HTTP hacia un servidor local o en la nube con latencia menor a 2 segundos. |
| **2. Desarrollar e integrar un modelo de Inteligencia Artificial para detección de anomalías y mantenimiento predictivo.** | Despliegue de un modelo de clasificación (Random Forest / Isolation Forest o clasificador de series de tiempo) capaz de diferenciar operación normal vs. fallas incipientes (desbalance, sobrecalentamiento, sobrecarga, desgaste de rodamiento) con una precisión (*accuracy*) >= 88 %, reduciendo falsas alarmas. |
| **3. Proporcionar una interfaz de usuario (Dashboard Web/Móvil) para alertas y gestión.** | Interfaz operativa que refleje el estado de los sensores en tiempo real, emita alertas push/correo ante anomalías y muestre el historial de eventos, el estado de salud del motor y las horas de operación. |
| **4. Cumplir con los hitos de entrega y documentación según el estándar PMI/académico.** | Entrega del 100 % de la documentación técnica, manual de arquitectura, código fuente versionado en Git y sustentación final dentro del calendario fijado. |

## Alcance del Proyecto

| Dentro del alcance | Fuera del alcance |
| :--- | :--- |
| • Diseño esquemático y prototipo funcional en protoboard/PCB con microcontrolador (ESP32 / Raspberry Pi Pico W).<br>• Calibración y lectura de sensores de vibración, temperatura, corriente y velocidad (RPM) sobre un motor de laboratorio de baja potencia.<br>• Módulo de comunicación inalámbrica (Wi-Fi) mediante protocolo MQTT o REST.<br>• Base de datos para persistencia de telemetría y lecturas históricas.<br>• Modelo de IA entrenado para clasificación de patrones de falla o estimación de la vida útil restante (RUL) del motor.<br>• Dashboard web responsivo para visualización y configuración de umbrales.<br>• Mecanismo de alerta local (buzzer + LED) y remota (notificación web/móvil). | • Comercialización, certificación industrial o sellos de seguridad (UL, RETIE, IEC).<br>• Monitoreo de motores de media/alta tensión o de potencias industriales elevadas (se trabajará con motores pequeños de laboratorio).<br>• Control de velocidad o arranque con variadores de frecuencia (VFD); el paro de emergencia se simulará mediante relé y testigo LED.<br>• Integración con sistemas SCADA/PLC industriales o ERP de mantenimiento.<br>• Provocar fallas mecánicas destructivas reales en el motor; las fallas se simularán (masas de desbalance, carga controlada, etc.).<br>• Desarrollo de hardware comercial final con carcasa inyectada (se utilizará caja prototipo o impresión 3D básica). |

## Suposiciones

| # | Suposición |
| :---: | :--- |
| 1 | Se cuenta con conectividad Wi-Fi estable y suministro eléctrico adecuado (110V/5V) en el entorno de pruebas del laboratorio. |
| 2 | Se dispone de un motor eléctrico de baja potencia (DC o AC monofásico) y de los elementos para simularle cargas y desbalances de forma segura. |
| 3 | Los módulos sensores comerciales (MPU6050, DS18B20, ACS712, etc.) tienen la sensibilidad adecuada para operar a escala de prototipo. |
| 4 | Se dispone de acceso a plataformas de almacenamiento o servidor local para desplegar el backend y el modelo de IA sin incurrir en costos elevados. |
| 5 | El equipo de trabajo cuenta con las herramientas para programación de microcontroladores (IDE Arduino/PlatformIO), backend/IA (Python) y desarrollo web. |

## Restricciones

| Restricción | Descripción |
| :--- | :--- |
| **Tiempo** | Plazo estricto de finalización supeditado al cierre del semestre académico (diciembre de 2026). |
| **Presupuesto** | Límite de financiamiento asumido por los integrantes para la compra de sensores, microcontroladores, motor y componentes electrónicos. |
| **Habilidades técnicas** | Curva de aprendizaje en procesamiento de señales de vibración (muestreo, FFT) y en la integración del protocolo IoT con el flujo de inferencia del modelo de IA. |
| **Seguridad física** | Prohibición expresa de realizar pruebas con partes giratorias sin protección, sobrecargas que puedan causar incendio o tensiones superiores a las del laboratorio sin supervisión del docente/laboratorista. |

## Factores Generales de Riesgo

| # | Riesgo | Consecuencia / Impacto | Dueño del plan de respuesta |
| :---: | :--- | :--- | :--- |
| 1 | Daño o defecto de fábrica en microcontrolador, sensores clave o en el motor de pruebas. | Retraso crítico en la recolección de datos y pruebas de hardware (Impacto Alto). | Responsable de Hardware (Adquisición de componentes de respaldo/stock crítico). |
| 2 | Insuficiencia o mala calidad de datos de vibración/corriente para entrenar el modelo de IA. | Desempeño deficiente o sobreajuste (*overfitting*) en la detección de fallas (Impacto Alto). | Responsable de IA / Datos (Uso de datasets públicos de monitoreo de motores y rodamientos + *data augmentation*). |
| 3 | Inestabilidad en la red Wi-Fi o pérdida de paquetes durante la telemetría. | Retardo o fallo en la activación de alertas tempranas (Impacto Medio). | Responsable de Firmware/IoT (Almacenamiento temporal en búfer local / SPIFFS en ESP32). |
| 4 | Desalineación de tiempos entre las entregas de ambas asignaturas (Gestión vs. Integrador). | Sobrecarga de trabajo en semanas de parciales/entregables (Impacto Medio). | Gerente del Proyecto (Cronograma sincronizado con entregables cruzados). |
| 5 | Ruido eléctrico y vibraciones externas que contaminan las lecturas de corriente y del acelerómetro (falsos positivos). | Pérdida de confianza en el sistema y alertas molestas (Impacto Alto). | Responsable de IA / Firmware (Filtrado de señales por ventana de tiempo, apantallamiento y ajuste de pesos en el modelo). |

## Interesados (Stakeholders)

| Interesado / Rol | Descripción y Responsabilidad |
| :--- | :--- |
| **Docente de Proyecto Integrador II** | Evalúa la viabilidad técnica, arquitectura del sistema, hardware e integración funcional de IoT e IA. |
| **Docente de Gestión de Proyectos** | Evalúa la metodología, cronograma, gestión de costos, riesgos y cumplimiento del acta de constitución y planes subsidiarios. |
| **Gerente de Proyecto (Líder del equipo)** | Responsable del cumplimiento de objetivos, coordinación técnica y comunicación interna. |
| **Desarrollador de Hardware y Firmware** | Encargado del diseño circuital, cableado, adquisición de datos de sensores y código en el microcontrolador. |
| **Ingeniero de Software e IA** | Responsable del preprocesamiento de señales, entrenamiento del modelo, creación de APIs y despliegue del servicio inteligente. |
| **Desarrollador Frontend / UI** | Diseña la interfaz para la visualización de métricas, alarmas e historial de salud del motor. |
| **Jefes de mantenimiento y operarios (Cliente / Usuario final)** | Personas que operan motores y requieren anticipar fallas y reducir paradas no planificadas. |
| **Monitores o laboratoristas de electrónica** | Facilitan equipos de medición (osciloscopios, multímetros, tacómetros) y el banco de pruebas. |
| **Proveedores locales de componentes electrónicos** | Entidades comerciales que suministran los módulos, sensores y cables a tiempo. |

## Hitos Principales

| Hito | Entregable principal | Fecha estimada (Semanas) |
| :--- | :--- | :---: |
| **Hito 1: Aprobación del Acta y Requisitos** | Acta de constitución firmada, EDT (WBS), historias de usuario y definición de arquitectura técnica. | Semana 2 - 3 |
| **Hito 2: Prototipo Hardware & Telemetría IoT** | Circuito ensamblado, lectura de variables (vibración, temperatura, corriente, RPM) validada y transmisión de datos vía MQTT a broker. | Semana 6 - 7 |
| **Hito 3: Entrenamiento y Despliegue de IA** | Modelo de detección de fallas entrenado, evaluado con métricas y servido mediante API. | Semana 10 - 11 |
| **Hito 4: Integración Total (IoT + IA + Dashboard)** | Plataforma conectada de extremo a extremo, pruebas de estrés y generación de alertas funcionales. | Semana 13 - 14 |
| **Hito 5: Sustentación Final y Cierre** | Demostración en vivo, informe final de gestión y entrega de repositorio y manuales. | Semana 15 - 16 |
