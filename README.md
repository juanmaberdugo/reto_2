# reto_2
Elija un problema de la vida real (sistema de gestión de biblioteca, negocio de compra-venta, automóvil, etc) que se pueda modelar a través de objetos y clases. Plantee las relaciones de clases, composiciones, propiedades y comportamientos del sistema en uno mas diagramas tipo UML.
## Problema a analizar
Para desarrollar este reto me plantee realizar un diagrama de clases que tuvo como problema un parqueadero, el diagrama que realice fue el siguiente:
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

    Parqueadero  <-- EspacioParqueo 
    EspacioParqueo  <--  Vehiculo 
    Vehiculo  <--  Propietario 
    Registro  <--  Vehiculo 
    Registro  <--  EspacioParqueo 
    Parqueadero  <--  Tarifa
```
