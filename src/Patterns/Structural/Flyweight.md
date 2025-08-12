CLASS Circle:
    PRIVATE PROPERTY color (string)

    CONSTRUCTOR(color):
        self.color = color

    METHOD draw(x: int, y: int, radius: int):
        PRINT "Drawing a " + color + " circle at (" + x + ", " + y + ") with radius " + radius

CLASS CircleFactory:
    PRIVATE PROPERTY circles (dictionary<string, Circle>) = empty dictionary

    METHOD getCircle(color: string) -> Circle:
        IF color EXISTS in circles:
            RETURN circles[color]
        ELSE:
            newCircle = NEW Circle(color)
            circles[color] = newCircle
            RETURN newCircle

factory = NEW CircleFactory()

red1 = factory.getCircle("Red")
red1.draw(10, 20, 5)

red2 = factory.getCircle("Red")
red2.draw(15, 25, 10)

blue = factory.getCircle("Blue")
blue.draw(30, 40, 7)

PRINT (red1 IS SAME INSTANCE AS red2)
