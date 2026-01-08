# Transmisor de TV Analógica NTSC definido por Software (SDR) con Etapa de Potencia RF

**Universidad de Cuenca - Facultad de Ingeniería** **Curso de Circuitos de Radiofrecuencia** *Septiembre 2024 - Febrero 2025*

![Banner o Foto del Proyecto](ruta_de_tu_imagen_aqui.png) 
## 📋 Descripción del Proyecto
Este proyecto implementa una estación de transmisión de televisión analógica completamente funcional bajo el estándar **NTSC-M**, utilizando tecnología de Radio Definida por Software (SDR). 

El sistema procesa digitalmente señales de video y audio en tiempo real mediante un ordenador y un **HackRF One**. Para superar las limitaciones de potencia nativas del equipo SDR (que solo alcanzan 1 a 3 metros), se diseñó e integró una etapa de amplificación externa basada en el circuito integrado **MMIC ERA-6**, sintonizada para ser recibida por televisores comerciales.

## 🎯 Objetivos

### Objetivo General
Implementar un sistema de transmisión de TV Analógica (NTSC) de largo alcance utilizando modulación digital SDR y una etapa de potencia RF dedicada.

### Objetivos Específicos
* **Generación de Señal:** Generar la señal banda base compuesta (Video + Croma + Audio) utilizando algoritmos de procesamiento digital (`hacktv`) para el estándar NTSC-M.
* **Diseño de Hardware:** Diseñar e implementar un circuito amplificador de RF con el **MMIC ERA-6** y acople de Bias Tee.
* **Validación:** Validar la calidad de imagen y la estabilidad de la transmisión en el canal UHF mediante televisores comerciales.

## 🛠️ Tecnologías y Hardware Utilizado

### Software
* **HackTV:** Software principal para la modulación y generación de la señal NTSC.
* **Entorno Linux:** Sistema operativo base para la ejecución del DSP.

### Hardware
* **SDR:** HackRF One (Transceptor de medio dúplex).
* **Amplificador:** Circuito MMIC ERA-6.
* **Alimentación RF:** Red Bias Tee y líneas de transmisión microstrip de 50 $\Omega$.
* **Antenas:** Monopolo / Dipolo sintonizado a la frecuencia del canal.

## ⚙️ Metodología

El proyecto se desarrolló siguiendo un diseño híbrido (Hardware + Software):

1.  **Procesamiento Digital (DSP):** Codificación por software de video y audio. Generación matemática de subportadoras de Color (3.58 MHz) y Audio (4.5 MHz). Uso de filtros VSB (Banda Lateral Vestigial) para eficiencia espectral.
2.  **Diseño de Hardware RF:** Diseño de etapa de amplificación lineal calculando pistas de transmisión para evitar pérdidas de retorno. Integración del MMIC ERA-6.
3.  **Integración y Pruebas:** La señal digital es convertida y mezclada a la banda UHF mediante el HackRF One. Finalmente, se potencia con una ganancia efectiva de **6 a 10 dB** antes de ser irradiada.

## 📊 Resultados y Discusión

* **Alcance y Potencia:** Se demostró que la potencia nativa del HackRF es insuficiente (-10 dBm aprox). La integración del **MMIC ERA-6** aportó una ganancia lineal de 6 a 8 dB, permitiendo una transmisión estable.
* **Estabilidad de Imagen:** La generación por software eliminó la deriva de frecuencia típica de los osciladores analógicos antiguos, garantizando una imagen sin parpadeos.
* **Eficiencia Espectral:** El uso de filtros VSB digitales en `hacktv` permite una ocupación estricta de 6 MHz, sin invadir canales adyacentes.

## 📸 Evidencia

| Montaje SDR y Amplificador | Recepción en TV Comercial |
|:--------------------------:|:-------------------------:|
| ![SDR Setup](ruta_foto_montaje.png) | ![TV Result](ruta_foto_tv.png) |
## 📝 Conclusiones

1.  La arquitectura SDR permite cambiar de estándar (NTSC/PAL) o frecuencia sin modificar el hardware físico.
2.  La etapa con **ERA-6** es crítica; sin ella, no se logra cobertura real más allá del laboratorio.
3.  La red Bias Tee y las líneas de 50 $\Omega$ permitieron una ganancia lineal sin distorsionar la señal de video (fase/color).
4.  El procesamiento DSP reemplaza circuitos analógicos complejos, garantizando subportadoras de color precisas.

## 👥 Autores

* **Eddison Paúl Espadero Morales** - [eddison.espadero@ucuenca.edu.ec](mailto:eddison.espadero@ucuenca.edu.ec)
* **Marcos Josue Japa Maza** - [marcos.japa@ucuenca.edu.ec](mailto:marcos.japa@ucuenca.edu.ec)
* **David Fernando Seraquive Tene** - [david.seraquive@ucuenca.edu.ec](mailto:david.seraquive@ucuenca.edu.ec)
* **Luis Enrique Quirindumbay Ochoa** - [luis.quirindumbay@ucuenca.edu.ec](mailto:luis.quirindumbay@ucuenca.edu.ec)
* **Francis Xavier Leon Leon** - [francis.leon@ucuenca.edu.ec](mailto:francis.leon@ucuenca.edu.ec)

---
*Proyecto presentado en el YACHANA DAY 2026.*
