**Propuestas para “IDM\_CASO\_1\_resolucion.pdf”**

 

**pág.5**

**Los duplicados se detectan a través de la clave compuesta (código de país, número de pasaporte), que garantiza unicidad global. El número de pasaporte es único única mente dentro de un mismo país, por lo que su combinación con el código de país resulta indispensable en un contexto internacional. El correo electrónico se emplea exclusiva mente como dato de contacto, dado que los huéspedes pueden modificarlo o compartirlo entre miembros de una familia.**

En la práctica puede haber huéspedes sin pasaporte, pasaportes vencidos, errores de carga o cambios de documento. Yo cambiaría la afirmación de que la clave (país, pasaporte) “garantiza unicidad global”. Mejor decir que se construye un **guest\_id** canónico usando reglas de vinculación de registros: país + documento, email, teléfono, fecha de nacimiento, nombre normalizado

** **

**pág 7**

**No todos los datos disponibles resultan relevantes para cada problema; esta etapa permite reducir la dimensionalidad y eliminar el ruido irrelevante.**

Yo no usaría la palabra “ruido” ya que eso lo usamos en el paso anterior: Limpieza de Datos (Data Cleaning)

 

**Se excluyen los registros de huéspedes con estadía de una única noche, dado que el tiempo disponible es insuficiente para el aprendizaje de preferencias.**

 

En selección de datos, revisaría la decisión de excluir huéspedes con estadía de una sola noche. Para aprender hábitos durante la estadía puede tener sentido, pero para mailing futuro o para evaluar conversiones rápidas no necesariamente. Mejor no descartarlos por completo: crear una variable estadia\_corta = 1 y tratarlos como un segmento especial. Así no se pierde información potencialmente útil.

 

**pág 8**

|                                      |                                                          |                                                       |
| ------------------------------------ | -------------------------------------------------------- | ----------------------------------------------------- |
| **Atributo original**                | **Transformacion**                                       | **Atributo resultante**                               |
| **Registros de acceso por servicio** | **Agregación como frecuencia de uso por día de estadía** | **visitas\_gimnasio/día, visitas\_piscina/día, etc.** |

** **

Si en vez de usar el registro de acceso usamos el tiempo en el que estuvo en cada lugar, sería mejor. Esto si tenemos también el registro de egreso. Ya que, por ejemplo, uno puede entrar una vez al gimnasio y estar un minuto o estar dos horas. Suponiendo que tenemos esos dos registros (el de ingreso, y el de egreso) haría un promedio de tiempo por día en los servicios.

|                                           |                                             |                                                   |
| ----------------------------------------- | ------------------------------------------- | ------------------------------------------------- |
| Atributo original                         | Transformacion                              | Atributo resultante                               |
| Registros de acceso y egreso por servicio | Promedio de tiempo por día en los servicios | visitas\_gimnasio/día, visitas\_piscina/día, etc. |

** **

** **

**pág 11**

**Al momento de la llegada, el huésped no dispone de historial conductual en la estadía actual. Solo se cuenta con los datos demográficos relevados en el check-in y las respuestas al cuestionario inicial. Este subproblema responde al requerimiento explícito del caso de ofrecer una sugerencia razonable durante los primeros días, cuando el sistema dispone de escasas oportunidades de aprender los hábitos del huésped.**

Creo que en este punto convendría separar entre “huésped nuevo” y “huésped recurrente”. Ya que si bien ninguno dispone del historial conductual actual. Sí disponemos del historial conductual pasado de los “héspedes recurrentes”.

Huésped nuevo en la cadena: sólo se dispone de datos demográficos, cuestionario inicial, tipo de viaje, hotel actual y duración esperada de la estadía.

Huésped recurrente: aunque no haya datos de la estadía actual, sí se puede usar el historial previo en otros hoteles de la cadena: servicios usados, compras, evaluaciones, tipos de hoteles visitados y respuestas pasadas a promociones.

** **
