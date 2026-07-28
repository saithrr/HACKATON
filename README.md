# HACKATON
# ⚡ EnergyAI LATAM: Optimización y Clasificación de Perfiles Energéticos

> *Un puente inteligente entre la narrativa de los hábitos de consumo y la Ciencia de Datos para transformar la gestión energética en América Latina.*

---

##  Descripción del Proyecto
Este proyecto forma parte de una solución integral orientada a evaluar, simular y clasificar el comportamiento energético de diferentes tipos de inmuebles (Casas, Apartamentos, Oficinas y Comercios) en la región de LATAM. 

A través de un enfoque basado en una **Línea Base Dinámica**, el sistema no solo analiza el volumen de consumo en kilovatios-hora (kWh), sino que pondera el impacto de variables contextuales como el clima regional, la estacionalidad temporal y los malos hábitos operativos (uso en horas pico y jornadas extendidas).

---

##  Lógica de Negocio y Criterios de Clasificación
Para evitar umbrales estáticos que ignoren la realidad del inmueble, el sistema calcula un estándar ideal personalizado:

$$\text{Ratio} = \frac{\text{Consumo Real (kWh)}}{\text{Línea Base Ajustada}}$$

### Perfiles Energéticos Definidos:
*   🟢 **Eficiente (`Ratio <= 1.05`):** El inmueble gasta lo esperado o menos según su infraestructura. Hábitos de consumo ejemplares.
*   🟡 **Moderado (`1.05 < Ratio <= 1.35`):** Supera ligeramente la meta ideal. Presenta áreas de oportunidad o uso intermitente en horas críticas.
*   🔴 **Ineficiente (`Ratio > 1.35`):** El consumo excede por más del 35% el valor de referencia o acumula penalizaciones graves por malas prácticas operativas.

---

##  Diccionario de Datos
El dataset sintético generado cuenta con **1,000 registros** estructurados de la siguiente manera:

| Nombre de Variable | Tipo de Dato | Descripción Detallada |
| :--- | :--- | :--- |
| **consumidor** | String | Identificador único asignado a cada inmueble simulado (`Usuario_1`, etc.). |
| **tipo_inmueble** | Categórica | Categoría de la propiedad: `Casa`, `Apartamento`, `Oficina` o `Comercio`. |
| **moneda_region** | Categórica | Código monetario (`USD`, `MXN`, `COP`, `ARS`, `CLP`, `PEN`, `BRL`) como proxy del clima regional. |
| **mes** | Entero | Mes del año del registro (`1` a `12`). Permite calcular estacionalidad climática. |
| **dia_semana** | Entero | Día de la semana (`0` = Lunes a `6` = Domingo). |
| **uso_horario_pico** | Entero / Booleano | `1` si concentra uso en horas de mayor demanda energética, `0` en caso contrario. |
| **cantidad_equipos** | Entero | Número total de equipos eléctricos activos (`1` a `40`). |
| **horas_alto_consumo** | Entero | Cantidad de horas al día que los equipos operan a máxima capacidad (`1` a `14`). |
| **consumo_kwh** | Flotante | **Variable Independiente principal:** Consumo mensual real simulado en kWh. |
| **perfil_energetico** | Categórica | **Variable Objetivo (Target):** Clasificación final (`Eficiente`, `Moderado`, `Ineficiente`). |

---

---

##  Plan de Trabajo - Próximo Sprint (Semana 2)
1.  **Codificación:** Aplicación de *One-Hot Encoding* a las variables categóricas (`tipo_inmueble`, `moneda_region`).
2.  **Escalado:** Normalización de variables continuas mediante `StandardScaler`.
3.  **Modelado:** Entrenamiento de un **Random Forest Classifier** como modelo principal, utilizando **Regresión Logística** como línea base de comparación.
4.  **Métricas de Éxito:** Evaluación mediante **F1-Score (Macro Average)** y Matriz de Confusión.

---
---

## ✒️ Autoría y Control del Proyecto

* **Desarrolladora:** [Saith Rocca]
* **Proyecto:** EnergyAI LATAM - Optimización y Clasificación de Perfiles Energéticos
* **SEMANA:** 1 (Simulación, EDA y Criterios de Ciencia de Datos)
* **Roles de Ejecución:** Data Analyst & Data Scientist
* **Estado del Entregable:** Completado, validado y sincronizado en producción (GitHub / Colab) ✅

> *"Transformando datos sintéticos en decisiones inteligentes para la gestión energética en América Latina."*
