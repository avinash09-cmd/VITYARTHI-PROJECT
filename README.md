
# Campus Course & Records Manager (CCRM)

## 📌 Project Overview

The **Campus Course & Records Manager (CCRM)** is a **console-based Java SE application** that enables an institute to manage:

* 👨‍🎓 **Students** – Add, update, deactivate, enroll/unenroll in courses.
* 📚 **Courses** – Add, update, deactivate, assign instructors, search, and filter.
* 📝 **Grades & Transcripts** – Record marks, compute GPA, generate transcripts.
* 📂 **File Utilities** – Import/export student/course data, backup/export with recursive utilities.

The project demonstrates **core Java concepts (OOP, Streams, Date/Time API, NIO.2, exception handling)** and integrates **design patterns (Singleton, Builder)** in a structured way.

---

## ⚙️ How to Run

### Requirements

* **Java SE 17+** (preferred)
* **Eclipse IDE / IntelliJ IDEA / CLI (javac + java)**
* OS: Windows/Linux/Mac

### Steps

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/ccrm.git
   cd ccrm
   ```
2. Compile and run:

   ```bash
   javac -d bin src/edu/ccrm/Main.java
   java -cp bin edu.ccrm.Main
   ```
3. Follow the **menu-driven console interface** to perform operations.

---

## 🚀 Minimum Demo Flow

1. On start, **AppConfig (Singleton)** loads configuration (e.g., data folder path).
2. CLI Menu provides options:

   * Manage Students / Courses / Enrollment / Grades
   * Import/Export Data
   * Backup & Show Recursive Backup Size
   * Reports (e.g., Top Students, GPA Distribution via Streams)
   * Exit
3. Perform **enrollments, record grades, and print transcript**.
4. Run **export and backup** → timestamped backup folder created.
5. Print platform note summarizing **Java ME vs SE vs EE**.

---

## 📂 Suggested Package Structure

```
edu.ccrm
├─ cli/          // Menu, Input loop
├─ domain/       // Person, Student, Instructor, Course, Enrollment, Grade, Semester
├─ service/      // StudentService, CourseService, EnrollmentService, TranscriptService
├─ io/           // ImportExportService, BackupService, CSV Parsers
├─ util/         // Validators, Comparators, Recursion Utilities
└─ config/       // AppConfig (Singleton), Builders
```

---

## 📖 Java Concepts Demonstrated

| Concept               | Where Used                                                               |
| --------------------- | ------------------------------------------------------------------------ |
| Encapsulation         | Student, Course classes (private fields + getters/setters)               |
| Inheritance           | `Person (abstract)` → `Student`, `Instructor`                            |
| Abstraction           | Abstract methods in `Person`                                             |
| Polymorphism          | Transcript printing with overridden `toString()`                         |
| Static Nested Class   | Inside `Course` (e.g., Builder)                                          |
| Inner Class           | Inside `Student` (Transcript printer)                                    |
| Interface             | `Persistable`, `Searchable<T>`                                           |
| Enums                 | `Semester`, `Grade` with constructors & fields                           |
| Functional Interfaces | Comparator lambdas for sorting                                           |
| Anonymous Inner Class | CLI callback handler                                                     |
| Singleton             | `AppConfig`                                                              |
| Builder Pattern       | `Course.Builder`, `Transcript.Builder`                                   |
| Exception Handling    | Custom `DuplicateEnrollmentException`, `MaxCreditLimitExceededException` |
| Assertions            | Used for credit limits & null checks                                     |
| Streams               | GPA distribution reports, search & filter                                |
| NIO.2                 | Backup, import/export, recursive file utilities                          |
| Date/Time API         | Enrollment dates, backup folder timestamps                               |

---

## 🛠️ Technical Notes

### Evolution of Java

* 1995: Java 1.0 released (Sun Microsystems).
* 2004: Java 5 (Generics, Enums, Annotations).
* 2011: Java 7 (try-with-resources, NIO.2).
* 2014: Java 8 (Lambdas, Streams, Date/Time API).
* 2017: Java 9+ (Modules, JShell).
* 2021+: Java 17 (LTS) with sealed classes, pattern matching.

### Java Editions

| Feature  | Java ME           | Java SE                                | Java EE            |
| -------- | ----------------- | -------------------------------------- | ------------------ |
| Use-case | Mobile & embedded | Desktop & core dev                     | Enterprise apps    |
| Scope    | Lightweight       | Core libraries (util, io, collections) | Servlets, EJB, JPA |
| Example  | Feature phones    | Local apps, CLI tools                  | Web apps, cloud    |

### JDK, JRE, JVM

* **JVM**: Executes Java bytecode.
* **JRE**: JVM + libraries (runtime only).
* **JDK**: JRE + compiler + dev tools.
  👉 **Dev uses JDK, Users use JRE.**

---

## 🖥️ Installation (Windows)

1. Download **JDK 17+** from [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Install and set `JAVA_HOME`.
3. Verify installation:

   ```bash
   java -version
   ```

   (include screenshot in `/screenshots`).

### Eclipse Setup

1. Install **Eclipse IDE for Java Developers**.
2. Create new project → `CCRM`.
3. Add packages (`edu.ccrm.*`) and run `Main`.
4. Screenshot setup + first run.

---

## 📝 Assertions

Enable assertions when running:

```bash
java -ea -cp bin edu.ccrm.Main
```

Used for:

* Checking **non-null IDs**.
* Validating **credit bounds**.

---

## 📦 Deliverables

* ✅ `src/` – Full source code
* ✅ `README.md` (this file)
* ✅ `USAGE.md` (sample commands & data files)
* ✅ `test-data/` (CSV import samples)
* ✅ `/screenshots/` folder (installation, IDE, runs, exports/backups)
* 🎥 Optional demo video (YouTube/Drive link)

---

## 🙏 Acknowledgements

* Oracle Java Docs
* Java Tutorials (docs.oracle.com/javase)
* NIO.2 & Streams API guides

---

Would you like me to also **make a USAGE.md with sample commands & sample CSV file formats** (students.csv, courses.csv) so that your project repo looks professional and demo-ready?
