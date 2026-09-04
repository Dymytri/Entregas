¿Qué hace exactamente el bloque let...in en lenguaje M? ¿Por qué cada paso puede referenciar al anterior?
El bloque definie un conjunto de variables intermedias y determina cual va a devolver como resultado final. Cada paso hace referencia al anterior, no trabaja de manera secuencial como otros lenguajes, por eso, cada paso almacena datos sin afectar los pasos anteriores.

¿Por qué M es Case Sensitive y qué consecuencia práctica tiene? Dá un ejemplo de un error que esto puede causar.
M es sensible al uso de mayusculas y minusculas, la diferencia entre poner una u otra significaria el error de todo el codigo.

¿Cuál es la diferencia entre usar Text.Trim y Text.Clean en M?
Text.Trim elimina espacios en blanco al principio y al final de una cadena de texto, mientras que Text.CLean elimina caracteres de control en cualquier parte del texto

¿Por qué filtraste los registros "PRUEBA" después de estandarizar la categoría y no antes?
SI filtraramos los registros antes de estandarizar, deberiamos contemplar todas las variables posibles de "Pureba" que se encuentren presentes en la tabla.
