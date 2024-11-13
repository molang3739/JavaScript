### When to Use === and ==

#### The == operator should only be used when comparing with null. In all other situations, use ===.

For example:



```
if(obj.a == null){}

```
is equivalent to:

```
if (obj.a === null || obj.a === undefined) {}

```
