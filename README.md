# reto_2
Elija un problema de la vida real (sistema de gestión de biblioteca, negocio de compra-venta, automóvil, etc) que se pueda modelar a través de objetos y clases. Plantee las relaciones de clases, composiciones, propiedades y comportamientos del sistema en uno mas diagramas tipo UML.
## Problema a analizar
Para desarrollar este reto, decidí modelar un sistema de gestión para un parqueadero. A continuación, presento el diagrama de clases correspondiente, que refleja las relaciones entre las distintas clases.
```mermaid
classDiagram
    class Parqueadero {
        + Str nombre
        + Str direccion
        + Int capacidadTotal
        + Int espaciosDisponibles
        + registrarIngresoVehiculo(Vehiculo)
        + registrarSalidaVehiculo(Vehiculo)
        + obtenerEspaciosDisponibles()
    }
    class EspacioParqueo {
        + Int numero
        + Bool estado
        + Vehiculo vehiculo
        + asignarVehiculo(Vehiculo)
        + liberarEspacio()
    }
    class Vehiculo {
        + Str placa
        + Bool tipo
        + Propietario propietario
        + obtenerInformacion(): String
    }
    class Propietario {
        + Str nombre
        + Str telefono
        + Str correo
        + obtenerContacto(): String
    }
    class Tarifa {
        + Bool tipoVehiculo
        + Float precioPorHora
        + calcularCosto(TiempoEstadia): Double
    }
    class Registro {
        + Vehiculo vehiculo
        + EspacioParqueo espacio
        + Int horaEntrada
        + Int horaSalida
        + registrarSalida()
        + calcularCosto()
    }

    Parqueadero  <-- EspacioParqueo : administra espacios
    EspacioParqueo  <--  Vehiculo : asignar vehiculo, liberar espacio
    Vehiculo  <--  Propietario : obtener informacion
    Registro  <--  Vehiculo : calcular costo, registrar salida
    Registro  <--  EspacioParqueo : asociar espacio ocupado
    Parqueadero  <--  Tarifa : calcular costo

```

Este modelo permite reflejar cómo la clase principal, que es Parqueadero, interactúa con las demás clases que le permiten realizar sus operaciones, entre las cuales se incluyen manejar los espacios y la entrada y salida de vehículos.
