
```js run
let user = {
  name: "John"
};

function wrap(target) {
  return new Proxy(target, {
    get(target, prop, receiver) {
      if (prop in target) {
        return Reflect.get(target, prop, receiver);
      } else {
        throw new ReferenceError(`Property doesn't exist: "${prop}"`)
      }
    }
  });
}

user = wrap(user);

alert(user.name); // John
<<<<<<< HEAD
alert(user.age); // ReferenceError: Property doesn't exist "age"
=======
alert(user.age); // ReferenceError: Property doesn't exist: "age"
>>>>>>> c56e6a57ac3497aab77128c5bfca13513980709b
```
