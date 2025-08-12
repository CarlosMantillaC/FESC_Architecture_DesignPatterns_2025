CLASS Book:
    PROPERTY title (string)

    CONSTRUCTOR(title):
        self.title = title

    METHOD getTitle():
        PRINT title

CLASS Library:
    PROPERTY books (list of Book) = []

    METHOD addBook(book: Book):
        APPEND book TO books

    METHOD bookCount():
        RETURN LENGTH OF books

CLASS Iterator:
    PROPERTY library (Library)
    PROPERTY currentIndex (int) = 0

    CONSTRUCTOR(library):
        self.library = library

    METHOD hasMore():
        RETURN currentIndex < library.bookCount()

    METHOD nextBook():
        IF NOT hasMore():
            RETURN null
        SET book = library.books[currentIndex]
        INCREMENT currentIndex BY 1
        RETURN book

library = NEW Library()

library.addBook( NEW Book("book1") )
library.addBook( NEW Book("book2") )

iterator = NEW Iterator(library)

WHILE iterator.hasMore():
    iterator.nextBook()?.getTitle()
