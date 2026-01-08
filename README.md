# Transmisor de TV Analógica NTSC con SDR y Etapa de Potencia RF

**Universidad de Cuenca - Facultad de Ingeniería** **Curso de Circuitos de Radiofrecuencia** *Septiembre 2024 - Febrero 2025*

![Status](https://img.shields.io/badge/Status-Finalizado-success)
![Hardware](https://img.shields.io/badge/Hardware-HackRF_One-blue)
![Standard](https://img.shields.io/badge/Standard-NTSC--M-red)

<img width="100%" alt="Banner Proyecto" src="https://github.com/user-attachments/assets/e05b561b-fb34-4922-acbb-b1871a81f200" />

## 📋 Descripción del Proyecto
Este repositorio contiene la documentación y metodología para la implementación de una estación de transmisión de televisión analógica bajo el estándar **NTSC-M**. 

El sistema utiliza un **HackRF One** para el procesamiento digital de señales (DSP) y una etapa de amplificación de RF externa diseñada a medida con el MMIC **ERA-6** para alcanzar una cobertura de 100 metros, superando la limitación de potencia nativa del SDR.

## 🎯 Objetivos
* **General:** Implementar un transmisor de TV Analógica de largo alcance mediante SDR.
* **Específicos:**
    * Generar la señal banda base (Video + Audio) con `hacktv`.
    * Diseñar un amplificador RF lineal (MMIC ERA-6) con acople Bias Tee.
    * Validar la recepción en televisores comerciales en banda UHF.

## 🛠️ Tecnologías y Hardware

| Categoría | Detalle |
| :--- | :--- |
| **SDR** | HackRF One (Half-duplex, 1MHz - 6GHz) |
| **Amplificador** | Mini-Circuits ERA-6+ (MMIC) |
| **Software** | HackTV (Modulación), Linux (Debian/Kali) |
| **Antena** | [Tipo de Antena, ej: Dipolo de media onda] sintonizada a [Frecuencia] MHz |
| **Impedancia** | 50 $\Omega$ (Microstrip + SMA) |

## 🚀 Guía de Instalación y Uso

### 1. Prerrequisitos
Este proyecto requiere un entorno Linux. Se utilizaron las siguientes librerías:

```bash
sudo apt-get update
sudo apt-get install hackrf libhackrf-dev
# Instrucciones para instalar hacktv (ejemplo):
git clone [https://github.com/fsphil/hacktv.git](https://github.com/fsphil/hacktv.git)
cd hacktv
make
sudo make install
