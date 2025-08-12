INTERFACE Light:
    METHOD turnOn()
    METHOD turnOff()

CLASS BasicLight IMPLEMENTS Light:
    METHOD turnOn():
        PRINT "light on"

    METHOD turnOff():
        PRINT "light off"

INTERFACE Command:
    METHOD execute()

CLASS TurnOnLight IMPLEMENTS Command:
    PROPERTY light (Light)

    CONSTRUCTOR(light: Light):
        self.light = light

    METHOD execute():
        light.turnOn()

CLASS TurnOffLight IMPLEMENTS Command:
    PROPERTY light (Light)

    CONSTRUCTOR(light: Light):
        self.light = light

    METHOD execute():
        light.turnOff()

CLASS RemoteControl:
    PROPERTY command (Command)

    CONSTRUCTOR(command: Command):
        self.command = command

    METHOD pressButton():
        command.execute()

light = NEW BasicLight()
turnOnLight = NEW TurnOnLight(light)

remoteControl = NEW RemoteControl(turnOnLight)
remoteControl.pressButton()
