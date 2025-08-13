INTERFACE Notification:
    METHOD send(message: string)

CLASS BasicNotification IMPLEMENTS Notification:
    METHOD send(message: string):
        PRINT "Sending basic notification: " + message


ABSTRACT CLASS NotificationDecorator IMPLEMENTS Notification:
    PROTECTED PROPERTY notification (Notification)

    CONSTRUCTOR(notification: Notification):
        self.notification = notification

    METHOD send(message: string):
        notification.send(message)


CLASS EmailDecorator EXTENDS NotificationDecorator:
    PRIVATE METHOD sendEmail(message: string):
        PRINT "Sending notification via Email: " + message

    OVERRIDE METHOD send(message: string):
        SUPER.send(message)
        sendEmail(message)


CLASS SMSDecorator EXTENDS NotificationDecorator:
    PRIVATE METHOD sendSMS(message: string):
        PRINT "Sending notification via SMS: " + message

    OVERRIDE METHOD send(message: string):
        SUPER.send(message)
        sendSMS(message)



notification = NEW BasicNotification()

notification = NEW EmailDecorator(notification)
notification = NEW SMSDecorator(notification)

notification.send("System Alert!")
