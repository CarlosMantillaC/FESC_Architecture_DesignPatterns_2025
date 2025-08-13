INTERFACE MovementStrategy:
    METHOD move()

CLASS SwimFast IMPLEMENTS MovementStrategy:
    METHOD move():
        PRINT "The duck swims quickly over the water"

CLASS FlyOverWater IMPLEMENTS MovementStrategy:
    METHOD move():
        PRINT "The duck flies elegantly over the water"

CLASS WalkClumsily IMPLEMENTS MovementStrategy:
    METHOD move():
        PRINT "The duck walks clumsily along the shore"

CLASS Duck:
    PRIVATE PROPERTY name (string)
    PRIVATE PROPERTY movementStrategy (MovementStrategy)

    CONSTRUCTOR(name, strategy: MovementStrategy):
        self.name = name
        self.movementStrategy = strategy
        PRINT name + " ready to compete" (green text for name, white text for rest)

    METHOD performMove():
        PRINT name + " is getting ready to move..."
        movementStrategy.move()

    METHOD setMovementStrategy(strategy: MovementStrategy):
        movementStrategy = strategy
        PRINT name + " changed strategy."

duck1 = NEW Duck("Fast Duck", NEW SwimFast())
duck2 = NEW Duck("Flying Duck", NEW FlyOverWater())
duck3 = NEW Duck("Clumsy Duck", NEW WalkClumsily())

PRINT "The duck race begins!"

duck1.performMove()
duck2.performMove()
duck3.performMove()

duck3.setMovementStrategy( NEW FlyOverWater() )
duck3.performMove()

duck3.setMovementStrategy( NEW SwimFast() )
duck3.performMove()