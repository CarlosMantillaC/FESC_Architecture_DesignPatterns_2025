CLASS Implementation:
    METHOD operation_implementation() ABSTRACT

CLASS ConcreteImplementationA IMPLEMENTS Implementation:

    METHOD operation_implementation():
        PRINT "ConcreteImplementationA: Here's the result"

CLASS ConcreteImplementationB IMPLEMENTS Implementation:

    METHOD operation_implementation():
        PRINT "ConcreteImplementationB: Here's the result"

CLASS Abstraction:
    PROPERTY implementation: Implementation

    CONSTRUCTOR(implementation: Implementation):
        self.implementation = implementation

    METHOD operation():
        self.implementation.operation_implementation()

CLASS ExtendedAbstraction EXTENDS Abstraction:

    METHOD operation():
        PRINT "ExtendedAbstraction: Extended behavior with:"
        self.implementation.operation_implementation()

# Usage
implementationA = NEW ConcreteImplementationA()

abstraction = NEW Abstraction(implementationA)

abstraction.operation()


implementationB = NEW ConcreteImplementationB()

extendedAbstraction = NEW ExtendedAbstraction(implementationB)

extendedAbstraction.operation()
