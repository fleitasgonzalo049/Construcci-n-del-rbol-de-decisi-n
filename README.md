# 🌳 Árbol de Decisión: Predicción de Aceptación de Plan de Datos

## 📌 Descripción
Este proyecto resuelve un problema de clasificación utilizando un **Árbol de Decisión**. El objetivo es predecir si un cliente de una empresa de telecomunicaciones aceptará una oferta de plan de datos móviles basándonos en sus atributos.

---

## 📊 Datos del Conjunto (10 Clientes)

| ID | Edad | Uso de Datos | Tiene Línea Fija | Aceptó Oferta |
|:--:|:----:|:------------:|:----------------:|:-------------:|
| 1  | 24   | 2.5 GB       | No               | **No**        |
| 2  | 38   | 6.0 GB       | Sí               | **Sí**        |
| 3  | 29   | 3.0 GB       | No               | **No**        |
| 4  | 45   | 8.0 GB       | Sí               | **Sí**        |
| 5  | 52   | 7.5 GB       | Sí               | **Sí**        |
| 6  | 33   | 4.0 GB       | No               | **No**        |
| 7  | 41   | 5.5 GB       | Sí               | **Sí**        |
| 8  | 27   | 2.0 GB       | No               | **No**        |
| 9  | 36   | 6.5 GB       | Sí               | **Sí**        |
| 10 | 31   | 3.5 GB       | No               | **No**        |

---

## ⚙️ Análisis y Pasos

### 1. Estado Inicial
* **Total de clientes:** 10
* **Aceptaron (Sí):** 5 clientes
* **Rechazaron (No):** 5 clientes
* La mezcla está totalmente emparejada (50% y 50%), por lo que la **entropía inicial es máxima (1.0 bit)**.

### 2. Evaluación de Atributos (Ganancia de Información)

Analizamos qué atributo separa mejor a los clientes que aceptan de los que no:

1. **Tiene línea fija:**
   * **Sí (5 clientes):** Los 5 aceptaron la oferta.
   * **No (5 clientes):** Los 5 rechazaron la oferta.
   * **Resultado:** Separa perfectamente los datos. **Ganancia = 1.0 bit** (Máxima).

2. **Uso de datos:**
   * **Bajo ($\le 3$ GB):** 3 clientes, ninguno aceptó.
   * **Medio (3.1 a 6 GB):** 4 clientes, 2 aceptaron y 2 no.
   * **Alto ($> 6$ GB):** 3 clientes, todos aceptaron.
   * **Resultado:** Separa bien pero no es perfecto. **Ganancia = 0.6 bits**.

3. **Edad:**
   * **Joven ($\le 30$):** 3 clientes, ninguno aceptó.
   * **Adulto (31 a 50):** 6 clientes, 4 aceptaron y 2 no.
   * **Mayor ($> 50$):** 1 cliente, aceptó.
   * **Resultado:** Es el atributo menos preciso. **Ganancia = 0.449 bits**.

---

## 🏆 Árbol de Decisión Resultante

El atributo **Tiene línea fija** se elige como el nodo principal porque divide los datos de forma perfecta sin cometer ningún error.

```text
               [¿Tiene línea fija?]
                   /         \
                 Sí           No
                /               \
   [Predicción: Acepta (Sí)]   [Predicción: Rechaza (No)]
