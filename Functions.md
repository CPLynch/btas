Constructors are functiono objects that create objects. The prototype property of a function object is a prototype object. A prototype object for property inheritance.

A function or "function object" is just an object with the [[Call]] internal slot and sometimes a [[Constructor]] internal slot. For this reason they are also known as callable objects.

[[Call]] internal slot description from the spec "Executes code associated with this object. Invoked via a function call expression. The arguments to the internal method are a this value and a list containing the arguments passed to the function by a call expression. Objects that implement this internal method are callable."

An agent is at any moment in time always has one running Execution Context. It also has an associated Execution Context Stack, a set of named job queues. Agents (browser tabs, web workers, etc) can share an executing thread (ie some browsers share a single executing thread accross multiple unrelated tabs) as long as the CanBlock internal boolean is false. 

All execution contexts have the following values in their record:
  code evaluation state
  the function object - allows the execution context to evaluate the code of the function object for that execution context
  As an alterantive to the function object a Script or Module record, otherwise null
  Realm record

Running execution contexts do not have to run to completion but can be suspended and restarted according to the specification. 
The running execution context has a "current realm Record" value and a "active function object" value. All execution contexts also have the state components: LexicalEnvironment, and VariableEnvironment



Agent Clusters are a set of agents that can comminicate by working on shared memory. (SharedArrayBuffer). Every agent belongs to exactly one agent cluster.

A Job: An abstract operation of running Javascript code once there is no running execution context and the execution stack is empty.
PendingJob is a request for future execution of a Job. A Job always runs to completion, but the execution of a job may enqueue further PendingJobs.

Each PendingJob Record has:
  Job name
  Argument value list
  A realm record - for initial excution context
  Script or module record for initial execution context
  
A Job Queue is FIFO. There are two types of Job Queues: ScriptJobs (script and modules, macrotasks) and PromiseJobs (async). ECMAscript doesn't specify whether jobs in the scriptJob queue or PromiseJobs should be run first, only that each queue must run FIFO. The HTML spec actually clarifies how these queues should be ordered: when the execution stack is completed the next scriptJob should be picked up, at the end of that scriptJob any promise jobs created by that script job should be completed before before the next script job is started - effectively the promisejobs are attached to the end of a parent script job. If there are no script jobs run all the promiseJobs even if the promise jobs add a new script job. This works the same way in node.js.

Other terminology used for ScriptJobs is: Event Queue, Queue, Message Queue. Typically

macrotasks: setTimeout, setInterval, setImmediate, requestAnimationFrame, I/O, UI rendering
microtasks: process.nextTick, Promises, Object.observe, MutationObserver

What are constructor functions? Just normal functions with a new operetor immediatly before. That's it. The new operator makes normal functions into constructors. What are often reffered to as constructor functions are just normal functions designed to be used with the new operator.

