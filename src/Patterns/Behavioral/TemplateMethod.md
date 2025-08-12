CLASS AbstractClass:

    METHOD templateMethod():
        self.baseOperation1()
        self.requiredOperation1()
        self.baseOperation2()
        self.requiredOperation2()
        self.hook()

    METHOD baseOperation1():
        PRINT "AbstractClass: baseOperation1"

    METHOD baseOperation2():
        PRINT "AbstractClass: baseOperation2"

    METHOD requiredOperation1() ABSTRACT

    METHOD requiredOperation2() ABSTRACT

    METHOD hook():
        PASS

CLASS ConcreteClass1 IMPLEMENTS AbstractClass:

    METHOD requiredOperation1():
        PRINT "ConcreteClass1: requiredOperation1"

    METHOD requiredOperation2():
        PRINT "ConcreteClass1: requiredOperation2"

CLASS ConcreteClass2 IMPLEMENTS AbstractClass:

    METHOD requiredOperation1():
        PRINT "ConcreteClass2: requiredOperation1"

    METHOD requiredOperation2():
        PRINT "ConcreteClass2: requiredOperation2"

    METHOD hook():
        PRINT "ConcreteClass2: Custom hook behavior"

# Usage
concrete1 = NEW ConcreteClass1()

concrete1.templateMethod()


concrete2 = NEW ConcreteClass2()

concrete2.templateMethod()
