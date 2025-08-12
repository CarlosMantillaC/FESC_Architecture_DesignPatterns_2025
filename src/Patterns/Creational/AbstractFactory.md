# English version
CLASS AbstractFactory:
    METHOD createProductA() ABSTRACT
    METHOD createProductB() ABSTRACT

CLASS ConcreteFactory1 IMPLEMENTS AbstractFactory:

    METHOD createProductA():
        RETURN NEW ConcreteProductA1()
    
    METHOD createProductB():
        RETURN NEW ConcreteProductB1()

CLASS ConcreteFactory2 IMPLEMENTS AbstractFactory:

    METHOD createProductA():
        RETURN NEW ConcreteProductA2()
    
    METHOD createProductB():
        RETURN NEW ConcreteProductB2()

CLASS AbstractProductA:
    METHOD operationA() ABSTRACT

CLASS ConcreteProductA1 IMPLEMENTS AbstractProductA:

    METHOD operationA():
        PRINT "ConcreteProductA1 operation"

CLASS ConcreteProductA2 IMPLEMENTS AbstractProductA:

    METHOD operationA():
        PRINT "ConcreteProductA2 operation"

CLASS AbstractProductB:
    METHOD operationB() ABSTRACT

CLASS ConcreteProductB1 IMPLEMENTS AbstractProductB:

    METHOD operationB():
        PRINT "ConcreteProductB1 operation"

CLASS ConcreteProductB2 IMPLEMENTS AbstractProductB:

    METHOD operationB():
        PRINT "ConcreteProductB2 operation"

# Usage
factory1 = NEW ConcreteFactory1()
productA1 = factory1.createProductA()
productB1 = factory1.createProductB()
productA1.operationA()
productB1.operationB()

factory2 = NEW ConcreteFactory2()
productA2 = factory2.createProductA()
productB2 = factory2.createProductB()
productA2.operationA()
productB2.operationB()