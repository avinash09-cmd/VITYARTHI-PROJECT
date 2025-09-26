# Campus Course & Records Manager (CCRM) - README

CCRM is a console-based Java application for managing student records, courses, enrollments, and grades. It's a Java SE 17 project demonstrating core OOP principles, modern Java APIs, and key design patterns through a command-line interface (CLI).

-----

## 1\. How to Run

**Prerequisites:**

  * Java Development Kit (JDK) 17+
  * Git

**Execution:**

1.  **Clone:** `git clone <your-repository-link> && cd CCRM-Project`
2.  **Compile:** `javac -d out src/edu/ccrm/cli/Main.java`
3.  **Run:** `java -cp out edu.ccrm.cli.Main`

-----

## 2\. Core Java Concepts

### Evolution of Java (Key Milestones)

  * **J2SE 5.0 (2004):** Added Generics, Enums, Annotations.
  * **Java SE 7 (2011):** Introduced try-with-resources and NIO.2.
  * **Java SE 8 (2014):** A major release with Lambdas, Streams, and a new Date/Time API.
  * **Java SE 11 (2018):** First Long-Term Support (LTS) release in the new cadence.
  * **Java SE 17 (2021):** Current LTS, adding Sealed Classes and Pattern Matching.

### Java Editions: ME vs SE vs EE

| Feature        | Java ME (Micro Edition)              | Java SE (Standard Edition)          | Java EE (Enterprise Edition) -\> Jakarta EE |
| -------------- | ------------------------------------ | ----------------------------------- | ------------------------------------------ |
| **Target** | Embedded Systems, old mobile devices | Desktops, Servers (Core Platform)   | Large-scale, distributed web applications  |
| **Scope** | Subset of SE API for small devices   | The foundational Java platform      | Superset of SE API for enterprise features |
| **Technology** | `MIDP`, `CLDC`                       | `JDK`, `JRE`, `JVM`, `Swing`, `NIO` | `JPA`, `Servlets`, `JSP`, `EJB`            |

### Java Architecture: JDK, JRE, JVM

  * **JDK (Java Development Kit):** For developers. Contains tools to *compile* (`javac`), debug, and package code. It includes the JRE.
  * **JRE (Java Runtime Environment):** For users. Provides the libraries and JVM needed to *run* Java applications.
  * **JVM (Java Virtual Machine):** The core component that *executes* compiled Java bytecode. It provides platform independence.

### Errors vs. Exceptions

  * **`Error`:** Critical, unrecoverable system-level failures (e.g., `OutOfMemoryError`). Applications should not try to catch them.
  * **`Exception`:** Recoverable conditions an application can handle.
      * **Checked:** Must be handled (`try-catch` or `throws`) by the compiler (e.g., `IOException`).
      * **Unchecked (Runtime):** Usually programming mistakes (e.g., `NullPointerException`). Not enforced by the compiler.

-----

## 3\. Setup & Installation

### Windows JDK Setup

1.  Download and run the JDK 17 installer from Oracle.
2.  Set the `JAVA_HOME` environment variable to your JDK path (e.g., `C:\Program Files\Java\jdk-17`).
3.  Add `%JAVA_HOME%\bin` to your `Path` environment variable.
4.  Verify with `java -version` in a new terminal.
    ```
    [Screenshot of 'java -version' output here]
    ```

### Eclipse IDE Setup

1.  `File > New > Java Project`. Name it `CCRM`.
2.  Select the JDK 17 JRE.
3.  Copy the project's `edu` package into the `src` folder.
4.  Right-click `Main.java` \> `Run As > Java Application`.
    ```
    [Screenshot of Eclipse project setup here]
    ```

-----

## 4\. Feature Demonstration Mapping

| Requirement | Implementation Location (File / Class / Method) |
| :--- | :--- |
| **Packages & `main`** | `edu.ccrm.cli.Main`, overall package structure |
| **Primitives, Operators** | `StudentService.calculateGpa()`, `Course.credits` |
| **Decision Structures** | `CliHandler.mainMenu()` (`switch`), `StudentService.enrollStudent()` (`if-else`) |
| **Loops & Jumps** | `CliHandler.run()` (`while`), `CourseService.listAllCourses()` (`for-each`) |
| **Arrays & Utilities** | `StudentService.sortStudentsById()` using `Arrays.sort()` |
| **String Methods** | `ImportExportService.parseStudentFromCsv()` uses `line.split()` |
| **Encapsulation** | `Student.java`, `Course.java` (private fields, public getters) |
| **Inheritance** | `Person` (abstract) -\> `Student` / `Instructor` (subclasses) |
| **Abstraction** | `Person.java` (abstract class), `getProfileDetails()` (abstract method) |
| **Polymorphism** | `TranscriptService.printTranscript(Person person)` |
| **Access Levels** | `private`, `protected`, `public`, `default` used throughout |
| **Immutability** | `domain.value.CourseCode.java` (final class with final fields) |
| **Nested Classes** | `Course.Builder` (static nested), anonymous inner class in `CliHandler` |
| **Interfaces** | `io.Persistable.java`, implemented by service classes |
| **Lambdas & Func. I/F** | `CourseService.searchCourses()` with `Stream.filter()` predicate |
| **Enums** | `domain.Grade.java`, `domain.Semester.java` (with fields & constructor) |
| **Singleton Pattern** | `config.AppConfig.getInstance()` |
| **Builder Pattern** | `domain.Course.Builder` for object construction |
| **Exception Handling** | `try-catch-finally` in `ImportExportService`, `multi-catch` in `CliHandler` |
| **Custom Exceptions** | `exception.MaxCreditLimitExceededException`, `DuplicateEnrollmentException` |
| **Assertions** | `assert studentId != null;` in `StudentService.enrollStudent()` |
| **File I/O (NIO.2)** | `io.BackupService.java` using `Path`, `Files.copy()`, `Files.walk()` |
| **I/O with Streams** | `ImportExportService` using `Files.lines()` and `Files.write()` |
| **Date/Time API** | `Enrollment.enrollmentDate`, timestamped backup folders in `BackupService` |
| **Recursion** | `util.FileUtility.calculateDirectorySize(Path)` |

-----

## 5\. Usage & Configuration

### Enabling Assertions

Run with the `-ea` flag to enable assertion checks: `java -ea -cp out edu.ccrm.cli.Main`

### Sample Data

The `test-data` directory contains CSV files for import:

  * **`students.csv`:** `regNo,fullName,email`
  * **`courses.csv`:** `code,title,credits,instructorId,semester,department`

### Design Justification: Interface vs. Class Inheritance

  * **Class Inheritance (`Person` -\> `Student`)** models an **"is-a"** relationship for shared state and identity.
  * **Interface (`Persistable`)** models a **"can-do"** capability, allowing unrelated classes like `StudentService` and `CourseService` to share a common behavior contract (saving/loading data) without a rigid class hierarchy.

-----

## 6\. Acknowledgements

  * Project completed based on the provided specifications.
  * References: Official Oracle Java SE 17 Documentation.
