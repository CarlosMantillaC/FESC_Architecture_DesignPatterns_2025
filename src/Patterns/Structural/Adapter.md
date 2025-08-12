INTERFACE LegacyCardReader:
    METHOD readOldCard()

CLASS OldCardReader IMPLEMENTS LegacyCardReader:
    METHOD readOldCard():
        PRINT "using old card"

INTERFACE SecureCardReader:
    METHOD readSecureData()

CLASS OldCardAdapter IMPLEMENTS SecureCardReader:
    PROPERTY oldCard (LegacyCardReader)

    CONSTRUCTOR(oldCard: LegacyCardReader):
        SET self.oldCard = oldCard

    METHOD readSecureData():
        PRINT "secure card"
        oldCard.readOldCard()

oldCard = NEW OldCardReader()
secureCard = NEW OldCardAdapter(oldCard)
secureCard.readSecureData()
