INTERFACE Observer:
    METHOD update(message: string)

INTERFACE Subject:
    METHOD addObserver(obs: Observer)
    METHOD notifyObservers(message: string)

CLASS YouTubeChannel IMPLEMENTS Subject:
    PROPERTY name (string)
    PROPERTY observers (list of Observer) = []

    CONSTRUCTOR(name: string):
        self.name = name

    METHOD addObserver(obs: Observer):
        APPEND obs TO observers

    METHOD notifyObservers(message: string):
        FOR EACH obs IN observers:
            obs.update("[" + name + "] " + message)

    METHOD uploadVideo(title: string):
        notifyObservers("New video: " + title)

CLASS EmailUser IMPLEMENTS Observer:
    PROPERTY name (string)

    CONSTRUCTOR(name: string):
        SET self.name = name

    METHOD update(message: string):
        PRINT "[EMAIL] " + name + " received: " + message

CLASS SmsUser IMPLEMENTS Observer:
    PROPERTY name (string)

    CONSTRUCTOR(name: string):
        self.name = name

    METHOD update(message: string):
        PRINT "[SMS] " + name + " received: " + message

channel = NEW YouTubeChannel("Channel1")
channel.addObserver( NEW SmsUser("Ana") )
channel.addObserver( NEW EmailUser("Ana") )

channel.uploadVideo("Observer Pattern")
