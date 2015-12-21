# eventemitter.js

This provides an API like node.js's EventEmitter for the web.

# Usage

First, import eventemitter.js using a script tag:

```html
<script src="event_emitter.js"></script>
```

Next, subclass EventEmitter like this:

```js
function MyClass() {
  window.EventEmitter.call(this);
  // Your initialization here...
}

MyClass.prototype = Object.create(window.EventEmitter.prototype);
```

If you wish to use multiple inheritance, you can use `EventEmitter.makeSubclass(proto)` to add the EventEmitter prototype to an existing prototype:

```js
function MyFancyClass() {
  EventEmitter.call(this);
  // Other superclass calls...
  // Your initialization code...
}
MyFancyClass.prototype = Object.create(SomeOtherBaseClass.prototype);
window.EventEmitter.makeSubclass(MyFancyClass.prototype);
```

An EventEmitter implements the following methods:

 * \[function\] listeners(name) - return all the listeners for an event name.
 * void addListener(name, listener) - add a listener for the given event.
 * void removeListener(name, listener) - remove a listener, given its name and handler.
 * void on(name, listener) - alias for addListener.
 * void once(name, listener) - register a listener which will be called once for the event. You will not be able to remove the listener through removeListener.
 * void removeAllListeners(\[name\]) - remove all of the listeners. You may supply a name, in which case only listeners for that name will be removed.
 * void emit(name, \[arguments\[, ...\]\]) - trigger all the listeners for the given name. If you specify arguments, they will be passed to all of the listeners as arguments.
