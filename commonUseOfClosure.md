### two common use of closure
there are two common use of closure: pass function as parameter,pass function as return value

## pass function as parameter
```
function a1(){
    let a = 100;
    return function(){
        console.log(a)
    }
}
let a = 200;
let b = a1()
b();
// output 100;
```
Explanation:
In this example, the function a1 defines a local variable a (with a value of 100) and returns an inner function. The inner function forms a closure over a. When b is executed, it remembers the environment where it was defined, so it uses the a from a1, not the outer a = 200.



## pass function as return value 

```
function fn(cb){
    let a = 200;
    cb()
}
let a = 100;
function fn2(){
    console.log(a)
}
fn(fn2);
//output 100

```
Explanation:
Here, the function fn takes a callback function cb as a parameter. When cb is executed inside fn, it still retains its original scope from the outer environment where it was defined. In this case, fn2 is defined in the global scope, so it uses the global variable a = 100, not the a declared inside fn.


Why Both Results Are 100?
The key concept of closures is lexical scoping, meaning a function’s variables are resolved based on where the function is defined, not where it is called.

In the first example, the returned function remembers the variable a from its defining scope in a1 (value is 100).
In the second example, the function fn2 was defined in the global scope, so it uses the global variable a = 100, even though it's executed inside fn.
Closures ensure that functions “remember” the variables from their defining scope, regardless of where they are called.
