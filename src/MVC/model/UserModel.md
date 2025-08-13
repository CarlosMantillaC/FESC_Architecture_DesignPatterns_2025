INTERFACE UserModel:

    METHOD getUserName() RETURNS String
    METHOD setUserName(name: String)

CLASS BasicUser IMPLEMENTS UserModel:
    PROPERTY name (String)

    CONSTRUCTOR():
        self.name = "Guest"

    METHOD getUserName() RETURNS String:
        RETURN self.name

    METHOD setUserName(name: String):
        self.name = name