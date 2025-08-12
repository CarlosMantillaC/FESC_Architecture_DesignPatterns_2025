CLASS Prototype:
    METHOD clone() ABSTRACT

CLASS ConcretePrototype1 IMPLEMENTS Prototype:
    PROPERTY field

    CONSTRUCTOR(field):
        self.field = field

    METHOD clone():
        RETURN NEW ConcretePrototype1(self.field)  # Deep copy

CLASS ConcretePrototype2 IMPLEMENTS Prototype:
    PROPERTY data

    CONSTRUCTOR(data):
        self.data = data

    METHOD clone():
        RETURN NEW ConcretePrototype2(self.data.copy())  # Deep copy

# Usage
prototype1 = NEW ConcretePrototype1("Example 1")

clone1 = prototype1.clone()

PRINT clone1.field  # Output: "Example 1"


prototype2 = NEW ConcretePrototype2({"key": "value"})

clone2 = prototype2.clone()

PRINT clone2.data  # Output: {"key": "value"}