## Understanding of this object

this is an attribute in the execution context that points to the object that last called this method. In actual development, the direction of this can be determined by four call modes.

● the first is function call mode when a function is not an object property and is called directly as a function, this point to the global object.

● the second is method call mode , if a function is called as a method of an object, this point to the object.

● the third is constructor call mode , if a function is called with new, a new object is created before the function is executed. this point points to the newly created object.

● the fourth is apply, call, and bind call modes , all three methods can display this direction of the specified calling function. The apply Method receives two parameters: an object bound to this parameter and an array of parameters. The parameters received by the call method. The first parameter is the object bound to this method, and the other parameters are the parameters passed into the function execution. In other words, when using the call() method, the parameters passed to the function must be listed one by one. The bind method returns a new function that is bound to the input object by passing in an object. this direction of this function will be changed except when new is used.

Among these four methods, the constructor call mode has the highest priority, followed by the apply, call, and bind call modes, followed by the method call mode, followed by the function call mode.
