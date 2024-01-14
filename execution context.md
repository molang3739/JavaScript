
## Understanding the execution context 
 
 1. Execution context type
    
（1）global execution context

Anything that is not inside a function is a global execution context. It first creates a global window object and sets the value of this object to be equal to this global object. A program has only one global execution context. 

（2）function execution context

When a function is called, a new execution context is created for the function. The context of the function can be as many as possible. 

（3）* * eval * * function execution context  

the code executed in the eval function has its own execution context. However, the eval function is not often used and is not introduced. 


## 2. Execute the context stack

● the JavaScript engine uses the execution context stack to manage the execution context.

● when the JavaScript executes the code, it first encounters the global code, creates a global execution context and presses it into the execution stack. Whenever a function call is encountered, it creates a new execution context for the function and presses it into the top of the stack. The engine executes the function at the top of the execution context stack. After the function execution is completed, the execution context pops up from the stack and continues to execute the next context. After all the code is executed, the global execution context pops up from the stack.

```
let a = 'Hello World!';
function first() {
  console.log('Inside first function');
  second();
  console.log('Again inside first function');
}
function second() {
  console.log('Inside second function');
}
first();
//order of excution
// second()  first()
```
## 3. Create an execution context 

there are two phases to create an execution context: creation phase and execution phase 


### 1）creation phase 
 （1）this binding 
● 
in the context of global execution, this point to a global object (window object) 

● 
in the context of function execution, this point depends on how the function is called. If it is called by a reference object, this is set to that object, otherwise the value of this is set to global object or undefined 

###（2）create lexical environment components 

● 
lexical environment is a kind identifier -- Variable mapping the identifier refers to the variable/function name, and the variable is a reference to the actual object or raw data.

● 
the lexical environment has two internal components: bold Style : environment recorder: used to store the actual location of variable function declarations references to external environments : you can access the parent scope. 

###（3）Create a variable environment component

● 
the variable environment is also a lexical environment. Its environment recorder holds the binding relationship created in the execution context of the variable declaration statement. 

### 2）execution phase


At this stage, variables are allocated and the code is executed. 


In short, the execution context refers:


Before executing a little JS code, you need to parse the code. When parsing, a global execution context is created. First, the variables and function declarations to be executed in the code are taken out. The variables are assigned to undefined first, and the functions are declared to be available. After this step is completed, the formal execution procedure is started. 


Before a function is executed, a function execution context is also created, which is similar to the global execution context. However, this, arguments, and function parameters are added to the function execution context. 

● 
global Context: variable definition, function declaration 

● 
function context: variable definition, function declaration, this , arguments
