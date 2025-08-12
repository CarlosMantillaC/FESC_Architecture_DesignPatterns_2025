CLASS ChatMediator:
    PROPERTY users (list of User) = []

    METHOD addUser(user: User):
        APPEND user TO users

    METHOD sendMessage(message: string, sender: User):
        FOR EACH user IN users:
            user.receive(message, sender)

CLASS User:
    PROPERTY name (string)
    PROPERTY mediator (ChatMediator)

    CONSTRUCTOR(name, mediator):
        self.name = name
        self.mediator = mediator

    METHOD send(message: string):
        mediator.sendMessage(message, self)

    METHOD receive(message: string, sender: User):
        IF sender IS SAME INSTANCE AS self:
            RETURN
        PRINT name + " received '" + message + "' from " + sender.name

chat1 = NEW ChatMediator()

juan = NEW User("Juan", chat1)
jose = NEW User("Jose", chat1)

chat1.addUser(juan)
chat1.addUser(jose)

juan.send("Hello Jose")
jose.send("Hello Juan")
