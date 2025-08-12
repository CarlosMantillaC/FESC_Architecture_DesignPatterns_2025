INTERFACE Component:
    PROPERTY name (string)
    METHOD show()

CLASS File IMPLEMENTS Component:
    PROPERTY name (string)
    
    CONSTRUCTOR(name):
        self.name = name
    
    METHOD show():
        PRINT "showing file " + name

CLASS Folder IMPLEMENTS Component:
    PROPERTY name (string)
    PROPERTY components (list of Component) = []
    
    CONSTRUCTOR(name):
        self.name = name
    
    METHOD addComponent(component: Component):
        APPEND component TO components
    
    METHOD show():
        PRINT "showing folder " + name
        FOR EACH component IN components:
            component.show()

file1 = NEW File("file1")
file2 = NEW File("file2")
file3 = NEW File("file3")
folder1 = NEW Folder("folder1")
folder2 = NEW Folder("folder2")

folder1.addComponent(file1)
folder1.addComponent(file2)
folder2.addComponent(file3)
folder1.addComponent(folder2)
folder1.show()
