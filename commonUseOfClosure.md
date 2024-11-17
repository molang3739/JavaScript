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
console.log(b());
```

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

```

both answer are 100, why? the first one is easy to understand.
the basic concept of closure is the variable will be defined  by the nearest definenation . In the second demo .cb is excuted in fn ,but it's definenation is  in the outer of fn.which is 
```
a = 100 
```
so the result is 100;