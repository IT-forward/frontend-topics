
# JavaScriptda funksiya turlari

JavaScriptda 10 xil ko'rinishdagi funksiya turlari bor. Ularning nomi va yozilishini birin ketinlik quyida ko'rishingiz mumkin👇:

### Declaration function

```js
    function sum(a,b) {
        return a + b;
    }
```

### Expression function

```js
    const sum = function sum(a,b) {
        return a + b;
    }
```

### Arrow function

```js
    const sum = (a,b) => {
        return a + b;
    }

```

### Async function

```js
    async function sum(a,b) {
        return await a + b;
    }
```

### Generator function

```js
    function *sum(a,b) {
        yield a + b;
    }
```

### Constructor function

```js
    new Function('a', 'b', 'return a + b;')
```

### Exported function

```js
    // Default exports
    export default function(a,b) { return a + b; }
    // Named exports
    export function sum(a,b) { return a + b; }

```

### Object property function

```js
    const object = {
        sum: function(a,b) { return a + b; }
    }
```

### Object dynamic property function

```js
    const functionName = 'sum';
    const object = {
        [functionName] : function(a,b) { return a + b ;}
    }
```

### Object dynamic property getter/setter function

```js
    const functionName = 'answer';
    const object = {
        get [functionName]() { return 21; },
        set [functionName](value) { /*   */ }
    }
```