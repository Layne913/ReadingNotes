# Clean Code

## Chapter 1: Clean Code
If developers write poor code, the productiviy decreases when time passes. The project become more and more messy, and there will be a day that the project just cannot continue.

The clean code is elegant, efficiency, simple, direct and readable.
The clean code means no duplication, one thing, expressivess, tiny abstraction.

"Clean code can be read, and enhanced by a developer other than its original author. It has unit and acceptance tests. It has meaningful
names. It provides one way rather than many ways for doing one thing. It has minimal dependencies, which are explicitly defined, and provides a clear and minimal API. Code should be literate since depending on the language, not all necessary information can be expressed clearly in code alone."

## Chapter 2: Meaingful Names
* The name should tell why it exists, what it does, and how it is used.
* The name should not be obscure and give the reader false clues on the variable or function. For example：If the name of a variable contains list, then the data structure of the variable should be list.
* Do not use the names that are meaningless (noise), for example a, b, c. 
* Do not use single-letter name in a large scope, since it will not be easy to locate/search. The length of a name should correspond to the size of its scope.  
* Class name should be noun/noun phrase, method name should be verb/verb phrase.
* One world per concept.

## Chapter 3: Functions
* The functions should be small.
* The blocks within if statements, else statements, while statements, and so on should be one line long. Functions should not be large enough to hold nested structures.
* FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL.THEY SHOULD DO IT ONLY.
* The statements within our function are all at the same level of abstraction. (logic, dom...)
* Open closed responsibilty: software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification. (We should strive to write code that doesn’t have to be changed every time the requirements change)  
  http://joelabrahamsson.com/a-simple-example-of-the-openclosed-principle/
* Use design pattern such as Abstract Factory, to make the structure clear. (Calculating the area of shapes: triangle, circle, rectangle should extend from shape class and implement their own area function.)
* The function should not hold three or more arguments, if it indeed needs that many arguments, these arguments might be able to wrapped into a class. 
The more the argumets the function has, the more difficult people will comprehend the code. Also, more difficult for testing.
The function shouldn't have flag argument(boolean argument), since the function will be conflicted with the single responsibility rule, it will handle true and false situation.
* If the function voilates the single responsibility rule, it might have some side effects which will influence the global.
* In general, output arguments should be avoided. If your function must change the state of something, have it change the state of its owning object. For example, report.appndFooter() is better than appendFooter(StrinigBuffer report) in this sense.
* Command Query Seperation: the function should change the state of an object or it  should return some information about that object. But not doing them together.
* Perfer Excption to Returning Error create a new file under the direcotry
* It is better to extract thee bodies of the try and catch blocks out into functions of their own.
* Accroding to single responsibilty rule,if the keyword try exists in a function, it should be the very first word in the function and that there should be nothing after the catch/finally blocks.
* Control/eliminate duplication.
* If the function voilates the single responsibility rule, it might have some side effects which will influence the global.
* In general, output arguments should be avoided. If your function must change the state of something, have it change the state of its owning object. For example, report.appndFooter() is better than appendFooter(StrinigBuffer report) in this sense.
* The function should change the state of an object or it  should return some information about that object. But not doing them together.

## Chapter 4: Comments
* Minimize Comment, use the code to explain themselves.
* Useful Comments
  Some comments for legal reasons such as copyrightand authorship statemnets are necessary to have.
  Comments for regular expression defines what expression it will be matched.
  Comments that make arguments or return value in a standard library clear are acceptable. (clarifying comment)
  Comments that warn they other developers some special situation are useful.
  Comments can also be used for amplify importance.
* Bad Comments
  Misleading, redundant, mandated, jurnal Comments, noise comments, commented out code...

## Chapter 5: Formatting
* Vertical Formatting
  Small files are usually easier to understand than large files are.
  Different thoughts should be seperated from each other with blank lines.
  Opennes seperates concepts, vertical density implies close association.
  Variables shoud be declared as close to their usage as possible. Instance variables, on the other hand, should be declared at the top of the class(JAVA).
  Dependent Function: if one function callls another, they should be veretically close, and the caller should be above the callee, if at all possible.
  The stonger the conceptual affinity two parts of code have, the less vertical distance there should be between them. Affinity might be caused because a group of functions perform a similar operation.
  The important, high level code comes first at the top, the detailed, low level  code comes then at bottom.
* Horizontal Formatting
  Horizontal limit for a line of code is 120 characters.
  To make the hierarchy of scope visible, we indent the lines of code. One level to the right of their 'parent'
* Team should have its own programing rules that every team member should apply.

## Chapter 6: Objeccts and Data Structures
* Hiding implementation (abstract/interface) allow users to manipulate the essence of the data,w ithout having to know its implementation.
* Object hide their data behind abstractions and expose functions that operate on that data. Data Structure expose their data and have no meaningful functions.
* The fundamental dichotomy between objects and data structure: 
  Procedural code (coding using data structures) make it easy to add new functions without changing the existing data structure.
  OO code (inheritance，interface), on the other hand, makes it easy to add new classes without changing existing functions.
  However, procedural code makes it hard to add new data structures/data type(eg.class), because all the functiosn must change. OO code makes it hard to add new functions because all the classes must change.
* The Law of Demeter says a module should not know about the innards of the objects it manipulates.:
  The method f of a class C should only call the methods of these
  -C
  -An object created by f
  -An object passed as an argument to f
  -An object held in an instance variable of C
  The method should not invoke methods on objects that are returned by andy of the allowed functions.
  Train wrecks: a.b().c().d(); looks like a train, and voilate the law of Demeter
* Hybrids structure: half object and half data structure. Difficult in both adding new data structure and adding new functions. Avoid  creating them.

## Chapter 7: Error Handling
* Use exceptions rather than return codes
* Define exception classes in terms of a caller's need.
  ????? If you throw a checked exception from a method in your code and the catch is three levels above, you must declare that exception in the ???? signature of each method between you and the catch. This means that a change at a low level of the software  can force signature changes on many higher levels. The changed modules must be rebuilt and redeployed, even though nothing they care about changed.
* Provide  Context with Exceptions
  Create informative error message which contains failed operation together with the type of the failure, and pass them along  with your exceptions.
  Types of error: by source; by type: device failures, network failures, or programming errors/
* When define exception classes, the biggest concern should be how they are caught.
* Wrapping a third party API will minimize dependencies upon it and easier for testing.
* Special case Pattern: you create a class or configure an object so that it handles a special case for you. (set default returns)
* Don't return null.Change the lower level code to try not return null, instead, it can return emptyList()..
* Don't pass null. We could create a  new exception type and throw it or use a set of assertations.
  When you do have pass a null, you can code with the knowledge that a null in an agrument list is an indication of a problem, and end up with far fewer careless mistakes.

## Chapter 8: Boundaries
* Keep the boundries clean: third party library and own code 
  Using boundarie object like Map, keep it inside the class, or close family of classes, where it is used. Avoid returning it from, or accepting it as an argument to, public APIs.
* Write tests for the third-party code we use. 
  In learning/integreting third-party code, we can write some tests to explore the understanding of the third-party code.
  A clean boundary should be supported by a set of outbound tests that exercise the interface the same way the production code does.
* Using code that doesn't yet exist







