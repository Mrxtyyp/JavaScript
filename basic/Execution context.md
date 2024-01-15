## Execution context type

1. global execution context
   Any context that is not inside a function is global execution context. it points to the window object. There is only one number in the program.
2. function execution context
   When a function is called, a function execution context will be created, there has any number of the function execution context.
3. eval function execution context
   The code executed in the eval function, and it have its own context. It uses very little.

## Execute the context stack

1. The JavaScript uses the execution context stack to manage the execution context.
2. JavaScript executes code, it first encounters the global code, creates a global execution context, and pushes it onto the execution stack. Whenever a function call is encountered, a new execution context is created for that function and pushed onto the top of the stack. The engine then executes the function at the top of the execution context stack. After the function has finished executing, the execution context is popped off the stack, and the engine continues to execute the next context. Once all the code has been executed, the global execution context is popped off the stack.

## Create an execution context

1. creation phase
   a. this binding
   b. create lexical envirment component
   c. create variable envirment component
2. execution phase
   a. variables allocated and The code executed.
