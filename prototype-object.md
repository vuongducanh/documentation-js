# Prototype - Khung nguyên mẫu

```js
// Tạo một object theo đúng nghĩa đen
const mouse = {
  weight: 0.2,
  getWeight: () => {
    return this.weight;
  },
};

// constructor function
function Mouse(color, weight) {
  this.type = "mouse";
  this.color = color;
  this.weight = weight;
}

// Thêm thuộc tính sleep cho đối tượng Mouse
Mouse.prototype.sleep = function () {
  console.log("Sleeping...");
};

// Khởi tại một intance cho object mình vừa tạo
const mickey = new Mouse("black", 20);
mickey.sleep(); // sẽ log ra : Sleeping...
const jerry = new Mouse("pink", 40);
jerry.sleep(); // sẽ log ra : Sleeping...
```

## Tại sao không viết method `sleep` trong đối tượng `Mouse`

- Thực ra viết thì logic của nó vẫn đúng vẫn chạy ok
- Mình sẽ so sánh khi method `sleep` viết trong `Mouse` nhé

```js
function Mouse(color, weight) {
  this.type = "mouse";
  this.color = color;
  this.weight = weight;

  this.sleep = function () {
    console.log("Sleeping...");
  };
}

const mickey = new Mouse("black", 20);
mickey.sleep();
const jerry = new Mouse("pink", 40);
jerry.sleep();

// Đều log ra `Sleeping...` vì vậy mình sẽ so sánh method của mickey và jerry có giống nhau không nhé
console.log(mickey.sleep === jerry.sleep); // kết quả là false;
```
- Kết quả ra `false` vì khi khởi tạo intance qua từ khóa new Mouse và gán cho mickey , jerry thì method sleep nó sẽ chiếm hai vùng nhớ khác nhau tương ứng với hai đối tượng nên so sánh nó sẽ ra kết quả false

- khi mình khởi tạo nhiều đối tượng thì nó sẽ chiếm càng nhiều cùng nhớ trên RAM thì sẽ gây ra tốn tài nguyên để không bị tốn bộ nhớ thì dùng prototype

```js
function Mouse(color, weight) {
  this.type = "mouse";
  this.color = color;
  this.weight = weight;
}

// Thêm thuộc tính sleep cho đối tượng Mouse
Mouse.prototype.sleep = function () {
  console.log("Sleeping...");
};

const mickey = new Mouse("black", 20);
mickey.sleep();
const jerry = new Mouse("pink", 40);
jerry.sleep();

console.log(mickey.sleep === jerry.sleep); // kết quả là true;
```

- mickey và jerry đều có method sleep và nó đều trỏ đến prototype sleep cùng trỏ đến 1 ô nhớ

## Mục đính dùng prototype để tạo method và properties là gì:
- Tiết kiệm bộ nhớ: các method và properties được chia sẻ giữa tất cả các đối tượng được tạo ra từ cùng một prototype vì đối tượng chỉ cần tham chiếu tới prototype
- Tái sử dụng và mở rộng


# Array

```js
const array1 = [1, 2];
typeof array1 // 'object'
```

## Tại sao lại là `'object'` nhỉ
- Vì khi khai báo `[1, 2]` chỉ là cú pháp khai báo ngắn thôi
- Bản chất là js nó sẽ tự nhận diện và hiểu cú pháp này như cách tạo mảng kiểu new Array(1,2)
- Vì thế check typeof thì nó vẫn là object
- Cách viết [] chỉ giúp dễ đọc hơn thôi bản chất nó là new Array()
- Nó là object vì nó có prototype của Array.prototype như: push(), pop(), slice(), length ....




