# Optimización de Redes WiFi con Deep Q-Network (DQN)

**Autores:** Jarod Tierra y Andrés Vega  
**NRC:** 3710

Este repositorio contiene el proyecto final para el curso de Redes, enfocado en la **Optimización Adaptativa de Redes WiFi mediante Reinforcement Learning (RL)**.

![Training Results](https://github.com/ELVEGA771/Optimizaci-n-de-redes-WiFi-con-Deep-Q-Network-DQN-/blob/main/output_images/training_results.png?raw=true)
*(Nota: Las imágenes de resultados se generarán al ejecutar el notebook)*

## 📋 Descripción

El objetivo de este proyecto es utilizar un agente de **Deep Reinforcement Learning (DQN)** para optimizar dinámicamente los parámetros de una red WiFi (canales y potencia de transmisión) en un entorno simulado. 

A diferencia de los simuladores comerciales complejos como NS-3, este proyecto implementa un **simulador WiFi customizado en Python** que modela aspectos clave de la red como:
- Interferencia co-canal y de canal adyacente.
- Pérdida de propagación (Path Loss).
- Cálculo de RSSI, Throughput, Latencia y Pérdida de Paquetes.
- Dinamismo en la demanda de tráfico de los usuarios y ruido externo.

El agente aprende a maximizar una **función de recompensa multi-objetivo** que balancea throughput, latencia, equidad (fairness) y eficiencia energética.

## 🚀 Características Principales

*   **Entorno WiFi Simulado**: Un entorno compatible con la interfaz `Gym` que simula múltiples Access Points (APs) y usuarios en un área definida.
*   **Agente DQN**: Implementación de un agente Deep Q-Network con:
    *   **Experience Replay**: Para romper la correlación entre muestras consecutivas.
    *   **Target Network**: Para estabilizar el entrenamiento.
    *   **Epsilon-Greedy**: Estrategia de exploración/explotación con decaimiento.
*   **Recompensa Multi-Objetivo**: Función de recompensa sofisticada que considera:
    *   ⬆️ Maximización del Throughput total.
    *   ⬇️ Minimización de Latencia y Packet Loss.
    *   📶 Calidad de Señal (RSSI).
    *   ⚖️ Equidad entre usuarios (Jain's Fairness Index).
    *   🔋 Eficiencia energética (penalización por potencia máxima innecesaria).
    *   🔄 Estabilidad (penalización por cambios frecuentes de configuración).
*   **Escenarios de Prueba**: Configuraciones predefinidas para Baja, Media y Alta congestión.
*   **Baselines de Comparación**: Comparación del agente DQN contra estrategias estáticas, aleatorias y greedy.

## 🛠️ Requisitos e Instalación

El proyecto está autocontenido en un Jupyter Notebook. Para ejecutarlo, necesitas las siguientes librerías de Python:

```bash
pip install tensorflow numpy matplotlib seaborn pandas scikit-learn pyyaml tqdm
```

### Tecnologías Usadas
*   **Python 3.x**
*   **TensorFlow / Keras**: Para la red neuronal del agente.
*   **NumPy & Pandas**: Procesamiento de datos y simulación numérica.
*   **Matplotlib & Seaborn**: Visualización de métricas y resultados.

##  ▶️ Cómo Ejecutar

1.  Clona este repositorio:
    ```bash
    git clone https://github.com/ELVEGA771/Optimizaci-n-de-redes-WiFi-con-Deep-Q-Network-DQN-.git
    cd Optimizaci-n-de-redes-WiFi-con-Deep-Q-Network-DQN-
    ```
2.  Instala las dependencias listadas arriba.
3.  Abre el archivo `Proyecto_final.ipynb` en Jupyter Notebook, JupyterLab o Google Colab.
4.  Ejecuta todas las celdas secuencialmente para:
    *   Inicializar el simulador.
    *   Entrenar el agente DQN.
    *   Visualizar las curvas de aprendizaje.
    *   Comparar los resultados con los baselines.
    *   Ejecutar pruebas de estrés.

## 📂 Estructura del Proyecto

El notebook `Proyecto_final.ipynb` está organizado en las siguientes secciones:

1.  **Setup e Instalación**: Importación de librerías.
2.  **Implementación del Entorno WiFi**: Clases `AccessPoint`, `User`, `WiFiSimulator` y `WiFiEnvironment`.
3.  **Implementación del Agente DQN**: Clases `DQNNetwork` (Modelo Keras), `ReplayBuffer` y `DQNAgent`.
4.  **Función de Recompensa Multi-Objetivo**: Definición de componentes de recompensa y penalizaciones.
5.  **Entrenamiento del Modelo**: Loop principal de entrenamiento con validación periódica.
6.  **Evaluación y Comparación con Baselines**: Comparativa de rendimiento vs métodos tradicionales.
7.  **Análisis de Resultados**: Gráficos de evolución de métricas (Throughput, Latencia, Reward).
8.  **Simulación de Estrés**: Evaluación del agente bajo condiciones extremas cambiantes.

## 📊 Resultados Esperados

El entrenamiento demuestra que el agente DQN es capaz de converger a una política que supera a las estrategias aleatorias y estáticas, adaptándose dinámicamente a las condiciones de interferencia y tráfico.

*   **Mejora de Throughput**: El agente aprende a seleccionar canales menos congestionados.
*   **Gestión de Potencia**: Ajusta la potencia para mantener cobertura sin causar interferencia excesiva.
*   **Adaptabilidad**: En las pruebas de estrés, el agente recupera el rendimiento ante cambios bruscos en el entorno.

---
*Este proyecto fue desarrollado como parte de la evaluación final de la materia de Redes Teoria.*
