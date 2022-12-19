# Frida Cheatsheet

## Native Lib

### Tamper pointer

```js
Interceptor.attach(Module.findExportByName(null, 'foo'), {
  onEnter: function (args) {
    console.log('foo called with argument: ', args[0]);
    var value = Memory.readPointer(args[0]);
    value = value + 1;
    Memory.writePointer(args[0], value);
  }
});
```
