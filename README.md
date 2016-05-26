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
* The function should change the state of an object or it  should return some information about that object. But not doing them together.
* 


