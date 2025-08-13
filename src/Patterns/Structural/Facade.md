CLASS Projector:
    METHOD turnOn():
        PRINT "Projector turned on"

    METHOD turnOff():
        PRINT "Projector turned off"


CLASS SoundSystem:
    METHOD on():
        PRINT "Sound system turned on"

    METHOD off():
        PRINT "Sound system turned off"


CLASS VideoPlayer:
    METHOD on():
        PRINT "Video player turned on"

    METHOD play(movie: string):
        PRINT "Playing " + movie

    METHOD stop():
        PRINT "Movie stopped"

    METHOD off():
        PRINT "Video player turned off"


CLASS PopcornMaker:
    METHOD poppingPopcorn():
        PRINT "Making popcorn"

    METHOD turnOffPoppingPopcorn():
        PRINT "Stopping popcorn"


INTERFACE HomeTheaterFacadeOptions:
    PROPERTY projector (Projector)
    PROPERTY soundSystem (SoundSystem)
    PROPERTY videoPlayer (VideoPlayer)
    PROPERTY popcornMaker (PopcornMaker)


CLASS HomeTheaterFacade:
    PRIVATE PROPERTY projector (Projector)
    PRIVATE PROPERTY soundSystem (SoundSystem)
    PRIVATE PROPERTY videoPlayer (VideoPlayer)
    PRIVATE PROPERTY popcornMaker (PopcornMaker)

    CONSTRUCTOR(options: HomeTheaterFacadeOptions):
        projector = options.projector
        popcornMaker = options.popcornMaker
        videoPlayer = options.videoPlayer
        soundSystem = options.soundSystem

    METHOD watchMovie(movie: string):
        PRINT "Preparing to watch the movie" 
        projector.turnOn()
        soundSystem.on()
        popcornMaker.poppingPopcorn()
        videoPlayer.on()
        videoPlayer.play(movie)
        PRINT "Enjoy the movie" 

    METHOD endWatchingMovie():
        PRINT "Preparing to stop the movie" 
        projector.turnOff()
        soundSystem.off()
        popcornMaker.turnOffPoppingPopcorn()
        videoPlayer.stop()
        videoPlayer.off()
        PRINT "System turned off" 



projector = NEW Projector()
soundSystem = NEW SoundSystem()
videoPlayer = NEW VideoPlayer()
popcornMaker = NEW PopcornMaker()

homeTheater = NEW HomeTheaterFacade({
    projector: projector,
    soundSystem: soundSystem,
    videoPlayer: videoPlayer,
    popcornMaker: popcornMaker
})

homeTheater.watchMovie("The Avengers")
homeTheater.endWatchingMovie()


