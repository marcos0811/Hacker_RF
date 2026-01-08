# Transmisor de TV Analógica NTSC definido por Software (SDR) con Etapa de Potencia RF

**Universidad de Cuenca - Facultad de Ingeniería** **Asignatura:** Circuitos de Radiofrecuencia  
**Período:** Septiembre 2024 - Febrero 2025

![Status](https://img.shields.io/badge/Estado-Finalizado-success?style=flat-square)
![SDR](https://img.shields.io/badge/Hardware-HackRF_One-blue?style=flat-square)
![Amplificador](https://img.shields.io/badge/Amp-MMIC_ERA--6-orange?style=flat-square)
![Standard](https://img.shields.io/badge/Normativa-NTSC--M-red?style=flat-square)

<div align="center">
  <img width="100%" src="https://github.com/user-attachments/assets/e05b561b-fb34-4922-acbb-b1871a81f200" alt="Banner del Proyecto">
</div>

---

## 📋 Descripción del Proyecto
Este repositorio documenta la implementación exitosa de una estación transmisora de televisión analógica (Estándar **NTSC-M**) operativa en la banda UHF.

El sistema combina el procesamiento digital de señales (DSP) mediante un **HackRF One** con una etapa de potencia de RF personalizada. El objetivo principal fue superar la limitación de potencia de salida del SDR (aprox. -10 dBm) integrando un amplificador **MMIC ERA-6**, logrando así una cobertura efectiva de **100 metros** con recepción clara en televisores comerciales.

## 🎯 Objetivos
* **General:** Implementar un transmisor de TV Analógica de largo alcance mediante SDR y amplificación externa.
* **Específicos:**
    1. Generar la señal banda base (Video + Audio + Croma) utilizando `hacktv`.
    2. Diseñar un amplificador RF lineal con el chip **MMIC ERA-6** y acople Bias Tee.
    3. Validar la recepción de imagen y audio en televisores comerciales.

## ⚙️ Arquitectura del Sistema

El flujo de señal viaja desde la generación digital hasta la radiación por antena:

``mermaid
graph LR
    A[PC: Archivo de Video] -->|USB 2.0| B(SDR: HackRF One)
    B -->|Señal NTSC Débil| C{Bias Tee}
    C -->|Alimentación DC| D[Amp: MMIC ERA-6]
    D -->|RF Amplificada +8dB| E[Antena UHF]
    E -.- link -->|Canal Analógico| F[TV Receptor]
    style D fill:#f96,stroke:#333,stroke-width:2px
🛠️ Especificaciones TécnicasParámetroValor / DescripciónSoftware SDRhacktv (Fork de fsphil)Frecuencia CentralConfigurable (Banda UHF, ej: 471.25 MHz)Ancho de Banda6 MHz (Filtro VSB Digital)Sample Rate16 - 20 MspsAmplificadorMini-Circuits ERA-6SM+ (DC-4 GHz)Ganancia Amp~12 dB típica (medida real: 6-8 dB de ganancia neta)Impedancia50 $\Omega$ (Microstrip + SMA)🚀 Puesta en Marcha1. Instalación de DependenciasSe requiere un entorno Linux (Ubuntu/Debian/Kali).Bashsudo apt update
sudo apt install hackrf libhackrf-dev fftw3-dev
# Clonar y compilar hacktv
git clone [https://github.com/fsphil/hacktv.git](https://github.com/fsphil/hacktv.git)
cd hacktv
make
sudo make install
2. Comando de TransmisiónPara transmitir un video MP4 en el canal deseado:Bash# Ejemplo para Canal 14 UHF (471.25 MHz)
hacktv -f 471250000 -g 40 -s 20000000 input_video.mp4
Nota: El parámetro -g 40 ajusta la ganancia interna del amplificador IF del HackRF.📸 Galería de EvidenciasLas pruebas demostraron que la etapa de amplificación es crítica para lograr estabilidad a más de 2 metros.Montaje y PruebasRecepción Exitosa (100m)<img src="https://github.com/user-attachments/assets/d06c0bf1-849b-4561-a835-39be2a2817af" width="400">Aquí puedes agregar otra foto si tienesIzquierda: Configuración con HackRF. Derecha: TV recibiendo la señal.Detalle de la recepción.🧪 Análisis de ResultadosPotencia: La integración del Bias Tee y el MMIC ERA-6 elevó la señal permitiendo vencer el piso de ruido en el trayecto de 100m.Calidad de Imagen: El uso de SDR elimina el "drift" (deriva) de frecuencia típica de los transmisores analógicos antiguos. La croma (color) se mantuvo estable.Espectro: Se verificó mediante FFT que la señal respeta la máscara espectral de 6 MHz, con portadoras de audio y video separadas correctamente por 4.5 MHz.👥 AutoresTrabajo realizado por estudiantes de la Universidad de Cuenca:Eddison Paúl Espadero Morales - Correo InstitucionalMarcos Josue Japa Maza - Correo InstitucionalDavid Fernando Seraquive Tene - Correo InstitucionalLuis Enrique Quirindumbay Ochoa - Correo InstitucionalFrancis Xavier Leon Leon - Correo InstitucionalPresentado en el YACHANA DAY 2026 - Ingeniería en Telecomunicaciones
