You have to look at the call site for the currently running function.

This by default if the "this" value is undefined then JavaScript binds it to the global object, unless it is running in strict mode then it remains undefined.
If a called from an object property (as a method) the "this" value is the object it is called from.
  If the object property reference is passed to another identifier (either as a a declaration or as an argument) end then called then it will no longer have the this value of the original object.
  Also if the method is called from a nested object (obj1.obj2.run()) then the this value is the object has that property (in this case obj2)
  
This can be bound explicitly useing call(), apply(), and bind() (bind - es5). bind() is hardbinding.
