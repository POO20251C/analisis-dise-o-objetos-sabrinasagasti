classDiagram
    class Biblioteca {
        -libros: List~Libro~
        -usuarios: List~Usuario~
        -prestamos: List~Prestamo~
        +registrarLibro(libro: Libro): void
        +registrarUsuario(usuario: Usuario): void
        +registrarPrestamo(prestamo: Prestamo): void
        +registrarDevolucion(libroID: int, usuarioID: int): void
        +listarLibrosDisponibles(): List~Libro~
        +listarLibrosPrestados(): List~Libro~
        +consultarHistorial(usuarioID: int): List~Prestamo~
    }

    class Libro {
        -id: int
        -titulo: string
        -autor: string
        -genero: string
        -estado: string
        +marcarPrestado(): void
        +marcarDisponible(): void
    }

    class Usuario {
        -id: int
        -nombre: string
    }

    class Prestamo {
        -libroID: int
        -usuarioID: int
        -fechaInicio: date
        -fechaDevolucion: date
        -estado: string
    }

    Biblioteca "1" --> "*" Libro : contiene
    Biblioteca "1" --> "*" Usuario : registra
    Biblioteca "1" --> "*" Prestamo : gestiona
    Prestamo "*" --> "1" Libro : incluye
    Prestamo "*" --> "1" Usuario : realizadoPor
