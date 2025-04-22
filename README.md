# HMM - Hidden Markov Models
##### Michelle Mejía y Silvia Illescas

Este proyecto implementa un Modelo Oculto de Markov (HMM) utilizando el algoritmo Forward-Backward. El HMM es un modelo probabilístico utilizado para modelar sistemas donde el estado no es observable, pero las observaciones relacionadas con el estado son observables.

## Tabla de contenidos

- [Instalación](#instalación)
- [Uso](#uso)
- [Funciones principales](#funciones-principales)
- [Ejemplo de uso](#ejemplo-de-uso)
- [Licencia](#licencia)

## Instalación

### Requisitos previos

Para ejecutar este proyecto, necesitas tener Python 3.x instalado. Además, el código usa la librería **NumPy**. Si no tienes NumPy, instálalo utilizando `pip`:

```bash
pip install numpy
```

## Uso

1. Clona este repositorio en tu máquina local:
    ```bash
    git clone https://github.com/michellemej22596/Lab9-IA.git
    cd Lab9-IA
    ```

2. Ejecuta el script de `hmm` insertado en el notebook para utilizar la clase HMM y realizar las predicciones sobre secuencias de observaciones.

3. El código generará una secuencia de observaciones y luego calculará las probabilidades forward y backward, además de las probabilidades de estado en cada momento de tiempo.

## Funciones principales

### 1. **`__init__()`**

Inicializa el modelo HMM con los parámetros necesarios:
- `states`: lista de posibles estados del sistema (por ejemplo, `['Sunny', 'Rainy']`).
- `observations`: lista de posibles observaciones (por ejemplo, `['sunny', 'rainy']`).
- `initial_prob`: diccionario con las probabilidades iniciales de cada estado.
- `transition_prob`: diccionario con las probabilidades de transición entre estados.
- `emission_prob`: diccionario con las probabilidades de emisión para cada estado.

### 2. **`generate_sequence(length)`**

Genera una secuencia de observaciones basada en el modelo HMM. Esta función es útil para generar datos de prueba.

### 3. **`forward(observations)`**

Calcula las probabilidades forward (hacia adelante), es decir, las probabilidades de estar en un estado específico dado una secuencia de observaciones hasta el paso `t`.

### 4. **`backward(observations)`**

Calcula las probabilidades backward (hacia atrás), es decir, las probabilidades de observar la secuencia restante desde un paso de tiempo hasta el final, dado un estado específico en ese tiempo.

### 5. **`compute_state_probabilities(observations)`**

Combina las probabilidades forward y backward para calcular las probabilidades de estar en un estado en cada paso de tiempo, dada una secuencia observada.

## Ejemplo de uso

A continuación se muestra un ejemplo de cómo utilizar el código:

```python
# Definición de parámetros
states = ['Sunny', 'Rainy']
observations = ['sunny', 'rainy']
initial_prob = {'Sunny': 0.6, 'Rainy': 0.4}
transition_prob = {'Sunny': {'Sunny': 0.8, 'Rainy': 0.2}, 'Rainy': {'Sunny': 0.4, 'Rainy': 0.6}}
emission_prob = {'Sunny': {'sunny': 0.9, 'rainy': 0.1}, 'Rainy': {'sunny': 0.2, 'rainy': 0.8}}

# Crear la instancia del modelo HMM
hmm = HMM(states, observations, initial_prob, transition_prob, emission_prob)

# Generar una secuencia de observaciones
obs_sequence = hmm.generate_sequence(5)
print("Secuencia Generada:", obs_sequence)

# Calcular las probabilidades forward
forward_probs = hmm.forward(obs_sequence)
print("Probabilidades Forward:", forward_probs)

# Calcular las probabilidades backward
backward_probs = hmm.backward(obs_sequence)
print("Probabilidades Backward:", backward_probs)

# Calcular las probabilidades de estado
state_probs = hmm.compute_state_probabilities(obs_sequence)
print("Probabilidades de Estados:", state_probs)
```

### Salida esperada:

El código imprimirá las probabilidades de los estados a lo largo de la secuencia observada.

## Licencia

Este proyecto está licenciado bajo la **Licencia MIT**. Para más detalles, revisa el archivo `LICENSE`.