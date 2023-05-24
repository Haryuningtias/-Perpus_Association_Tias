# -Perpus_Association_Tias
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author
        self.is_available = True

    def borrow(self):
        if self.is_available:
            self.is_available = False
            return True
        else:
            return False

    def return_book(self):
        self.is_available = True


class LibraryMember:
    def __init__(self, name):
        self.name = name
        self.borrowed_books = []

    def borrow_book(self, book):
        if book.borrow():
            self.borrowed_books.append(book)
            print(f"{self.name} has borrowed the book '{book.title}'.")
        else:
            print(f"The book '{book.title}' is not available for borrowing.")

    def return_book(self, book):
        if book in self.borrowed_books:
            self.borrowed_books.remove(book)
            book.return_book()
            print(f"{self.name} has returned the book '{book.title}'.")
        else:
            print(f"The book '{book.title}' is not borrowed by {self.name}.")

    def display_borrowed_books(self):
        print(f"{self.name}'s borrowed books:")
        for book in self.borrowed_books:
            print(f"Title: {book.title}")
            print(f"Author: {book.author}")
            print(f"Availability: {'Available' if book.is_available else 'Borrowed'}")
            print()


# Create Book objects
book1 = Book("Python Crash Course", "Eric Matthes")
book2 = Book("The Pragmatic Programmer", "Andrew Hunt, David Thomas")
book3 = Book("Clean Code", "Robert C. Martin")

# Membuat objek LibraryMember
member = LibraryMember("Tias")

# Meminjam buku
member.borrow_book(book1)
member.borrow_book(book2)
member.borrow_book(book3)

# Menampilkan buku yang dipinjam
member.display_borrowed_books()

# Mengembalikan buku
member.return_book(book2)

# Menampilkan buku setelah pengembalian
member.display_borrowed_books()
