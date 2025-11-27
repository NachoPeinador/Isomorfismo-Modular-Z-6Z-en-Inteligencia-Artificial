# Isomorfismo Modular en Inteligencia Artificial: Del Anillo $\mathbb{Z}/6\mathbb{Z}$ a NPUs de Arquitectura Shared-Nothing

[![License: PolyForm Noncommercial](https://img.shields.io/badge/License-PolyForm_Noncommercial_1.0.0-red.svg)](LICENSE)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![Platform](https://img.shields.io/badge/Platform-PyTorch_%7C_CUDA-orange.svg)](notebooks/hex_ensemble_mnist.ipynb)
[![Status](https://img.shields.io/badge/Status-Validated_(MNIST_97%25)-success.svg)]()
[![DOI](https://img.shields.io/badge/DOI-Preprint_Pending-lightgrey)](https://zenodo.org/)

**Autor:** José Ignacio Peinador Sala  
**Contacto:** [joseignacio.peinador@gmail.com](mailto:joseignacio.peinador@gmail.com)  
**ORCID:** [0009-0008-1822-3452](https://orcid.org/0009-0008-1822-3452)

---

## 📜 Resumen Ejecutivo

Este repositorio contiene la **implementación de referencia** y la validación experimental de la arquitectura **Hex-Ensemble**, una propuesta de hardware para IA basada en el principio de **"Shared-Nothing"** (Sin Compartición).

Frente al paradigma monolítico actual que enfrenta límites termodinámicos, este trabajo propone el uso del **Isomorfismo Modular** bajo el anillo $\mathbb{Z}/6\mathbb{Z}$ para descomponer redes neuronales profundas en seis sub-redes independientes. Esto permite reemplazar las costosas interconexiones de baja latencia y las matrices de silicio de 3nm por un "enjambre" de *chiplets* económicos de 28nm, logrando una reducción de costes de **18x** sin sacrificar significativamente la precisión predictiva.

![Esquema NPU Hex-Ensemble](img/hex_npu_arch.png)
*> Esquema conceptual: Distribución determinista de tensores mediante bus de diezmado pasivo hacia 6 núcleos aislados.*

---

## 🚀 Hitos de Validación

La arquitectura ha sido validada experimentalmente demostrando que la falta de comunicación entre nodos (*Shared-Nothing*) actúa como un regularizador estructural eficiente, permitiendo un rendimiento competitivo con una fracción del coste.

| Experimento | Modelo Base | Precisión Monolítica | Precisión Modular (Hex) | Gap |
| :--- | :--- | :--- | :--- | :--- |
| **Visión (CV)** | MLP (MNIST) | 98.10% | **97.03%** | -1.07% |
| **Lenguaje (NLP)** | Transformer | 100.00% | **94.75%** | -5.25% |
| **Eficiencia** | **Coste Silicio** | $666.67 (3nm) | **$37.92 (28nm)** | **-94% (18x)** |

---

## 📂 Estructura del Repositorio

* **`src/`**: Código fuente del motor modular.
    * `hex_layers.py`: Implementación de capas `Linear` y `Attention` con soporte nativo para Stride-6.
    * `hex_ensemble.py`: Orquestador de los 6 workers aislados y lógica de *Logit Mixing*.
* **`paper/`**: Manuscrito científico unificado (LaTeX/PDF).
    * **"Isomorfismo Modular en Inteligencia Artificial: Del Anillo $\mathbb{Z}/6\mathbb{Z}$ a NPUs de Arquitectura Shared-Nothing"**.
* **`notebooks/`**: Experimentos reproducibles.
    * `Hex_Ensemble_MNIST_Validation.ipynb`: Entrenamiento y validación en clasificación de dígitos.
    * `Modular_Transformer_PoC.ipynb`: Prueba de concepto de atención modular distribuida.
* **`analysis/`**: Modelos económicos.
    * `yield_wafer_model.xlsx`: Hoja de cálculo del modelo de costes (Yield/Wafer) comparando nodos de 28nm vs 3nm.

---

## ⚙️ Innovación Técnica

### 1. Operador de Diezmado Modular (Tensor Stride-6)
Formalizamos un operador matemático $\mathcal{P}_r$ que proyecta cualquier tensor de entrada en 6 sub-espacios disjuntos basándose en la congruencia $i \equiv r \pmod 6$. Esto transforma el problema de multiplicación de matrices densas en 6 problemas independientes de menor dimensión, isomorfos a la **Descomposición Polifase** en DSP.

### 2. Arquitectura "Shared-Nothing"
Cada uno de los 6 *Workers* opera con su propia memoria SRAM local y no tiene acceso físico a la memoria de los demás. Esto elimina la necesidad de coherencia de caché y buses de alto ancho de banda, permitiendo una escalabilidad lineal teórica ilimitada y reduciendo drásticamente el consumo energético por movimiento de datos.

### 3. Arbitraje de Nodos (Economic Moat)
La arquitectura permite fabricar chips de IA de alto rendimiento utilizando nodos de litografía maduros (28nm) en lugar de nodos de vanguardia (3nm). Aprovechando el mayor *Yield* (rendimiento de oblea) de los chips pequeños y baratos, se logra una ventaja económica masiva frente a las GPUs monolíticas.

---

## ⚖️ Licencia y Uso (Dual Licensing)

Este proyecto utiliza un modelo de **Licenciamiento Dual** para fomentar la innovación abierta manteniendo la sostenibilidad de la investigación independiente.

### ✅ Uso Académico y Open Source (Gratuito)
El código fuente y la documentación están disponibles bajo la licencia **PolyForm Noncommercial License 1.0.0**.
* **Permitido:** Uso personal, investigación académica, docencia y proyectos de código abierto (sin ánimo de lucro).
* **Requisito:** Debe atribuir la autoría original y mantener este aviso de licencia.

### ⛔ Uso Comercial (Requiere Licencia)
**La integración en productos propietarios, servicios de pago o hardware comercial cerrado está prohibida** sin un acuerdo previo. Esto incluye:
* Aceleradores de hardware (ASIC/FPGA) propietarios.
* Servicios de inferencia SaaS cerrados.
* Consultoría comercial basada en esta arquitectura.

> 💼 **Para obtener una Licencia Comercial (exención de Copyleft)**, contacte con el autor: [joseignacio.peinador@gmail.com](mailto:joseignacio.peinador@gmail.com)

---

## 💻 Reproducibilidad

Para replicar el experimento de MNIST en su máquina local:

1.  Clone el repositorio.
2.  Instale las dependencias: `pip install torch torchvision numpy`
3.  Ejecute el script de entrenamiento:
    ```bash
    python src/train_hex_mnist.py --epochs 5 --batch-size 64
    ```

---

## ✍️ Citación

Si utiliza esta arquitectura, el operador Stride-6 o el análisis económico en su investigación, por favor cite el artículo original:

```bibtex
@article{PeinadorSala2025_HexNPU,
  author = {Peinador Sala, José Ignacio},
  title = {Isomorfismo Modular en Inteligencia Artificial: Del Anillo Z/6Z a NPUs de Arquitectura Shared-Nothing},
  year = {2025},
  publisher = {Zenodo},
  version = {v1.0},
  doi = {10.5281/zenodo.XXXXXXX}
}
