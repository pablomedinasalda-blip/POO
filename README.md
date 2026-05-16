Ejercicio 1
from abc import ABC, abstractmethod

class Figura(ABC):

    @abstractmethod
    def calcular_area(self):
        pass

    @abstractmethod
    def calcular_perimetro(self):
        pass


class Rectangulo(Figura):

    def __init__(self, base, altura):
        self.base = base
        self.altura = altura

    def calcular_area(self):
        return self.base * self.altura

    def calcular_perimetro(self):
        return 2 * (self.base + self.altura)


class Triangulo(Rectangulo):

    def __init__(self, base, altura, lado_a, lado_b, lado_c):
        super().__init__(base, altura)
        self.lado_a = lado_a
        self.lado_b = lado_b
        self.lado_c = lado_c

    def calcular_area(self):
        return (self.base * self.altura) / 2

    def calcular_perimetro(self):
        return self.lado_a + self.lado_b + self.lado_c


rectangulo = Rectangulo(10, 5)
triangulo = Triangulo(6, 4, 6, 5, 5)

print("Rectangulo")
print("Area:", rectangulo.calcular_area())
print("Perimetro:", rectangulo.calcular_perimetro())

print("\nTriangulo")
print("Area:", triangulo.calcular_area())
print("Perimetro:", triangulo.calcular_perimetro())



Ejercicio 2
from abc import ABC, abstractmethod

class Vehiculo(ABC):
    def __init__(self, marca):
        self.marca = marca

    @abstractmethod
    def describir_transporte(self):
        pass


class Bicicleta(Vehiculo):
    def __init__(self, marca, num_cambios):
        super().__init__(marca)
        self.num_cambios = num_cambios

    def describir_transporte(self):
        print(f"La bicicleta es de marca {self.marca} y tiene {self.num_cambios} cambios.")


bicicleta1 = Bicicleta("GW", 18)
bicicleta2 = Bicicleta("Venzo", 21)

bicicleta1.describir_transporte()
bicicleta2.describir_transporte()

Ejercicio 3
from abc import ABC, abstractmethod

class Docente:
    def __init__(self, nombre, especialidad):
        self.nombre = nombre
        self.especialidad = especialidad


class Curso(ABC):
    def __init__(self, nombre, docente, horas, costo_hora):
        self.nombre = nombre
        self.docente = docente
        self.horas = horas
        self.costo_hora = costo_hora

    @abstractmethod
    def calcular_costo(self):
        pass

    @abstractmethod
    def mostrar_detalle(self):
        pass


class CursoPresencial(Curso):
    def calcular_costo(self):
        return (self.horas * self.costo_hora) + 30000

    def mostrar_detalle(self):
        print("----- CURSO PRESENCIAL -----")
        print("Nombre del curso:", self.nombre)
        print("Docente:", self.docente.nombre)
        print("Especialidad:", self.docente.especialidad)
        print("Horas:", self.horas)
        print("Costo total:", self.calcular_costo())


class CursoVirtual(Curso):
    def calcular_costo(self):
        return self.horas * self.costo_hora

    def mostrar_detalle(self):
        print("----- CURSO VIRTUAL -----")
        print("Nombre del curso:", self.nombre)
        print("Docente:", self.docente.nombre)
        print("Especialidad:", self.docente.especialidad)
        print("Horas:", self.horas)
        print("Costo total:", self.calcular_costo())


docente1 = Docente("Carlos Ramirez", "Programacion")
docente2 = Docente("Laura Gomez", "Bases de Datos")

curso1 = CursoPresencial("Python POO", docente1, 40, 50000)
curso2 = CursoVirtual("SQL Basico", docente2, 30, 40000)

curso1.mostrar_detalle()
print()
curso2.mostrar_detalle()
