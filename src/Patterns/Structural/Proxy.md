INTERFACE Video:
    METHOD play()

CLASS PrivateVideo IMPLEMENTS Video:
    PROPERTY title (string)

    CONSTRUCTOR(title: string):
        self.title = title

    METHOD play():
        PRINT "playing " + title

CLASS VideoProxy IMPLEMENTS Video:
    PROPERTY user (string)
    PROPERTY realVideo (Video)
    PROPERTY allowedUsers (list of string)

    CONSTRUCTOR(user: string, realVideo: Video, allowedUsers: list of string):
        self.user = user
        self.realVideo = realVideo
        self.allowedUsers = allowedUsers

    METHOD play():
        IF allowedUsers CONTAINS user:
            realVideo.play()

realVideo = NEW PrivateVideo("Private Video")
allowedUsers = ["admin", "user1", "user2"]

videoProxy = NEW VideoProxy("admin", realVideo, allowedUsers)
videoProxy.play()
