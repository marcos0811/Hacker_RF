# 📡 Transmisor de TV Analógica NTSC definido por Software (SDR) con Etapa de Potencia RF

**Universidad de Cuenca – Facultad de Ingeniería**  
**Asignatura:** Circuitos de Radiofrecuencia  
**Período:** Septiembre 2024 – Febrero 2025  

![Status](https://img.shields.io/badge/Estado-Finalizado-success?style=flat-square)
![SDR](https://img.shields.io/badge/Hardware-HackRF_One-blue?style=flat-square)
![Amplificador](https://img.shields.io/badge/Amp-MMIC_ERA--6-orange?style=flat-square)
![Normativa](https://img.shields.io/badge/Normativa-NTSC--M-red?style=flat-square)

<div align="center">
  <img width="100%" src="https://github.com/user-attachments/assets/e05b561b-fb34-4922-acbb-b1871a81f200" alt="Banner del Proyecto">
</div>

---

## 📋 Descripción del Proyecto

Este repositorio documenta la implementación de una estación transmisora de televisión analógica **NTSC-M** en la banda **UHF**.

El sistema utiliza un **HackRF One** como plataforma de **Radio Definida por Software (SDR)** y una etapa de potencia de RF personalizada.  
El objetivo fue superar la baja potencia de salida del SDR (≈ −10 dBm) mediante la integración de un amplificador **MMIC ERA-6**, logrando una cobertura aproximada de **100 metros**, visible en televisores analógicos comerciales.

---

## 🎯 Objetivos

### Objetivo General
- Implementar un transmisor de televisión analógica de mayor alcance mediante SDR.

### Objetivos Específicos
1. Generar la señal de banda base (video + audio) usando `hacktv`.
2. Diseñar un amplificador RF lineal con **MMIC ERA-6** y acople mediante **Bias Tee**.
3. Validar la recepción de imagen y audio en televisores comerciales.

---

## ⚙️ Arquitectura del Sistema

```mermaid
graph LR
    A[PC: Archivo de Video] -->|USB 2.0| B[SDR: HackRF One]
    B -->|Señal NTSC Débil| C[Bias Tee]
    C -->|Alimentación DC| D[Amp: MMIC ERA-6]
    D -->|RF Amplificada| E[Antena UHF]
    E -.->|Canal Analógico| F[TV Receptor]

    style D fill:#f96,stroke:#333,stroke-width:2px
```

---

## 🛠️ Especificaciones Técnicas

| Parámetro           | Valor / Descripción |
|--------------------|---------------------|
| Software SDR        | hacktv (fork de fsphil) |
| Frecuencia          | Banda UHF (ej. 471.25 MHz) |
| Ancho de Banda      | 6 MHz (NTSC-M VSB) |
| Sample Rate         | 16 – 20 Msps |
| Amplificador        | Mini-Circuits ERA-6SM+ |
| Ganancia            | ~12 dB típica (6–8 dB neta medida) |
| Impedancia          | 50 Ω (microstrip + SMA) |

---

## 📸 Evidencia Experimental

### Montaje Experimental
<img src="https://github.com/user-attachments/assets/d06c0bf1-849b-4561-a835-39be2a2817af" width="100%">

### Recepción Exitosa (~100 m)
- Configuración: HackRF + Bias Tee + Amplificador RF
- Recepción en TV analógica comercial

---

## 🧪 Análisis de Resultados

- **Potencia:** La etapa con MMIC ERA-6 permitió vencer el piso de ruido del enlace a 100 m.
- **Calidad:** El uso de SDR eliminó la deriva de frecuencia; la croma se mantuvo estable.
- **Espectro:** Mediante FFT se verificó el cumplimiento de la máscara de 6 MHz NTSC.

---

## 👥 Autores

**Universidad de Cuenca – Ingeniería en Telecomunicaciones**

- Eddison Paúl Espadero Morales – eddison.espadero@ucuenca.edu.ec  
- Marcos Josué Japa Maza – marcos.japa@ucuenca.edu.ec  
- David Fernando Seraquive Tene – david.seraquive@ucuenca.edu.ec  
- Luis Enrique Quirindumbay Ochoa – luis.quirindumbay@ucuenca.edu.ec  
- Francis Xavier León León – francis.leon@ucuenca.edu.ec  

---

## ⚠️ Advertencia Legal

Este proyecto fue desarrollado **exclusivamente con fines académicos y experimentales**.  
La transmisión de señales de TV en banda UHF puede estar regulada por entidades gubernamentales.  
Asegúrese de cumplir la normativa local antes de realizar transmisiones RF.

---

📌 **Presentado en el YACHANA DAY 2026**
