INTERFACE State:
    PROPERTY name (string)
    METHOD insertMoney()
    METHOD selectProduct()
    METHOD dispenseProduct()

CLASS VendingMachine:
    PRIVATE PROPERTY state (State)

    CONSTRUCTOR():
        self.state = NEW WaitingForMoney(self)

    METHOD insertMoney():
        state.insertMoney()

    METHOD selectProduct():
        state.selectProduct()

    METHOD dispenseProduct():
        state.dispenseProduct()

    METHOD setState(newState: State):
        state = newState
        PRINT "State changed to: " + newState.name

    METHOD getStateName():
        RETURN state.name


CLASS WaitingForMoney IMPLEMENTS State:
    PROPERTY name = "Wait Money"
    PRIVATE PROPERTY vendingMachine (VendingMachine)

    CONSTRUCTOR(vendingMachine):
        self.vendingMachine = vendingMachine

    METHOD insertMoney():
        PRINT "Money accept: Now you can choose a product"
        vendingMachine.setState( NEW ProductSelected(vendingMachine) )

    METHOD selectProduct():
        PRINT "You must insert money first"

    METHOD dispenseProduct():
        PRINT "You must insert money first"


CLASS ProductSelected IMPLEMENTS State:
    PROPERTY name = "Seleccting product"
    PRIVATE PROPERTY vendingMachine (VendingMachine)

    CONSTRUCTOR(vendingMachine):
        self.vendingMachine = vendingMachine

    METHOD insertMoney():
        PRINT "Please select a product"

    METHOD selectProduct():
        vendingMachine.setState( NEW DispensingProduct(vendingMachine) )

    METHOD dispenseProduct():
        PRINT "Please select a product for dispatch" (en rojo)


CLASS DispensingProduct IMPLEMENTS State:
    PROPERTY name = "Please wait"
    PRIVATE PROPERTY vendingMachine (VendingMachine)

    CONSTRUCTOR(vendingMachine):
        self.vendingMachine = vendingMachine

    METHOD insertMoney():
        PRINT "Please wait" 

    METHOD selectProduct():
        PRINT "Product selected and dispacthed" 

    METHOD dispenseProduct():
        PRINT "Product dispatched" 
        vendingMachine.setState( NEW WaitingForMoney(vendingMachine) )



vendingMachine = NEW VendingMachine()
selectedOption = "4"

DO:
    PRINT "Selecciona una opción: " + vendingMachine.getStateName() 
    selectedOption = INPUT("""
        1. Insert money
        2. Choose product
        3. Dispense product
        4. Close
        opción:
    """)

    SWITCH selectedOption:
        CASE "1":
            vendingMachine.insertMoney()
        CASE "2":
            vendingMachine.selectProduct()
        CASE "3":
            vendingMachine.dispenseProduct()
        CASE "4":
            PRINT "Back to system"
        DEFAULT:
            PRINT "Invalid option"
            
WHILE selectedOption != "4"