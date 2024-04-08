## Khái niệm

### Javascript có hai loại type của value đó là Primitive types và Reference types

### 1. Primitive types (các kiểu dữ liệu nguyên thủy) bao gồm:

```js
undefined, null, boolean, number, string, Symbol;
```

> Khi bạn gán một biến có kiểu dữ liệu nguyên thủy cho một biến khác , Javascript sẽ lưu giá trị trực tiếp vào ô nhớ khác biệt và mọi thay đổi đối với một biến sẽ không ảnh hưởng đến biến kia

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

### 2. Reference types (các kiểu dữ liệu tham chiếu) bao gồm:

```js
Object, Array, Function
```

> Khi bạn gán một biến có kiểu dữ liệu tham chiếu cho một biến khác , Js không lưu giá trị đó riêng biệt mà lưu trữ một tham chiếu đến giá trị đọ Bất kỳ thay đổi nào được thực hiện thông hoa tham chiếu này sẽ ảnh hưởng đến giá trị ban đầu vì cả hai đều tham chiếu đến một vị trí vùng nhớ

- Xem ví dụ

```js
let obj = { value: 10 };
let anotherObj = obj;

obj.value = 20;

console.log(obj.value); // 20
console.log(anotherObj.value); // 20
```

- Đó như bạn đấy thay đổi thuộc tính `value` của Object `obj` thì biến `anotherObj` cũng bị thay đổi vì cả hai `obj` và `anotherObj` đều tham chiếu đến giá trị ```{ value: 10 }`


> Tài liệu gốc : [Link](https://codedamn.com/news/javascript/pass-by-reference-in-javascript)
