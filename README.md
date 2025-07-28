
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"> 
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <nav>
      <ul class="navbar">
        <li><a href="#core">Dot Net Core</a></li>
        <li><a href="#csharp">C# Sharp</a></li>
        <li><a href="#services">Web Services</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <section id="core">
    <h1>Welcome to My Website</h1>
    <p>This is a sample GitHub Pages site.</p>
  </section>

  <section id="csharp">
    <h2>C# Sharp</h2>
    <p>Some details about who I am and what I do.</p>
  </section>

  <section id="services">
    <h2>Web Services</h2>
    <p>Links to my GitHub projects.</p>
  </section>

  <section id="contact">
    <h2>Contact</h2>
    <p>How to reach me.</p>
  </section>

  <footer>
    <p>&copy; 2025 My GitHub Page</p>
  </footer>
</body>
</html>

https://beetroot.co/team/18-interview-questions-to-ask-a-senior-net-developer/?utm_source=chatgpt.com

https://www.onestopdevshop.io/senior-net-developer-interview-questions/?utm_source=chatgpt.com

https://zerotomastery.io/blog/dot-NET-interview-questions/

https://www.interviewbit.com/dot-net-interview-questions/

Classes and Methods in C#
Types of Classes in C#
C# provides several types of classes, each serving different purposes:

1. Regular (Concrete) Classes
Standard classes that can be instantiated

Can contain fields, properties, methods, events, etc.

Can inherit from other classes (single inheritance)

csharp
public class Person
{
    public string Name { get; set; }
    public void Greet() => Console.WriteLine($"Hello, {Name}");
}
2. Abstract Classes
Cannot be instantiated directly

Designed to be inherited by other classes

Can contain both implemented and abstract (unimplemented) members

csharp
public abstract class Shape
{
    public abstract double CalculateArea();
    
    public void Display()
    {
        Console.WriteLine($"Area: {CalculateArea()}");
    }
}
3. Static Classes
Cannot be instantiated

Contains only static members

Often used for utility functions

csharp
public static class MathHelper
{
    public static double Square(double num) => num * num;
}
4. Sealed Classes
Cannot be inherited

Prevents other classes from deriving from it

csharp
public sealed class Configuration
{
    // Implementation
}
5. Partial Classes
Class definition can be split across multiple files

Useful for separating generated code from hand-written code

csharp
// File1.cs
public partial class Employee
{
    public void Work() { /* ... */ }
}

// File2.cs
public partial class Employee
{
    public void TakeBreak() { /* ... */ }
}
6. Generic Classes
Classes that can work with different data types

Type is specified when the class is instantiated

csharp
public class GenericList<T>
{
    private List<T> items = new List<T>();
    public void Add(T item) => items.Add(item);
}
Types of Methods in C#
1. Instance Methods
Belong to an object instance

Can access instance members

csharp
public class Calculator
{
    public int Add(int a, int b) => a + b;
}
2. Static Methods
Belong to the class itself, not instances

Called using the class name

csharp
public class MathOperations
{
    public static int Multiply(int a, int b) => a * b;
}
3. Abstract Methods
Declared in abstract classes

No implementation (must be overridden in derived classes)

csharp
public abstract class Animal
{
    public abstract void MakeSound();
}
4. Virtual Methods
Can be overridden in derived classes

Have a base implementation

csharp
public class Vehicle
{
    public virtual void Start() => Console.WriteLine("Vehicle started");
}
5. Override Methods
Override virtual or abstract methods from base class

csharp
public class Car : Vehicle
{
    public override void Start() => Console.WriteLine("Car engine started");
}
6. Sealed Methods
Prevent further overriding in derived classes

Must be used with override keyword

csharp
public class SportsCar : Car
{
    public sealed override void Start() => Console.WriteLine("Sports car started");
}
7. Extension Methods
Static methods that appear to be instance methods

Extend existing types without modifying them

csharp
public static class StringExtensions
{
    public static bool IsNullOrEmpty(this string str) => string.IsNullOrEmpty(str);
}
8. Async Methods
Marked with async keyword

Can use await for asynchronous operations

csharp
public async Task<string> DownloadContentAsync(string url)
{
    using var client = new HttpClient();
    return await client.GetStringAsync(url);
}
9. Partial Methods
Split implementation across partial class definitions

Must return void

If not implemented, compiler removes the calls

csharp
public partial class DataProcessor
{
    partial void ValidateData();
    
    public void Process()
    {
        ValidateData();
        // Processing
    }
}

public partial class DataProcessor
{
    partial void ValidateData() => Console.WriteLine("Validating...");
}
Each type of class and method serves specific purposes in C# programming, allowing for flexible and maintainable code organization.

constructor and destructor is also methods in c#
Constructors and Destructors in C#
Constructors and destructors are special types of methods in C# that handle object initialization and cleanup, respectively.

Constructors
Constructors are special methods that are called when an object is created. They have the same name as the class and don't have a return type.

Types of Constructors:
Default Constructor

Provided automatically if no constructors are defined

Takes no parameters

Initializes fields to default values

csharp
public class Person
{
    // Default constructor (implicit if none defined)
    public Person() { }
}
Parameterized Constructor

Accepts parameters to initialize object with specific values

csharp
public class Person
{
    public string Name { get; set; }
    
    public Person(string name)
    {
        Name = name;
    }
}
Static Constructor

Initializes static members of a class

Called automatically before any static members are accessed

No access modifiers or parameters

csharp
public class Logger
{
    static Logger()
    {
        Console.WriteLine("Static constructor called");
    }
}
Private Constructor

Used to prevent instantiation of a class

Common in singleton pattern

csharp
public class Singleton
{
    private static Singleton _instance;
    
    private Singleton() { }
    
    public static Singleton Instance => _instance ??= new Singleton();
}
Copy Constructor

Creates an object by copying values from another object

csharp
public class Person
{
    public string Name { get; set; }
    
    public Person(Person otherPerson)
    {
        Name = otherPerson.Name;
    }
}
Constructor Chaining

One constructor calls another using this keyword

csharp
public class Rectangle
{
    public int Width { get; set; }
    public int Height { get; set; }
    
    public Rectangle() : this(0, 0) { }
    
    public Rectangle(int width, int height)
    {
        Width = width;
        Height = height;
    }
}
Destructors (Finalizers)
Destructors (also called finalizers) are special methods that are called when an object is being garbage collected. They are used to perform cleanup operations.

Key Points About Destructors:
Defined with a tilde (~) followed by the class name

Cannot be called explicitly - invoked automatically by garbage collector

Cannot have parameters or access modifiers

Should only be used when necessary (for unmanaged resources)

Implementation is generally preferred using IDisposable pattern

csharp
public class ResourceHolder
{
    // Destructor (Finalizer)
    ~ResourceHolder()
    {
        // Cleanup unmanaged resources
        Console.WriteLine("Destructor called");
    }
}
Better Alternative: IDisposable Pattern
For proper resource cleanup, implementing IDisposable is recommended over destructors:

csharp
public class ResourceHolder : IDisposable
{
    private bool disposed = false;
    
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }
    
    protected virtual void Dispose(bool disposing)
    {
        if (!disposed)
        {
            if (disposing)
            {
                // Dispose managed resources
            }
            
            // Dispose unmanaged resources
            disposed = true;
        }
    }
    
    ~ResourceHolder()
    {
        Dispose(false);
    }
}
Important Differences:
Feature	Constructor	Destructor
When called	Object creation	Garbage collection
Syntax	ClassName()	~ClassName()
Can be called	Explicitly via new	Only by GC
Parameters	Can have parameters	No parameters
Overloading	Possible	Not possible
Inheritance	Not inherited	Not inherited
Execution	Deterministic	Non-deterministic


Write a SQL query to find third highest salary of the employee.

CREATE TABLE EmployeeSalary (
    ID INT PRIMARY KEY,
    Name VARCHAR(100),
    Salary INT
);


INSERT INTO EmployeeSalary (ID, Name, Salary)
VALUES 
(1, 'Alice', 9000),
(2, 'Bob', 8500),
(3, 'Charlie', 8500),
(4, 'David', 8200),
(5, 'Eve', 7900),
(6, 'Frank', 7600),
(7, 'Grace', 9000),
(8, 'Hank', 7500);

Here are all the possible ways to get the top 3 highest salaries, depending on how you want to handle duplicates (ties).

SELECT TOP 1 salary 
FROM 
    (SELECT TOP 3 salary 
     FROM EmployeeSalary 
     ORDER BY salary DESC) AS Comp 
ORDER BY salary 

Simple and fast.
Does not handle ties. You get exactly 3 rows, even if there’s a tie at the third position.


WITH Ranked AS (
    SELECT *, ROW_NUMBER() OVER (ORDER BY Salary DESC) AS rn
    FROM EmployeeSalary
)
SELECT *
FROM Ranked
WHERE rn <= 3;


SELECT *
FROM EmployeeSalary E1
WHERE 2-1 = (
    SELECT COUNT(DISTINCT Salary)
    FROM EmployeeSalary E2
    WHERE E2.Salary > E1.Salary
);

WITH RankedEmployees AS (
    SELECT *, RANK() OVER (ORDER BY Salary DESC) AS RankNum
    FROM EmployeeSalary
)
SELECT  *
FROM RankedEmployees
WHERE RankNum <= 3;



deepseek
Finding the 3 Highest Salaries in MS SQL Server: Multiple Approaches
There are several ways to retrieve the top 3 highest salaries in MS SQL Server. Below I'll demonstrate each approach with detailed explanations.

1. Using TOP with ORDER BY (Simplest Approach)
sql
SELECT TOP 3 salary
FROM employees
ORDER BY salary DESC;
Explanation:

TOP 3 limits the result to just 3 rows

ORDER BY salary DESC sorts salaries in descending order (highest first)

This is the simplest approach but doesn't handle ties properly (if multiple employees share the same salary)

2. Using TOP WITH TIES
sql
SELECT TOP 3 WITH TIES salary
FROM employees
ORDER BY salary DESC;
Explanation:

WITH TIES includes all rows that match the last salary in the result

If the 3rd highest salary is shared by multiple employees, all will be returned

This ensures you get all employees who have the top 3 salary values

3. Using DENSE_RANK() (Best for handling ties)
sql
SELECT salary
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) as salary_rank
    FROM employees
) ranked_salaries
WHERE salary_rank <= 3;
Explanation:

DENSE_RANK() assigns the same rank to identical values without gaps

The inner query assigns a rank to each salary

The outer query filters for ranks 1-3

This is the most robust solution as it:

Handles ties properly

Returns exactly 3 distinct salary values (with all employees who have them)

Doesn't skip ranks if there are ties

4. Using ROW_NUMBER() (When you want distinct rows)
sql
SELECT salary
FROM (
    SELECT DISTINCT salary, ROW_NUMBER() OVER (ORDER BY salary DESC) as row_num
    FROM employees
) numbered_salaries
WHERE row_num <= 3;
Explanation:

ROW_NUMBER() assigns a unique number to each row

Using DISTINCT ensures we only count each salary value once

This approach returns exactly 3 rows (even if multiple employees share the same salary)

5. Using OFFSET-FETCH (SQL Server 2012+)
sql
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
OFFSET 0 ROWS FETCH NEXT 3 ROWS ONLY;
Explanation:

OFFSET 0 ROWS starts from the first row

FETCH NEXT 3 ROWS ONLY limits to 3 rows

DISTINCT ensures we get unique salary values

Modern syntax but less flexible than window functions

6. Using a Self-Join (Traditional approach)
sql
SELECT DISTINCT e1.salary
FROM employees e1
WHERE (
    SELECT COUNT(DISTINCT e2.salary)
    FROM employees e2
    WHERE e2.salary >= e1.salary
) <= 3
ORDER BY e1.salary DESC;
Explanation:

For each salary, counts how many distinct salaries are greater than or equal to it

Only keeps salaries where this count is ≤ 3

Works in older SQL Server versions but less efficient

7. Using CROSS APPLY (Alternative approach)
sql
SELECT DISTINCT top_salaries.salary
FROM employees e
CROSS APPLY (
    SELECT DISTINCT salary
    FROM employees
    ORDER BY salary DESC
    OFFSET 0 ROWS FETCH NEXT 3 ROWS ONLY
) top_salaries;
Explanation:

Uses CROSS APPLY to join with a derived table of top salaries

Combines the distinct salary approach with the OFFSET-FETCH method

Recommendation:
For most scenarios, I recommend using the DENSE_RANK() approach (#3) as it:

Handles ties properly

Returns all employees with the top 3 salaries

Is clear and readable

Works in all modern SQL Server versions

If you specifically need exactly 3 rows regardless of ties, use the ROW_NUMBER() approach (#4).


Great! Since you're working with Microsoft SQL Server (MSSQL), here are all the possible ways to get the top 3 highest salaries, depending on how you want to handle duplicates (ties).

🟢 1. Using TOP with ORDER BY
sql
Copy
Edit
SELECT TOP 3 *
FROM Employees
ORDER BY Salary DESC;
✅ Simple and fast.

❌ Does not handle ties. You get exactly 3 rows, even if there’s a tie at the third position.

🟢 2. Using ROW_NUMBER() (Window Function)
sql
Copy
Edit
WITH Ranked AS (
    SELECT *, ROW_NUMBER() OVER (ORDER BY Salary DESC) AS rn
    FROM Employees
)
SELECT *
FROM Ranked
WHERE rn <= 3;
✅ Good if you want exactly 3 rows and are okay with breaking ties arbitrarily.

❌ Ties are not included beyond the 3rd row.

🟢 3. Using RANK() (to Include Ties)
sql
Copy
Edit
WITH Ranked AS (
    SELECT *, RANK() OVER (ORDER BY Salary DESC) AS rnk
    FROM Employees
)
SELECT *
FROM Ranked
WHERE rnk <= 3;
✅ Includes all employees tied in top 3 ranks.

E.g., if salaries are 9000, 8500, 8500, 8200, it will return 4 rows.

🟢 4. Using DENSE_RANK() (Alternative Tie Handling)
sql
Copy
Edit
WITH Ranked AS (
    SELECT *, DENSE_RANK() OVER (ORDER BY Salary DESC) AS drnk
    FROM Employees
)
SELECT *
FROM Ranked
WHERE drnk <= 3;
✅ Similar to RANK() but doesn't skip numbers after ties.

Example:

Salaries: 9000 (1), 8500 (2), 8500 (2), 8200 (3)

You still get 3 rank levels.

🟢 5. Using a Correlated Subquery (No Window Functions)
sql
Copy
Edit
SELECT *
FROM Employees E1
WHERE 3 > (
    SELECT COUNT(DISTINCT Salary)
    FROM Employees E2
    WHERE E2.Salary > E1.Salary
);
✅ Works without window functions.

✅ Includes ties.

❌ Slightly less readable; may be less efficient on large datasets.

✅ Summary – Which to Use?
Goal	Best Option
Simple top 3 rows	TOP 3 ORDER BY
Top 3 salaries including all ties	RANK() or DENSE_RANK()
Top 3 rows with no ties	ROW_NUMBER()
No window functions allowed	Correlated subquery


Find 3rd Highest Salary of the Employee (MSSQL)


SELECT MIN(salary) AS ThirdHighestSalary
FROM (
    SELECT DISTINCT TOP 3 salary
    FROM employees
    ORDER BY salary DESC
) AS temp;
Copy Data from One Table into Another (MSSQL)


INSERT INTO target_table (column1, column2, ...)
SELECT column1, column2, ...
FROM source_table;
👉 Ensure both tables have the same structure or match selected columns.

Delete Duplicate Data from Table (MSSQL)
(Assuming there's a unique column like ID)

WITH CTE AS (
    SELECT *, 
           ROW_NUMBER() OVER (PARTITION BY name, salary ORDER BY id) AS rn
    FROM employees
)
DELETE FROM CTE
WHERE rn > 1;

Find Duplicate Data in SQL Server

SELECT name, salary, COUNT(*) AS duplicate_count
FROM employees
GROUP BY name, salary
HAVING COUNT(*) > 1;


### **1. Tell me about yourself.**

Hello, my name is \[Your Name]. I have completed my \[Degree] from \[University Name]. I have a strong interest in software development and have experience working with technologies like \[e.g., Java, .NET, Python, React]. I am passionate about building efficient and scalable applications. During my academic and professional journey, I’ve worked on a few projects which helped me understand real-world problem-solving and teamwork.



### **2. Tell me more about the project you are currently working on.**


I am currently working on a \[name/type of project], which is \[brief project description]. The project aims to \[purpose of the project]. It involves technologies such as \[technologies used], and I am primarily responsible for \[your role, e.g., backend API development, frontend UI, database integration, etc.]. The project is being developed as part of \[team/organization/internship] and follows Agile methodology.

---

### **3. What role or features have you worked on in the project?**

**Answer:**
In the project, I worked as a \[role – e.g., backend developer], where I designed and implemented \[mention features – e.g., user authentication module, payment gateway integration, etc.]. I also participated in code reviews, testing, and deploying the features on our development servers. My focus was on writing clean, optimized, and reusable code.

---

### **4. Describe a challenge or specific task you faced in the project and how you solved it.**

**Answer:**
One of the challenges I faced was integrating a third-party API for \[feature]. The API documentation was unclear and outdated, which caused delays. I solved it by thoroughly debugging the requests, checking forums for similar issues, and contacting API support. Eventually, I was able to write a wrapper class that handled all the requests properly and added retry logic for failures.

---

### **5. What are your achievements and strengths?**

**Answer:**
Some of my key strengths include quick learning, problem-solving, and being a good team player. I take ownership of my work and enjoy finding efficient solutions to technical problems. As for achievements, I successfully completed a project where I reduced API response time by 40% through code optimization. I’ve also received appreciation for meeting tight deadlines and maintaining code quality.


---

1. What is Web API? What is the purpose of a Web API?
2. What are the advantages of Web API over WCF and Web Services?
3. What is REST and what does RESTful mean?
4. Is it possible to use WCF as a RESTful service?
5. What are HTTP verbs or HTTP methods?
6. How do you consume a Web API in a .NET MVC application?
7. What is the difference between Web API and MVC Controller?
8. What is Basic Authentication in Web API?
9. What is API Key Authentication in Web API?
10. What is Token-Based Authentication?
11. What is OAuth?
12. What is JWT Authentication?
13. What are the parts of a JWT token?
14. Where does the JWT token reside in the request?
15. How do you test a Web API? What tools are used?
16. What are the main return types supported in Web API?
17. What is the difference between `HttpResponseMessage` and `IHttpActionResult`?
18. What is Content Negotiation in Web API?
19. What is the `MediaTypeFormatter` class in Web API?
20. What are the response codes in Web API?
21. What is a URI?
22. What is a refresh token?
23. How do you handle exceptions in your project?
24. Can we use multiple `catch` blocks within a single `try` block?
25. What is the use of the `finally` block?

---

Let me know if you'd like **answers or explanations** for these questions too!



