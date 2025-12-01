# Isomorfismo Modular en Inteligencia Artificial: Del Anillo $\mathbb{Z}/6\mathbb{Z}$ a NPUs Shared-Nothing

[![License: PolyForm Noncommercial](https://img.shields.io/badge/License-PolyForm_Noncommercial_1.0.0-red.svg)](LICENSE)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-ee4c2c.svg)](https://pytorch.org/)
[![Platform](https://img.shields.io/badge/Platform-Google_Colab_%7C_Linux-orange.svg)](Notebooks/VALIDACION_Z_6Z_IA.ipynb)
[![Status](https://img.shields.io/badge/Status-Validated_(p_value_<_0.05)-success.svg)]()
[![DOI](https://img.shields.io/badge/DOI-Zenodo-blue)](https://doi.org/10.5281/zenodo.17777464)

**Autor:** José Ignacio Peinador Sala  
**Contacto:** [joseignacio.peinador@gmail.com](mailto:joseignacio.peinador@gmail.com)  
**ORCID:** [0009-0008-1822-3452](https://orcid.org/0009-0008-1822-3452) 

---

## 📜 Resumen Ejecutivo

Este repositorio presenta una nueva arquitectura para Inteligencia Artificial basada en el **Isomorfismo Modular**, diseñada para romper la dependencia de los chips monolíticos de alta densidad .

Utilizando el anillo $\mathbb{Z}/6\mathbb{Z}$, demostramos que es posible descomponer redes neuronales profundas (MLPs y Transformers) en un "enjambre" de 6 sub-redes independientes (*Shared-Nothing*) . Esta topología elimina la necesidad de coherencia de caché global y permite la construcción de NPUs mediante **chiplets de 28nm**, reduciendo los costes de fabricación en **18x** frente a los nodos de 3nm .

![Diagrama Hex-NPU](Images/Hex_Ensemble.png)
*> Esquema de la NPU Hex-Ensemble: Distribución pasiva de datos y procesamiento en 6 núcleos aislados sin comunicación cruzada.* 

---

## 🚀 Hito de Validación: Robustez y Generalización Inversa

La arquitectura ha sido validada experimentalmente, demostrando que la "ceguera parcial" de los módulos actúa como un potente regularizador estructural.

| Métrica | Resultado Validado | Referencia |
| :--- | :--- | :--- |
| **Precisión MNIST** | **97.03%** (vs 98.10% Monolítico) | |
| **Transformer (Val)** | **94.75%** (Gap de Generalización Inverso) | |
| **Robustez Estadística** | **p-value = 0.0112** (Monte Carlo N=10) | *Notebook Analysis* |
| **Reducción de Coste** | **18x** (Arbitraje de Nodos 28nm vs 3nm) | |
| **Aislamiento** | **Total (Shared-Nothing)** | |

---

## 📂 Estructura del Repositorio y 💻 Reproducibilidad

* **`Paper/`**: Manuscrito científico y demostraciones teóricas.
    * `Isomorfismo_IA.pdf`: Artículo completo detallando el operador *Stride-6* y el análisis económico. 
    * `Isomorfismo_IA.tex`: Código fuente LaTeX.
* **`Notebooks/`**: Código de validación y experimentos.
    * [VALIDACION_Z_6Z_IA](https://colab.research.google.com/github/NachoPeinador/Isomorfismo-Modular-Z-6Z-en-Inteligencia-Artificial/blob/main/Notebooks/VALIDACION_Z_6Z_IA.ipynb) :
   
        - **Prueba de Isomorfismo Tensorial**: Verificación matemática de la descomposición $C = A \times B$ con error $< 10^{-5}$ .
        - **Hex-Ensemble en MNIST**: Entrenamiento de 6 workers ciegos con agregación de votos .
        - **Análisis de Monte Carlo**: Test estadístico que confirma la reducción del overfitting en Transformers Modulares.
* **`Images/`**: Diagramas de arquitectura y gráficas de convergencia.

---

## ⚙️ Innovación Técnica

### 1. Operador de Proyección Modular (Stride-6)
Formalizamos un operador $\mathcal{P}_r$ que proyecta tensores densos en 6 sub-espacios disjuntos basándose en congruencias modulares . Esto permite transformar operaciones matriciales globales en operaciones locales paralelizables.

### 2. Regularización por "Ceguera Parcial"
Descubrimos un fenómeno de **Gap de Generalización Inverso** . Al impedir que cada worker vea el 83% de los datos, el sistema se ve forzado a aprender características robustas, evitando la memorización del ruido (Overfitting) y superando a los modelos densos en datos de validación .

### 3. Economía de Chiplets (Arbitraje de Nodos)
El diseño permite utilizar procesos de litografía maduros (28nm) para obtener rendimiento competitivo. Al evitar las retículas grandes y los defectos de los nodos de 3nm, el coste efectivo por transistor cae drásticamente, democratizando el acceso a hardware de IA de alto rendimiento .

---

## ⚖️ Licencia y Uso (Dual Licensing)

Este proyecto utiliza un modelo de **Licenciamiento Dual** alineado con los principios de la Ciencia Abierta sostenible .

### ✅ Uso Académico y No Comercial
El código fuente se distribuye bajo la licencia **PolyForm Noncommercial License 1.0.0**.
* **Permitido:** Investigación, educación y uso personal sin ánimo de lucro .
* **Requisito:** Mantener la atribución y este aviso de licencia.

### ⛔ Uso Comercial
Cualquier uso comercial (productos, servicios SaaS, consultoría) está **estrictamente prohibido** sin acuerdo previo .

> 💼 **Contacto para Licencias Comerciales:** [joseignacio.peinador@gmail.com](mailto:joseignacio.peinador@gmail.com) 

## ✍️ Citación

Si utiliza esta arquitectura o el código en su investigación, por favor cite:

```bibtex
Peinador Sala, J. I. (2025). Modular Isomorphism in Artificial Intelligence: From the Ring Z/6Z to Shared-Nothing Architecture NPUs (Versión v1). Zenodo. https://doi.org/10.5281/zenodo.17777464
```

---

## 🔬 Ciencia Independiente y Abierta

> *"La perfección no se alcanza cuando no hay nada más que añadir, sino cuando no hay nada más que quitar."* — **Antoine de Saint-Exupéry**

Este trabajo demuestra que la inteligencia robusta no requiere la complejidad de un monolito interconectado, sino la elegancia de módulos eficientes. Realizado de manera independiente para democratizar el acceso al hardware de alto rendimiento.

