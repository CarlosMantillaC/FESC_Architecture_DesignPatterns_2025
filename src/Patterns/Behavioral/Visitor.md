INTERFACE Visitor:
    METHOD visitRollerCoaster(rollerCoaster: RollerCoaster)
    METHOD visitHauntedHouse(hauntedHouse: HauntedHouse)
    METHOD visitFerrisWheel(ferrisWheel: FerrisWheel)

INTERFACE Attraction:
    METHOD accept(visitor: Visitor)
    METHOD getPrice() RETURNS number

CLASS RollerCoaster IMPLEMENTS Attraction:
    PRIVATE PROPERTY price = 50

    METHOD getPrice():
        RETURN price

    METHOD accept(visitor: Visitor):
        visitor.visitRollerCoaster(self)

CLASS HauntedHouse IMPLEMENTS Attraction:
    PRIVATE PROPERTY price = 40

    METHOD getPrice():
        RETURN price

    METHOD accept(visitor: Visitor):
        visitor.visitHauntedHouse(self)

CLASS FerrisWheel IMPLEMENTS Attraction:
    PRIVATE PROPERTY price = 30

    METHOD getPrice():
        RETURN price

    METHOD accept(visitor: Visitor):
        visitor.visitFerrisWheel(self)


CLASS ChildVisitor IMPLEMENTS Visitor:
    METHOD visitRollerCoaster(rollerCoaster: RollerCoaster):
        PRINT "Child on Roller Coaster: Discounted price $" + (rollerCoaster.getPrice() * 0.5)

    METHOD visitHauntedHouse(hauntedHouse: HauntedHouse):
        PRINT "Child in Haunted House: Discounted price $" + (hauntedHouse.getPrice() * 0.7)

    METHOD visitFerrisWheel(ferrisWheel: FerrisWheel):
        PRINT "Child on Ferris Wheel: Discounted price $" + (ferrisWheel.getPrice() * 0.6)


CLASS AdultVisitor IMPLEMENTS Visitor:
    METHOD visitRollerCoaster(rollerCoaster: RollerCoaster):
        PRINT "Adult on Roller Coaster: Price $" + rollerCoaster.getPrice()

    METHOD visitHauntedHouse(hauntedHouse: HauntedHouse):
        PRINT "Adult in Haunted House: Price $" + hauntedHouse.getPrice()

    METHOD visitFerrisWheel(ferrisWheel: FerrisWheel):
        PRINT "Adult on Ferris Wheel: Price $" + ferrisWheel.getPrice()


CLASS SeniorVisitor IMPLEMENTS Visitor:
    METHOD visitRollerCoaster(rollerCoaster: RollerCoaster):
        PRINT "Senior on Roller Coaster: Discounted price $" + (rollerCoaster.getPrice() * 0.85)

    METHOD visitHauntedHouse(hauntedHouse: HauntedHouse):
        PRINT "Senior in Haunted House: Discounted price $" + (hauntedHouse.getPrice() * 0.85)

    METHOD visitFerrisWheel(ferrisWheel: FerrisWheel):
        PRINT "Senior on Ferris Wheel: Discounted price $" + (ferrisWheel.getPrice() * 0.85)



attractions = [
    NEW RollerCoaster(),
    NEW HauntedHouse(),
    NEW FerrisWheel()
]

PRINT "Roller Coaster: $" + NEW RollerCoaster().getPrice()
PRINT "Haunted House: $" + NEW HauntedHouse().getPrice()
PRINT "Ferris Wheel: $" + NEW FerrisWheel().getPrice()

PRINT "\nChild Visitor"
childVisitor = NEW ChildVisitor()
FOR EACH attraction IN attractions:
    attraction.accept(childVisitor)

PRINT "\nAdult Visitor"
adultVisitor = NEW AdultVisitor()
FOR EACH attraction IN attractions:
    attraction.accept(adultVisitor)

PRINT "\nSenior Visitor"
seniorVisitor = NEW SeniorVisitor()
FOR EACH attraction IN attractions:
    attraction.accept(seniorVisitor)
