CLASS Computer:
    PROPERTY cpu (string) 
    PROPERTY ram (int)
    PROPERTY storage (int)
    PROPERTY gpu (string)

    METHOD getProperties():
        PRINT cpu
        PRINT ram
        PRINT storage
        PRINT gpu

CLASS ComputerBuilder:
    METHOD setCPU(cpu: string)
    METHOD setRAM(ram: int)
    METHOD setStorage(storage: int)
    METHOD setGPU(gpu: string)
    METHOD build() : Computer

CLASS GamingComputerBuilder IMPLEMENTS ComputerBuilder:
    PROPERTY computer (Computer) = NEW Computer()

    METHOD setCPU(cpu):
        computer.cpu = cpu

    METHOD setRAM(ram):
        computer.ram = ram

    METHOD setStorage(storage):
        computer.storage = storage

    METHOD setGPU(gpu):
        computer.gpu = gpu

    METHOD build():
        RETURN computer

CLASS ComputerDirector:
    PROPERTY builder (ComputerBuilder)

    CONSTRUCTOR(builder):
        self.builder = builder

    METHOD buildGamingPC():
        builder.setCPU("Intel i9")
        builder.setRAM(32)
        builder.setStorage(2000)
        builder.setGPU("NVIDIA RTX 4090")
        RETURN builder.build()

gamingBuilder = NEW GamingComputerBuilder()
director = NEW ComputerDirector(gamingBuilder)

gamingPC = director.buildGamingPC()
gamingPC.getProperties()
