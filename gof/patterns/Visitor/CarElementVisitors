from __future__ import generators


class CarElement(object):
    def accept(self, visitor):
        visitor.visit(self)

    def __str__(self):
        return self.__class__.__name__


class Car(CarElement):
    def __init__(self):
        self.elements = [Engine(), Body(), Wheel("Front right"), Wheel("Front left"), Wheel("Rear right"),
                         Wheel("Rear left")]

    def accept(self, visitor):
        for element in self.elements:
            element.accept(visitor)

        visitor.visit(self)


class Body(CarElement): pass


class Engine(CarElement): pass


class Wheel(CarElement):
    def __init__(self, name):
        self.name = name


class Visitor:
    def __str__(self):
        return self.__class__.__name__


class CarElementVisitor(Visitor): pass


class CarElementPrint(CarElementVisitor):
    def visit(self, element):
        if isinstance(element, Wheel):
            print('Visiting my', element.name)
        else:
            print('Visiting my', element)


class CarElementDo(CarElementVisitor):
    def visit(self, element):
        if isinstance(element, Wheel):
            print('Doing action on my', element.name)
        else:
            print('Doing action on my', element)


car = Car()
visitor = CarElementPrint()
car.accept(visitor)
visitor = CarElementDo()
car.accept(visitor)

