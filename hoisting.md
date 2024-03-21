# Hoisting - Kéo lên / đưa lên

### Đưa ra các khai báo biến với "var" và khai báo hàm lên đầu phạm vi được khai báo

## Hoisting với "var" , "function declaration"

- Xét ví dụ sau:

```js
console.log(age); // undefined
console.log(fullName); // ReferenceError: fullName is not defined
var age = 16;
```

- Xét ví dụ sau:

```js
console.log(sum(6, 9)); // 15
function sum(a, b) {
  return a + b;
}
```

> Lưu ý: Phần khai báo được đưa lên, phần gán không được đưa lên. Khai báo với function auto đưa lên trên

## Hoisting với "let", "const"

- Xét ví dụ:

```js
{
  console.log(fullName); // ReferenceError: Cannot access 'fullName' before initialization
  let fullName = "Nguyen Van A";
}
```

- Xét ví dụ:

```js
console.log(test(10, 9));
const test = (a, b) => {
  return a - b;
};

// ReferenceError: test is not defined
```

> Lưu ý: Khai bao biến với "let", "const" khi được hoisted không được tạo giá trị và được đưa vào "Temporal Dead Zone"

## Bonus

- Xét ví dụ sau:

```js
const counter1 = makeCounter();

console.log(counter1()); // What's the output?

function makeCounter() {
  let counter = 0;

  return increase;

  function increase() {
    return ++counter;
  }
}
```
