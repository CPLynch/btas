##Queue
Ecmascript defines 2 mandatory queues the scriptJobs and promiseJobs, (the spec allows for implementation defined extra queues)

The Html spec define the event loop and the microtask queue. There are actually three types of event loop: window, worker, and worklet. Microtasks include the promiseJobs defined by ES.


https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/#process-nexttick
https://www.youtube.com/watch?v=PNa9OMajw9w
https://www.youtube.com/watch?v=zphcsoSJMvM
In node the event loop is phased like this: timers, pending callbacks, idle and prepare, poll, check, close callbacks. Then is starts again. It runs all jobs in each phase before moving on to the next one unless it hits a maximum number (this number is system dependant).
Node.js has process.nextTick() which has its own nextTick queue - this is always processed before the event loop continues on to the next phase. queueMicrotask for the Microtask queue performs the same function as the nextTick queue, just that nextTick is managed by node and microtask are mangaged by V8, both run before continuing on to the next phase of the event loop but nextTick queue is unwound first.
