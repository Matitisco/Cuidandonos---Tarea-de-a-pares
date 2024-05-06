# Cuidandonos: Tarea-de-a-pares

# Alumnos

- Matías José Tiscornia
- Pablo Joaquín Borquez Belli


# Justificaciones
---------------

**Modelado Persona:**  
Le definimos los atributos solicitados, decidimos normalizar la Dirección implementando una clase para la misma que tenga: `direccion: String` y `altura: Integer`. La misma se utiliza en Parada.

**Modelado Viaje:**  
Decidimos agregar "origen" y "destino" ya que para poder `calcularDistancia` los necesitamos, además que es coherente que esos datos se persistan dentro de Viaje.

*   Le agregamos 2 listas, "cuidadoresPropuestos" y "cuidadoresSeleccionados" para poder llevar un control de los cuidadores que se le proponen al usuario y los que acepta.
*   También el usuario que solicita el Viaje mismo, `reaccionIncidente` del usuario, una lista de Paradas (puede estar vacía tranquilamente), si `seDetiene`, ligado a las paradas y `estadoViaje` para abstraer algunas funcionalidades que dependerán del estado del mismo.

PATRONES:
---------

1.  Utilizamos el **PATRON STATE** en Persona para indicar si es una Persona Activa (cuidador) o Pasiva. Cabe resaltar que un usuario puede cumplir tanto el rol de Cuidador como Transeúnte por lo que aplicar herencia no sería válido en este caso. La diferencia entre ambos estados es que en el pasivo, `asignacionViaje()` implica solicitar un cuidador, mientras que si es activo debe aceptar la solicitud de viaje.
    
2.  Decidimos usar el **PATRON ADAPTER** para abstraer la funcionalidad de `calcularDistancia`, de la API "Distancia Matrix" y así integrar la misma con el sistema y buscando evitar el rozamiento con el resto del sistema. De esta forma ganamos desacoplamiento de terceros
    
3.  También aplicamos el **PATRON STATE** para la `reaccionIncidente` y así poder tener un cambio de comportamiento dependiendo de la reacción que sea definida por el usuario, esto también nos permitiría agregar nuevas reacciones sin muchos cambios en el código de Viaje.
    
4.  Para la reacción de "EnviarAlertaCuidadores" decidimos usar el **PATRON ADAPTER**, para implementar las notificaciones, le definimos `notificar(mensaje: String, destinatario: String)` y no usando por ejemplo un `mensaje: Mensaje`, normalizado, para que el Adapter sea independiente de nuestro sistema y generar una alta cohesion.
    
5.  Por último, usamos el **PATRON STATE** para los estados del viaje, de forma tal que podamos abstraer las funcionalidades del viaje que dependen de la instancia del mismo, ya sea que este recién Creado, enTranscurso, enPeligro o Finalizado.

