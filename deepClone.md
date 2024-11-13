#### Implement deepClone manually


##### Reason:
Reference types will share the same address, so when we use = operator, if there is modification on the new object, the value on the old object will change too.


#### Solution
Iterate the Object recursively. If there is reference type, we create a new one and copy all the value type to the new reference type.


```

function deepClone(obj = {}) {
    // null can't be treated as object
    if (typeof obj != "object" || obj === null) {
        console.log(obj, "obj");
        return obj;
    }
    let result;
    // create a new reference type
    if (obj instanceof Array) {
        result = [];
    } else {
        result = {};
    }
    for (let key in obj) {
        // make sure key is not on prototype
        if (obj.hasOwnProperty(key)) {
            result[key] = deepClone(obj[key]);
        }
    }
    return result;
}
let obj1 = { x: 100, y: 200, z: [1, 2, 3], c: null };
let obj2 = deepClone(obj1);
console.log(obj2);
obj2.x = 102;
console.log(obj2, obj1);

```
