CLASS UserController:

    PROPERTY model (UserModel)
    PROPERTY view (UserView)

    CONSTRUCTOR(model: UserModel, view: UserView):
        self.model = model
        self.view = view

    METHOD updateUserName(name: String):
        model.setUserName(name)
        view.displayUserInfo(model.getUserName())

    METHOD showUser():
        view.displayUserInfo(model.getUserName())

// Usage
user = NEW BasicUser()
view = NEW ConsoleUserView()
controller = NEW UserController(user, view)

controller.showUser() 
controller.updateUserName("Alice") 