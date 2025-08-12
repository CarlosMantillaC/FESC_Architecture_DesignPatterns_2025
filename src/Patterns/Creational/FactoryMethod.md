CLASS Creator:

    METHOD factoryMethod() ABSTRACT
    METHOD someOperation():
        product = self.factoryMethod()
        product.operation()

CLASS ConcreteCreator1 IMPLEMENTS Creator:

    METHOD factoryMethod():
        RETURN NEW ConcreteProduct1()

CLASS ConcreteCreator2 IMPLEMENTS Creator:

    METHOD factoryMethod():
        RETURN NEW ConcreteProduct2()

CLASS Product:
    METHOD operation() ABSTRACT

CLASS ConcreteProduct1 IMPLEMENTS Product:

    METHOD operation():
        PRINT "ConcreteProduct1 operation"

CLASS ConcreteProduct2 IMPLEMENTS Product:

    METHOD operation():
        PRINT "ConcreteProduct2 operation"

# Usage
creator1 = NEW ConcreteCreator1()

creator1.someOperation()  # Output: "ConcreteProduct1 operation"

creator2 = NEW ConcreteCreator2()

creator2.someOperation()  # Output: "ConcreteProduct2 operation"