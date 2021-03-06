## Notes

A big hurdle in fully understanding Javascript is that learning one part of the language requires that you have knowledge on another part of the language, and leanring that part of the language requires that you actually know about the original part of the language you were trying to learn. For that reason I picture javascript as a ring of knowledge, you start out just scambling to create the basic ring in your mind and then increase that rings diameter and solidity as you understand more. This course assumes you already assumes you most of this ring formed already, with perhaps a few gaps, but close. We will then fill out this vauge arc to make a string and complete circle. The following is audit on the main tenants of javascript that the rest of the course will be based off.

Javascript is object based. A Javascript program is a bunch of objects communicating in order to fullfill the programmers desired outcome. What is an object? It is a collection of zero or more properties, a property being a single key to value pair, and a set of attributes that control how these properties can be used. Object properties can hold other objects as their values or can hold primitive types as their values, primitive types just mean non-object types of data (meaning they have no properties attached to them). There are seven of these non-object primitive types: Numbers, BigInt, Strings, Undefined, Null, Boolean, and Symbol. Javascript has many built in objects that have various duties some examples are: the global object, the function object, the Math object, the RegExp object, and the Json object, among others.

Javascript objects can either have their own properties or they can also inherit properties. Inherited properties come from other objects linked from top to bottom with a prototype inheritance chain.

The function object

The "this" keyword refers to the context object. It allows you to perfrom functions against a paticular object depinting on the context of the fucntion the "this" keyword is found in. This gets rid of the need to pass around objects to functions as you can use the this keyword instead, this can mean clearer more readable code - as long as reader can understand how which object the context object is. The context object, "this", will depend in what is executed how at runtime. Everytime a function is run a new execution context for that function is created. 


typeof() can be used to see the data type, execpt for null as null was intended originally to represent the lack of an object, therefore making typeof(identifier) where var identifier = null consistent when identifier is expecting an object.

ECMAscript specifies normal and exotic objects. Normal objects are object with the standard internal slots and methods. Exoctic objects may override default implementations of internal methods.

Error objects: typically, when the spec says an error should be thrown, it only specifies the type of error, not the error message. 


Functions can become what are called constructor functions in Jasvascript. It is important for anyone coming from other languages to leave their pereption of how a contructor function should work at the door. A constuctor function in javascript is just a normal function modulated by the new operator. By convention a constructor function has a capital first letter (nothing to do with the language, but has become something JS developers have just collectivley decided to do to make it clear between themselves). The new operator creates a new object whos [[Prototype]] is set to the contsructurs .prototype property, the this value for the called function is set as that new object, if the constructor returns a non-null object then that object will be returned otherwise the new object i returned automatically.
https://2ality.com/2014/01/new-operator.html

Other ways to set the [[prototype]] value (also known as __proto__ - but this is vendor implemented and not spec compliant) is the Object.create() and Object.setPrototypeOf().

Array indexes are between 0 and 2^32-2 (4294967294)

Internal slots are not inherited

Super needs a home object

globalThis (EcmaScript2020) refers to the global environment across environment (like window in browsers and global in node.js)

--------------------------------------------

# Ultimate guide to JS Objects video script

(this video reflects the 2019 ECMAscript specification)

Ok so a common trope you hear in the Javascript world is that every thing is an Object... Is that right?
No!!

There are 8 types in JavaScript 
7 primitives:
*Boolean
*Null
*Undefined
*Number
*String
*Symbol
*BigInt (to be added to JS in ECMAscript2020)
and 
*Object

Primitives in the ECMAscript spec literally just means not an object! And an object is defined as a collection of properties...

Sometimes 

> Object description - object structure, property types, property attributes

Javascript objects are made up of:
1. A collection of properties, as well as a selection of property attributes for each respective property that can be set as boolean values - either true or false.
2. Internal Methods / Internal Slots


There are two types of properties: "data properties" and "accessor properties"
* a _data properties_ is the association of key - value pairs
* an _accessor properties_ is the association of a key with up to two accessor functions; a getter and a setter
For both, keys can either be string (even an empty string - "") or symbols.


Accessor properties 
Enumarable will default to true, as will the configurable attribute. 

To delete a property: delete obj.prop; delete obj["prop"]. The return value for this opertation is true unless the property's configurable attribute has been set to false, in which case the operation will return false.


Every object has a [[Prototype]] internal slot, this slot holds a reference to an Object or null value. 
When an attempt to access a property on an object is made the js engine of course attempts to find the key on that object, if it fails to find it the engine will move to the object in the [[Prototype]] reference and try to find a the key there and if so use that value. This makes a chain commonly called the prototype inheritance chain. You can set the prototype with Object.create and Object.setPrototypeOf, as well as obj.__proto__ (although __proto__ is not recommended). 
It can also be set with the help of the "new" operator and a function. A function used with the new operator is called a constructor function although there is nothing special about it from other functions it is just a normal function (by convention an uppercase first character is used to denote a function designed to be used with the new keyword - a constructor). Every function has a .prototype property. When new func() is called the a new object is created with its [[Prototype]] reference pointing to the functions .prototype key object reference. This object has a constructor property on it that points back to the constructor. This constuctor property is writable and configurable though so could be changed accidentaly or on purpose by other parts of the code base.





##Arrays
