INTERFACE UserView:
    METHOD displayUserInfo(info: String)

CLASS ConsoleUserView IMPLEMENTS UserView:

    METHOD displayUserInfo(info: String):
        PRINT "User Information: " + info