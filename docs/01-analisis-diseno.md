# Analisis y diseño

## 1. Descripción del problema
El sistema que se va a representar es un invernadero inteligente que contara con 3 sensores, los cuales medirán diferentes variables, las que son temperatura del aire, humedad ambiental y humedad del suelo, que con base en la información recabada indicaran y tomaran una decisión automatica, como activar o desactivar un sistema de riego en caso de ser necesario.

---

## 2. Identificación de objetos
- **Sensor (Superclase):** El sensor se toma como objeto. Contiene características y comportamientos que se pueden asignar (id, ubicación, estado y última medición). Donde se derivaran 3 sensores (subclases) especiales que son:
  - Sensor de humedad ambiental
  - Sensor de humedad del suelo
  - Sensor de temperatura
- **Sistema de riego:** Representa el mecanismo que regara las plantas, que se activara con base en la medición del sensor de humedad del suelo

---

## 3. Estado y comportamiento
| Objeto propuesto   | Responsabilidad                                                                                                                                                                    | Información que debe conservar                                             | Comportamientos que debe realizar                                |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|------------------------------------------------------------------|
| Sensor(Superclase) | Ser la super clase que definira los atributos para las subclases                                                                                                                   | identificador, ubicación, estado actual, ultima medición                   | Permitir consultar su estado, actualizar su medición y evaluar su valor. |
| SensorTemperatura  | Medir la temperatura ambiente del invernadero en grados °C en un rango de adecuado de entre 18°C - 30°C                                                                            | Heredara los atributos del objeto Sensor                                   | Permitir consultar su estado, actualizar su medición y evaluar su valor. |
| SensorHumedadSuelo | Indica la cantidad de humedad que hay en suelo que representa la medición en porcentaje que el rango adecuado es de 30% - 70%                                                      | Heredara los atributos del objeto Sensor                                   | Permitir consultar su estado, actualizar su medición y evaluar su valor. |
| SensorHumedad      | Indica la canitdad de humedad que hay en el aire, la medición se representa en porcentaje donde el rando adecuado es de 40% - 70%                                                  | Heredara los atributos del objeto Sensor                                   | Permitir consultar su estado, actualizar su medición y evaluar su valor. |
| SistemaRiego       | Su responsabilidad es regar las plantas, para ello se relaciona con el Sensor de humedad de suelo, el cual el sensor le mandara la ccion a realizar que son dos: activo o inactivo | Estado actual del sistema (activo o inactivo).                             | Activar el riego, desactivar el riego y consultar si está funcionando.   |

---

## 4. Características comunes y especialización
1. ¿Qué información tienen en común?
    - Todos los sensores tienen en común atributo básico para identificarse y registras datos. 
2. ¿Qué comportamientos tienen en común?
    - Todos los sensores deben actualizar o registrar una medición, cambiar de estado y permitir que se consulte su información.
3. ¿Qué características cambian dependiendo del tipo de sensor?
    - Cambia la unidad de medida (grados Celsius para la temperatura, porcentajes para las humedades) y los parámetros de interpretación.
4. ¿Existe un concepto general que permita representar a todos los sensores?
    - Sí, el concepto general de "Sensor".
5. ¿Qué elementos podrían representar especializaciones de ese concepto?
    - Sensor de temperatura, sensor de humedad ambiental y sensor de humedad del suelo.
   
## 5. Relaciones entre objetos
- Un sensor de temperatura es un sensor
- Un sensor de humedad es un sensor
- El sistema de riego utiliza la información proporcionada por el sensor de humedad del suelo
>¿Por qué SistemaRiego no debería ser una subclase de Sensor?
> 
> El sistema de riego no es un sensor, ya que su responsabilidad es suministrar o detener el agua para las plantas y no medir alguna varable como lo hacen los sensores
