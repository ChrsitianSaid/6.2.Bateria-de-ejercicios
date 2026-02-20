# 6.2.Bateria-de-ejercicios
UML


Ejercicio 1 (1 punto)
Supuesto: Diseña una clase para gestionar un Usuario de una plataforma de streaming.

Atributos: nombre de usuario (privado), contraseña (privada), correo (público).
Métodos: cambiarPassword(String nueva) (público) y validarEmail() (privado).

classDiagram
    class Usuario {
        -nombreUsuario : String
        -password : String
        +correo : String
        +cambiarPassword(nueva : String)
        -validarEmail()
    }

<img width="731" height="518" alt="image" src="https://github.com/user-attachments/assets/8319ec53-c5bb-486c-aa9f-5fc2fd0d456c" />

Ejercicio 2 (1 punto)
Supuesto: En un sistema escolar, tenemos Personas y Estudiantes.

Una Persona tiene nombre y DNI.
Un Estudiante es una Persona, pero además tiene un numeroExpediente y una notaMedia.

classDiagram
    class Persona {
        nombre : String
        DNI : String
    }

    class Estudiante {
        numeroExpediente : int
        notaMedia : double
    }

    Persona <|-- Estudiante

    <img width="493" height="529" alt="image" src="https://github.com/user-attachments/assets/d881896d-e09a-40b2-a52e-0f5b037eac3f" />

    
Ejercicio 3 (1 punto)
Supuesto: Modelar una Computadora.

Una Computadora tiene una PlacaBase. Si la computadora se destruye, la placa base también se considera destruida (vínculo fuerte).
Una Computadora tiene periféricos como un Raton. Si la computadora desaparece, el ratón puede usarse en otra (vínculo débil).

classDiagram
    class Computadora
    class PlacaBase
    class Raton

    %% Composición (vínculo fuerte)
    Computadora *-- PlacaBase : contiene

    %% Agregación (vínculo débil)
    Computadora o-- Raton : usa


<img width="588" height="525" alt="image" src="https://github.com/user-attachments/assets/8d42756b-239f-4df7-8cb0-41aead9da99c" />


Ejercicio 4 (1,5 puntos)
Supuesto: Un CentroComercial y sus Tiendas.

Un CentroComercial puede albergar de 1 a muchas tiendas.
Cada Tienda pertenece exactamente a un CentroComercial.

classDiagram
    class CentroComercial {
    }

    class Tienda {
    }

    CentroComercial "1" o-- "1..*" Tienda


<img width="651" height="667" alt="image" src="https://github.com/user-attachments/assets/03e66861-77b1-4f8b-8331-24916f3273fc" />

Ejercicio 5 (2,5 puntos)
Supuesto: Sistema de pagos.

Crea una interfaz MetodoPago con el método procesar(double importe).
Las clases Tarjeta y Paypal deben implementar dicho contrato.
La clase Carrito tiene un método pagar(MetodoPago miMetodo) (Uso puntual).

classDiagram
    class MetodoPago {
        <<interface>>
        +procesar(importe : double)
    }

    class Tarjeta {
    }

    class Paypal {
    }

    class Carrito {
        +pagar(miMetodo : MetodoPago)
    }

    MetodoPago <|.. Tarjeta
    MetodoPago <|.. Paypal
    Carrito --> MetodoPago : usa


<img width="379" height="573" alt="image" src="https://github.com/user-attachments/assets/3c86a164-2532-4b6b-a6d2-1d6e597abc82" />

Ejercicio 6  (3 puntos)
Supuesto: Sistema de Gestión de una Biblioteca Universitaria

Contexto: La biblioteca necesita un sistema básico para gestionar su catálogo de recursos y los préstamos a los usuarios.

Requisitos del diseño (UML):

Clase Recurso (Padre):
Atributos: id (int) y titulo (String), ambos privados.
Métodos: prestar() y devolver(), ambos públicos.
Clases Libro y Revista (Hijas):
Ambas son tipos de Recurso (herencia).
Libro tiene un atributo propio: isbn (String).
Revista tiene un atributo propio: numeroEdicion (int).
Clase Usuario:
Atributos: nombre (String) y numCarnet (int).
Relación: Un Usuario puede tener uno o varios Recurso prestados en un momento dado (1 a 0..*).

classDiagram
    class Recurso {
        -id : int
        -titulo : String
        +prestar()
        +devolver()
    }

    class Libro {
        isbn : String
    }

    class Revista {
        numeroEdicion : int
    }

    class Usuario {
        nombre : String
        numCarnet : int
    }

    Recurso <|-- Libro
    Recurso <|-- Revista

    Usuario "1" --> "0..*" Recurso : presta
<img width="445" height="603" alt="image" src="https://github.com/user-attachments/assets/b609cccf-7857-4d5f-9e36-d253ef4edc0a" />

