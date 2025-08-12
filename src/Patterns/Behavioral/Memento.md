CLASS Memento:
    PRIVATE PROPERTY state (string)

    CONSTRUCTOR(state):
        self.state = state

    METHOD getState():
        RETURN state

CLASS TextEditor:
    PROPERTY content (string) = ""

    METHOD addContent(text: string):
        content = content + text

    METHOD show():
        PRINT content

    METHOD createMemento():
        RETURN NEW Memento(content)

    METHOD restore(memento: Memento):
        content = memento.getState()

CLASS History:
    PROPERTY changes (list of Memento) = []

    METHOD save(memento: Memento):
        APPEND memento TO changes

    METHOD undo():
        IF changes IS NOT EMPTY:
            REMOVE last item FROM changes
            RETURN last item OF changes OR null IF empty
        RETURN null

editor = NEW TextEditor()
history = NEW History()

editor.addContent("Hello ")
history.save(editor.createMemento())
editor.show()

editor.addContent("World ")
history.save(editor.createMemento())
editor.show()

editor.addContent("Cruel ")
history.save(editor.createMemento())
editor.show()

IF history.undo() IS NOT null:
    editor.restore(history.undo())
editor.show()

IF history.undo() IS NOT null:
    editor.restore(history.undo())
editor.show()
