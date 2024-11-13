### When to Use === and ==

#### Use the == operator only when checking for null or undefined. In all other cases, use === for strict equality.

For example:



```
if(obj.a == null){}

```
is equivalent to:

```
if (obj.a === null || obj.a === undefined) {}

```
