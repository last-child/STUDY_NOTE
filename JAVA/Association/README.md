## 01. Association

<br>   

```java
class Librarian {
    String name;

    Librarian(String name) {
        this.name = name;
    }

    public void manageLibrary() {
        System.out.println(name + " is managing the library.");
    }
}
```

<br>   

```java
class Library {
    String name;
    private Librarian librarian;

    Library(String name, Librarian librarian) {
        this.name = name;
        this.librarian = librarian;
    }

    public void changeLibrarian(Librarian newLibrarian) {
        this.librarian = newLibrarian;
        System.out.println("Librarian has been changed to : " + newLibrarian.name);
    }

    public void openLibrary() {
        System.out.println(name + " is now open.");
        librarian.manageLibrary();
    }
}
```

<br>   

```java

public class AssociationExample {
    public static void main(String[] args) {
        Librarian teacher1 = new Librarian("서세연");
        Librarian teacher2 = new Librarian("최수민");

        Library library = new Library("중앙 도서관", teacher1);
        library.openLibrary();

        library.changeLibrarian(teacher2);
        library.openLibrary();
    }
}
```

<br>   

#### Association은 두 클래스 간의 연결을 나타낸다. 
#### 한 클래스의 객체는 다른 클래스의 객체를 참조할 수도 있고, 다른 클래스의 객체로부터 참조될 수도 있다.
#### 하지만 객체 간의 연결이 느슨하기 때문에 한 객체의 상태 변화가 반드시 다른 객체에 영향을 미치는 것은 아니다.

<br>   

#### 예를 들어 도서관 객체가 사서 객체를 참조하지만, 도서관 객체가 소멸되어도 사서 객체는 그대로 남아있을 수 있다.
#### 또한 사서 클래스의 코드를 수정해도 도서관 객체의 기능에 영향을 미치지 않는다.
#### Association에서 참조가 동적으로 변경될 수 있다. 즉 도서관 객체는 사서 객체를 유연하게 교체할 수 있다. 

<br>   
<br>   
<br>   
<br>   

## 02. Aggregation

<br>   

```java
class Book {
    String title;
    String author;

    Book(String title, String author) {
        this.title = title;
        this.author = author;
    }
}
```

<br>   

```java
class Library {
    String name;
    private List<Book> books;

    Library(String name) {
        this.name = name;
        this.books = new ArrayList<>();
    }

    public void addBook(Book book) {
        books.add(book);
        System.out.println(book.title + " has been added to the library.");
    }

    public void removeBook(Book book) {
        if (books.remove(book)) {
            System.out.println(book.title + " has been removed from the library.");
        } else {
            System.out.println("Book not found in the library.");
        }
    }

    public List<Book> getBooks() {
        return books;
    }
}
```

<br>   

```java
public class AggregationExample {
    public static void main(String[] args) {
        Library library = new Library("Central Library");

        Book book1 = new Book("나루토", "키시모토 마사시");
        Book book2 = new Book("원피스", "오다 에이치로");
        Book book3 = new Book("블리치", "쿠보 타이토");

        library.addBook(book1);
        library.addBook(book2);
        library.addBook(book3);

        library.removeBook(book1);

        // 도서관에 있는 책 출력
        for (Book book : library.getBooks()) {
            System.out.println(book.title + " by " + book.author);
        }
    }
}
```

<br>   

#### Aggregation은 전체와 부분의 관계를 나타내지만, 전체 객체와 부분 객체는 독립적으로 존재할 수 있다. 
#### 전체 객체와 부분 객체는 느슨하게 결합되어 있어 부분 객체를 유연하게 교체하거나, 부분 객체의 코드를 자유롭게 수정할 수 있다. 

<br>   

#### 예를 들어 Library 객체는 Book 객체들을 가지고 있다. 
#### 하지만 Book 객체는 Library 객체의 생명주기에 의존적이지 않으므로, Book 객체가 Library 객체 없이도 존재할 수 있다. 
#### 또한 두 객체는 느슨하게 결합되기 때문에 Library 객체는 Book 객체를 유연하게 교체할 수 있다. 

<br>   
<br>   
<br>   
<br>   

## 03. Composition

<br>   

```java
class Room {
    String roomName;
    int floor;

    Room(String name, int floor) {
        this.roomName = name;
        this.floor = floor;
    }

    public void describe() {
        System.out.println(floor + "층 " + roomName);
    }
}
```

<br>   

```java
class Library {
    private List<Room> rooms;

    Library(List<Room> rooms) {
        this.rooms = rooms;
    }

    public void describe() {
        for (Room room : rooms) {
            room.describe();
        }
    }
}
```

<br>   

```java
public class CompositionExample {
    public static void main(String[] args) {
        Library library = new Library();
        
        Room readingRoom = new Room("ReadingRoom", 1);
        Room referenceRoom = new Room("ReferenceRoom", 2);

        library.addRoom(readingRoom);
        library.addRoom(referenceRoom);

        library.describe();
    }
}
```

<br>   

#### Composition은 전체와 부분의 관계를 나타내지만, '부분' 객체의 생명주기는 '전체' 객체에 의존적이다.
#### 전체 객체가 소멸하면 부분 객체도 함께 소멸하기 때문에 부분 객체가 전체 객체 없이는 독립적으로 존재할 수 없다.
#### 예를 들어 각 방은 도서관의 일부로서만 존재한다. 도서관이 소멸하면 그 안의 모든 방들도 함께 소멸한다. 
