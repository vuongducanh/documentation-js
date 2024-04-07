## Khhái niệm

### Javascript có hai loại type của value đó là Primitive types và Reference types

### 1. Primitive types (các kiểu dữ liệu nguyên thủy) bao gồm:

```js
undefined, null, boolean, number, string, Symbol;
```

> Khi bạn gán một biến với kiểu dữ liệu nguyên thủy vào biến nguyên thủy khác thì js sẽ lưu trực tiếp giá trị vào biến đó luôn mà không ảnh hưởng tới các biến khác

- Xem ví dụ

```js
let primitive = 10;
let anotherPrimitive = primitive;

primitive = 20;

console.log(primitive); // 20
console.log(anotherPrimitive); // 10
```
- Đó khi thay đổi giá trị của `primitive` sẽ không ảnh hưởng đến biến `anotherPrimitive`
- `primitive` và `anotherPrimitive` sẽ lưu ở hai ô nhớ khác nhau sẽ không ảnh hưởng đến giá trị của nhau




> Tài liệu gốc : [Link](https://codedamn.com/news/javascript/pass-by-reference-in-javascript)
