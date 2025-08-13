CLASS DragonBalls:
    PROPERTY instance (DragonBalls)
    PROPERTY ballsCollected (int)

    CONSTRUCTOR():
        self.ballsCollected = 0

    METHOD getInstance():
        IF instance IS NULL:
            instance = NEW DragonBalls()
        RETURN instance

    METHOD collectBall():
        IF ballsCollected < 7:
            ballsCollected = ballsCollected + 1
            PRINT ballsCollected
            RETURN
        PRINT "DragonBalls collected"

    METHOD summonShenlong():
        IF ballsCollected == 7:
            ballsCollected = 0
            RETURN
        PRINT "Incomplete DrangonBalls, you need: " + (7 - ballsCollected) + " DragonBalls"



gokuDragonBalls = DragonBalls.getInstance()

gokuDragonBalls.collectBall()
gokuDragonBalls.collectBall()
gokuDragonBalls.collectBall()

gokuDragonBalls.summonShenlong()

vegetaDragonBalls = DragonBalls.getInstance()
vegetaDragonBalls.collectBall()
vegetaDragonBalls.collectBall()
vegetaDragonBalls.collectBall()
vegetaDragonBalls.collectBall()

gokuDragonBalls.summonShenlong()

vegetaDragonBalls.summonShenlong()
