INTERFACE HandleAmount:
    PROPERTY next (HandleAmount)
    METHOD authorize(amount: float)
    METHOD passToNext(amount: float)

CLASS Employee IMPLEMENTS HandleAmount:
    PROPERTY next (HandleAmount) = null

    METHOD authorize(amount: float):
        IF amount <= 1000:
            PRINT "Amount " + amount + " authorized by Employee."
        ELSE:
            passToNext(amount)

    METHOD passToNext(amount: float):
        PRINT "Employee passes amount " + amount + " to Supervisor."
        IF next IS NOT null:
            next.authorize(amount)

CLASS Supervisor IMPLEMENTS HandleAmount:
    PROPERTY next (HandleAmount) = null

    METHOD authorize(amount: float):
        IF amount <= 5000:
            PRINT "Amount " + amount + " authorized by Supervisor."
        ELSE:
            passToNext(amount)

    METHOD passToNext(amount: float):
        PRINT "Supervisor passes amount " + amount + " to Manager."
        IF next IS NOT null:
            next.authorize(amount)

CLASS Manager IMPLEMENTS HandleAmount:
    PROPERTY next (HandleAmount) = null

    METHOD authorize(amount: float):
        IF amount <= 10000:
            PRINT "Amount " + amount + " authorized by Manager."
        ELSE:
            passToNext(amount)

    METHOD passToNext(amount: float):
        PRINT "Amount " + amount + " cannot be authorized by anyone."

employee = NEW Employee()
supervisor = NEW Supervisor()
manager = NEW Manager()

employee.next = supervisor
supervisor.next = manager

employee.authorize(700)
employee.authorize(3000)
employee.authorize(7500)
employee.authorize(20000)
