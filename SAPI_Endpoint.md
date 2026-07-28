Este documento define el **acuerdo formal de integración (Contrato de API)**.

---

#  Acuerdo de Formato de Datos (API Endpoint Contracto)

**Proyecto:** EnergyAI LATAM

**Módulo:** Evaluación de Perfil Energético en Tiempo Real

**Método HTTP:** `POST`

**Ruta sugerida:** `/api/v1/evaluar-perfil`

---

## 1. Estructura de Entrada (Request Body - JSON)

El servidor backend debe enviar un objeto JSON con los siguientes campos y tipos de datos para que el modelo de ciencia de datos pueda procesar la predicción:

```json
{
  "tipo_inmueble": "Casa",
  "moneda_region": "COP",
  "mes": 7,
  "dia_semana": 2,
  "uso_horario_pico": 1,
  "cantidad_equipos": 15,
  "horas_alto_consumo": 6,
  "consumo_kwh": 450.5
}

```

### Detalle de validación de campos (Request):

* `tipo_inmueble` (String): Debe ser estrictamente uno de los siguientes valores: `"Casa"`, `"Apartamento"`, `"Oficina"`, `"Comercio"`.
* `moneda_region` (String): Código de región/moneda: `"USD"`, `"MXN"`, `"COP"`, `"ARS"`, `"CLP"`, `"PEN"`, `"BRL"`.
* `mes` (Integer): Rango de `1` a `12`.
* `dia_semana` (Integer): Rango de `0` (Lunes) a `6` (Domingo).
* `uso_horario_pico` (Integer): `1` si hay consumo en hora pico, `0` si no.
* `cantidad_equipos` (Integer): Número entero mayor a 0.
* `horas_alto_consumo` (Integer): Horas operadas a máxima capacidad (ej. `1` a `14`).
* `consumo_kwh` (Float): Valor numérico real del consumo medido.

---

## 2. Estructura de Salida (Response Body - JSON)

Una vez procesada la lógica, la API devolverá la respuesta estructurada para que la interfaz de usuario (frontend) la muestre al cliente:

```json
{
  "estado": "success",
  "codigo_http": 200,
  "data": {
    "perfil_energetico": "Moderado",
    "detalles_evaluacion": {
      "consumo_reportado_kwh": 450.5,
      "alerta_habitos": "Se detectó concentración en horario pico."
    }
  }
}

```

---
