## You should know the answers to these questions:
### Can you explain how refactoring differs from plain coding?
### Can you tell the difference between Corrective, Adaptive and Perfective maintenance? And how about preventive maintenance?
### Can you name the three phases of the iterative development life-cycle? Which of the three does refactoring support the best? Why do you say so?
### Can you give 4 symptoms for code that can be “cured” via refactoring?
### Can you explain why add class/add method/add attribute are behaviour preserving?
### Can you give the pre-conditions for a “rename method” refactoring?
### Which 4 activities should be supported by tools when refactoring?
### Why can’t we apply a “push up” to a method “x()” which accesses an attribute in the class the method is defined upon (see Refactoring Sequence on page 27–31)?

## You should be able to complete the following tasks
### Two classes A & B have a common parent class X. Class A defines a method a() and class B a method b() and there is a large portion of duplicated code between the two methods. Give a sequence of refactorings that moves the duplicated code in a separate method x() defined on the common superclass X.
### What would you do in the above situation if the duplicated code in the methods a() and b() are the same except for the name and type of a third object which they delegate responsibilities too?
### Monitor the technical debt of you bachelor capstone project.

## Can you answer the following questions?
### Why would you use refactoring in combination with Design by Contract and Regression Testing?
### Can you give an example of a sequence of refactorings that would improve a piece of code with deeply nested conditionals?
### How would you refactor a large method? And a large class?
### Consider an inheritance relationship between a superclass “Square” and a subclass “Rectangle”. How would you refactor these classes to end up with a true “is-a” relationship? Can you generalise this procedure to any abusive inheritance relationship?