# Real Time Data Manager

Este proyecto consta de tres archivos en Python que simulan la generación de datos en tiempo real y la notificación de eventos. A continuación se proporciona una breve descripción de cada archivo:

## `datamanager.py`

### `RealTimeDataManager` Clase:
- **`__init__`:** Inicializa la instancia con valores iniciales de temperatura y humedad, así como una instancia del `EventManager`.
- **`start_real_time_updates`:** Inicia un bucle infinito que espera 3 segundos, genera datos de temperatura y humedad de forma aleatoria, y notifica a los suscriptores (registrados en el `EventManager`) que los datos se han actualizado.
- **`generate_real_time_data`:** Genera datos aleatorios simulando cambios en temperatura y humedad.

## `eventos.py`

### `EventManager` Clase:
- **`__init__`:** Inicializa un diccionario para almacenar a los suscriptores.
- **`subscribe`:** Suscribe un callback a un evento particular.
- **`unsubscribe`:** Cancela la suscripción del callback al evento.
- **`notify`:** Notifica a todos los suscriptores del evento con los datos indicados.

## `simulacion.py`

### Script Principal:
- **`callback_imprimir_datos`:** Un simple callback que imprime los datos actualizados.
- **`if __name__ == "__main__":`**
  - Crea una instancia de `RealTimeDataManager` y un `EventManager`.
  - Suscribe el callback a la actualización de datos.
  - Crea un hilo para ejecutar la generación de datos.
  - Configura el hilo como demonio para que el programa se cierre al ingresar Ctrl + C.
  - Inicia el hilo.
  - Ejecuta el programa hasta que se ingrese Ctrl + C, momento en el que imprime "Programa terminado."

## Ejemplo de salida del programa:

Supongamos que ejecutas `simulacion.py`. La salida del programa podría verse así:

