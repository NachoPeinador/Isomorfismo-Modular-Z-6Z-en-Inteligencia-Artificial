# Isomorfismo Modular en Inteligencia Artificial: Del Anillo $\mathbb{Z}/6\mathbb{Z}$ a NPUs Shared-Nothing

[![Read in English](https://img.shields.io/badge/Lang-Read%20in%20English-blue?style=flat&logoColor=white&color=B31B1B)](https://github.com/NachoPeinador/Isomorfismo-Modular-Z-6Z-en-Inteligencia-Artificial/blob/main/README.md)
[![License: PolyForm Noncommercial](https://img.shields.io/badge/License-PolyForm_Noncommercial_1.0.0-red.svg)](LICENSE)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-ee4c2c.svg)](https://pytorch.org/)
[![Papers](https://img.shields.io/badge/Paper-Read_PDF-B31B1B?style=flat&logo=latex&logoColor=white)](https://github.com/NachoPeinador/Isomorfismo-Modular-Z-6Z-en-Inteligencia-Artificial/blob/main/Paper/Isomorfismo_IA.pdf)
[![Status](https://img.shields.io/badge/Status-Validated_(p_value_<_0.05)-success.svg)]()
[![DOI](https://img.shields.io/badge/DOI-Zenodo-blue)](https://doi.org/10.5281/zenodo.18505586)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NachoPeinador/Isomorfismo-Modular-Z-6Z-en-Inteligencia-Artificial/blob/main/Notebooks/VALIDACION_Z_6Z_IA.ipynb)

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
    * [![Papers](https://img.shields.io/badge/Paper-Read_PDF-B31B1B?style=flat&logo=latex&logoColor=white)](https://github.com/NachoPeinador/Isomorfismo-Modular-Z-6Z-en-Inteligencia-Artificial/blob/main/Paper/Isomorfismo_IA.pdf)
* **`Notebooks/`**: Código de validación y experimentos.
  
    *  [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/NachoPeinador/Isomorfismo-Modular-Z-6Z-en-Inteligencia-Artificial/blob/main/Notebooks/VALIDACION_Z_6Z_IA.ipynb)
   
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

## 🏛️ Fundamentos Teóricos y Computacionales

Esta arquitectura Hex-NPU es la tercera evolución de la **Teoría del Espectro Modular**. Antes de aplicarse al Cálculo Tensorial y la Inteligencia Artificial, el paradigma *Shared-Nothing* verificó su robustez en la Teoría de Números y la Computación de Alto Rendimiento (HPC).

Las garantías matemáticas del operador **Stride-6** y el **Isomorfismo DSP** se fundamentan en estos dos trabajos precedentes:

### 1. Validación Algorítmica: El Motor $\pi$ a Exaescala
**Repositorio:** [Arquitectura-de-Hibridacion-Algoritmica-en-Z-6Z](https://github.com/NachoPeinador/Arquitectura-de-Hibridacion-Algoritmica-en-Z-6Z)  
Demostramos que el **algoritmo de Chudnovsky** (el estándar para calcular $\pi$) podía descomponerse en 6 "canales polifásicos" independientes.
* **Logro:** Se calcularon **100 Millones de dígitos** de $\pi$ utilizando una arquitectura *Shared-Nothing* con una eficiencia paralela del 95%.
* **Relevancia para la IA:** Validó que operaciones globales complejas pueden ser isomorfas a operaciones modulares locales sin pérdida de información.

### 2. Génesis Matemática: El Espectro Modular
**Repositorio:** [Espectro-Modular-Pi](https://github.com/NachoPeinador/Espectro-Modular-Pi)  
La investigación fundacional que estableció el anillo $\mathbb{Z}/6\mathbb{Z}$ como la estructura óptima para la computación paralela.
* **Teoría Central:** Demostró que la distribución de números primos ($6k \pm 1$) crea un "Sustrato Primo" natural que permite la separación ortogonal de canales.
* **Relevancia para la IA:** Proporciona la justificación teórico-numérica de por qué **6 workers** (y no 4 u 8) ofrecen el equilibrio óptimo entre densidad y dispersión de canales.

Claro, aquí tienes la propuesta traducida al español:

---

## 🚀 La Próxima Evolución: De la Teoría al Silicio

La descomposición modular validada en Teoría de Números (cálculo de π) y formalizada en Álgebra Tensorial (IA) encuentra su expresión última en una **implementación física**: un diseño de chip completo optimizado para coste, privacidad y sostenibilidad.

### 3. Realización Física: El Chip FrugalAI
**Repositorio:** [FRUGAL_AI_CHIP](https://github.com/NachoPeinador/FRUGAL_AI_CHIP)  
Esta investigación traduce el paradigma **Shared-Nothing** a una arquitectura de silicio completa diseñada para aplicaciones de IA desechable en el edge.

* **Innovación Clave:** Aplica el operador Stride-6 a nivel hardware, implementando **Static Slicing**—un compilador que resuelve todo el enrutamiento de datos en tiempo de compilación, eliminando los requisitos de coherencia de caché.
* **Avance Económico:** Logra una **eficiencia de capital 10.9× superior** al aprovechar silicio maduro de 28nm frente a nodos de vanguardia de 3nm.
* **Privacidad por Diseño:** El aislamiento físico de las SRAM locales proporciona **privacidad intrínseca** sin sobrecarga de software.
* **Validación Experimental:** Demostró una mejora de precisión de **+4.8%** en CIFAR-10 mediante especialización implícita de ensemble, y una aceleración de **21.47×** para inferencia con Transformers.

### 🔄 Trayectoria de Investigación Completa
Esto completa el arco de investigación: desde el **descubrimiento matemático** (espectro de π) → **validación algorítmica** (HPC a exaescala) → **formalización teórica** (isomorfismo tensorial) → **implementación física** (silicio frugal). Cada etapa se construye sobre y valida el paradigma modular, demostrando su universalidad en los dominios computacionales.

**[👉 Explora el Diseño Completo del Chip y la Economía](https://github.com/NachoPeinador/FRUGAL_AI_CHIP/blob/main/README.md)**

---

La sección mantiene la misma estructura y tono en español, destacando claramente la conexión entre todos tus proyectos de investigación.

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
Peinador Sala, J. I. (2025). Modular Isomorphism in Artificial Intelligence: From the Ring Z/6Z to Shared-Nothing Architecture NPUs (Versión v1). Zenodo. https://doi.org/10.5281/zenodo.18505586
```

---

## 🔬 Ciencia Independiente y Abierta

> *"La perfección no se alcanza cuando no hay nada más que añadir, sino cuando no hay nada más que quitar."* — **Antoine de Saint-Exupéry**

Este trabajo demuestra que la inteligencia robusta no requiere la complejidad de un monolito interconectado, sino la elegancia de módulos eficientes. Realizado de manera independiente para democratizar el acceso al hardware de alto rendimiento.

