# Simulador de datos en tiempo real

Este programa en Python simula la generación de datos en tiempo real y notifica a los suscriptores cuando los datos están actualizados. Está conformado por lo siguiente tres archivos:

## datamanager.py

### RealTimeDataManager class:

- **Constructor (`__init__`):**
  - Inicializa el objeto `RealTimeDataManager` con datos iniciales de temperatura y humedad.
  - Crea una instancia de `EventManager` llamada `self.event_manager`.

- **`start_real_time_updates` method:**
  - Bucle infinito que espera 3 segundos y luego genera datos en tiempo real llamando a `generate_real_time_data` y notifica a los suscriptores utilizando `self.event_manager.notify`.

- **`generate_real_time_data` method:**
  - Modifica los valores de temperatura y humedad de manera aleatoria para simular cambios en los datos en tiempo real.

## eventos.py

### `EventManager` class:

- **Constructor (`__init__`):**
  - Inicializa el objeto `EventManager` con un diccionario que almacenará los eventos y sus respectivos suscriptores.

- **`subscribe` method:**
  - Permite a un suscriptor registrarse para un evento específico. Si el evento no existe, se crea una lista vacía.

- **`unsubscribe` method:**
  - Permite a un suscriptor anular su suscripción a un evento específico.

- **`notify` method:**
  - Notifica a todos los suscriptores registrados para un evento específico llamando a sus callbacks con los datos proporcionados.

## simulacion.py

- **`callback_imprimir_datos` function:**
  - Una función simple que imprime los datos en tiempo real actualizados.

- **Código principal:**
  - Crea una instancia de `RealTimeDataManager`.
  - Suscribe la función `callback_imprimir_datos` al evento "datos_actualizados".
  - Crea un hilo para ejecutar el método `start_real_time_updates`.
  - Establece el hilo como demonio para cerrar el programa completamente al recibir una interrupción de teclado.
  - Inicia el hilo.
  - Bucle infinito para mantener el programa en ejecución hasta que se recibe una interrupción de teclado, luego maneja la interrupción e imprime un mensaje de cierre.

---

**Instrucciones de uso:**

1. Ejecuta `simulacion.py` para iniciar la simulación.
2. El programa generará datos en tiempo real y notificará a los suscriptores.

**Nota:** Puedes personalizar los eventos y suscriptores según tus necesidades.

# Ejemplo de Salida del Programa

## Resultados de la Simulación

Ejecutar el programa `simulacion.py` podría producir una salida similar a la siguiente:

Datos en tiempo real actualizados: {'temperatura': 24.8144788325153, 'humedad': 59.22656452432036}
Datos en tiempo real actualizados: {'temperatura': 25.695321492733867, 'humedad': 61.59471649132475}
Datos en tiempo real actualizados: {'temperatura': 24.85648409627055, 'humedad': 60.57975982047561}


## Comentarios sobre los Resultados

- Cada línea representa una actualización de datos en tiempo real.
- Los valores de temperatura y humedad se generan aleatoriamente y cambian en cada actualización.
- Los datos actualizados se imprimen con el formato `{'temperatura': valor, 'humedad': valor}`.
- La simulación continua hasta que se interrumpe con `Ctrl + C`.

**Nota:** Los valores exactos pueden variar en cada ejecución debido a la naturaleza aleatoria de la generación de datos.

# Calculadora Simple en Python

Este es un programa simple de calculadora implementado en Python. Permite al usuario realizar operaciones básicas como suma, resta, multiplicación y división.

## Estructura del Programa

### Función `get_user_input`

Esta función se encarga de obtener la entrada del usuario. Utiliza un bloque `try-except` para manejar errores en caso de que el usuario ingrese algo que no sea un número. Pide al usuario que ingrese dos números y la operación que desea realizar (+, -, *, /), o puede escribir 'exit' para salir. Si se produce un error de valor al intentar convertir la entrada a `float`, imprime un mensaje de error y solicita la entrada nuevamente mediante una llamada recursiva a la misma función.

### Función `ejecutar_operacion`

Toma la entrada del usuario y una función de callback como argumentos. Llama a la función de callback con los dos números ingresados por el usuario y muestra el resultado.

### Función `main`

Define funciones lambda para realizar las operaciones de suma, resta, multiplicación y división. Crea un diccionario llamado `operations` que mapea los operadores (+, -, *, /) a las funciones lambda correspondientes. Utiliza un bucle infinito (`while True`) para solicitar continuamente la entrada del usuario y realizar operaciones. Dentro del bucle, obtiene la entrada del usuario llamando a `get_user_input`. Verifica si el usuario quiere salir. Si el operador ingresado es 'exit', imprime un mensaje y sale del bucle. Si el operador está en el diccionario `operations`, llama a la función `ejecutar_operacion` con la entrada del usuario y la función lambda correspondiente. Si el operador no está en el diccionario, imprime un mensaje de "Operación inválida".

### Llamada a `main` en el bloque `if __name__ == "__main__":`

Garantiza que la función `main` se ejecute solo si el script se ejecuta directamente y no se importa como un módulo en otro script.

## Flujo del Programa

1. **Inicio del Programa:**
   - El programa comienza ejecutando la función `main`.
   - Se definen las funciones lambda para realizar las operaciones y se crea el diccionario `operations`.

2. **Bucle Principal:**
   - El programa entra en un bucle infinito (`while True`) donde solicita la entrada del usuario y realiza operaciones.

3. **Entrada del Usuario:**
   - El usuario ingresa dos números y elige una operación.

4. **Verificación y Ejecución:**
   - Se verifica si el usuario desea salir. Si es así, el programa imprime un mensaje y sale del bucle.
   - Si la operación seleccionada está en el diccionario, se ejecuta la operación correspondiente llamando a la función `ejecutar_operacion`.
   - Si la operación no es válida, se imprime un mensaje de error.

5. **Repetición:**
   - El bucle continúa solicitando la entrada del usuario hasta que decide salir.

Espero que esta explicación te ayude a entender cómo funciona el programa. Si tienes alguna pregunta específica o si hay algo en particular que te gustaría saber más, ¡no dudes en preguntar!

# Calculadora Simple en Python

Este es un programa simple de calculadora implementado en Python. Permite al usuario realizar operaciones básicas como suma, resta, multiplicación y división.

## Ejemplo de Salida

Ingrese un numero: 10
Ingrese otro numero: 5
Elija una operacion (+, -, *, /) o escriba 'exit' para salir: +

Calculando...
Resultado: 15.0

Ingrese un numero: 8
Ingrese otro numero: 2
Elija una operacion (+, -, *, /) o escriba 'exit' para salir: *

Calculando...
Resultado: 16.0

Ingrese un numero: 12
Ingrese otro numero: 0
Elija una operacion (+, -, *, /) o escriba 'exit' para salir: /

Calculando...
Resultado: Error: División entre cero

Ingrese un numero: abc
Input invalido. Por favor ingrese numeros.
Ingrese un numero: 4
Ingrese otro numero: 3
Elija una operacion (+, -, *, /) o escriba 'exit' para salir: -

Calculando...
Resultado: 1.0

Ingrese un numero: 6
Ingrese otro numero: 0
Elija una operacion (+, -, *, /) o escriba 'exit' para salir: /

Calculando...
Resultado: Error: División entre cero

Ingrese un numero: exit
Salir.


## Comentarios sobre el Ejemplo

- **Suma (Operación `+`):** El usuario ingresó 10 y 5, y eligió la suma. El resultado es 15.
- **Multiplicación (Operación `*`):** El usuario ingresó 8 y 2, y eligió la multiplicación. El resultado es 16.
- **División entre Cero (Operación `/`):** El usuario intentó dividir 12 por 0, lo cual resulta en un mensaje de error.
- **Resta (Operación `-`):** El usuario ingresó 4 y 3, y eligió la resta. El resultado es 1.
- **División entre Cero (Operación `/`):** Nuevamente, el usuario intentó dividir, pero esta vez por 0, y recibe un mensaje de error.
- **Salir (`exit`):** El usuario ingresó "exit", lo que termina el programa.
