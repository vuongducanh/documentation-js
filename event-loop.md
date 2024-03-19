# Event Loop - Vòng lặp sự kiện trong javascript

## Như chúng ta đã biết thì javascript chạy single-threaded vậy tại sao nó lại chạy single-threaded thì chúng ta cùng đi tìm hiểu về event loop

## Event loop hoạt động như thế nào có các ý chính mình cần đi vào là:

- Heap
  - Cái dùng để lưu trữ các đối tượng trong javascript như object, string, array, đối tượng qua từ khóa new và được lưu trong RAM của máy , heap nó tự động cấp phát bộ nhớ cho các đối tượng trên
  - Ví dụ head cấp phát cho một tối tượng qua từ khóa new
    ```js
    let obj2 = new Person("Jane", 25);
    ```
  - Khi đối tượng được gán giá trị là `null` thì bộ thu gom rác sẽ quét qua heap và thu thôi bộ nhớ được cấp phát cho chúng
- Call stack
  - Xử lý code đồng bộ và thực thi
  - Dùng để thực thi chạy luôn các câu lệnh
- Callback queue
  - Hàng đợi chạy sau khi được đẩy từ web api xuống
- Event Loop
  - Có nhiệm vụ check xem call stack đang trống không nếu trống thì bốc thằng đầu tiên trong queue lên call stack
- Web api/ browser apis
  - xử lý bất đồng bộ
  - Các hàm như `setTimeout`, `setInterval`, `fetch` ...
  - Chờ đếm thời gian xong sẽ đẩy xuống callback queue

 ## Lý thuyết là như thế chúng ta đi vào ví dụ:
 - Cho ví dụ
```js
  setTimeout(function log1() {
    console.log(1) // 1
  }, 3000);

  console.log(2); // 2

  setTimeout(function log3() {
    console.log(3) // 3
  }, 0);

  console.log(4); // 4

  // Chương trình khi chạy sẽ log ra lần lượt là 2,4,3,1
```

## Giải thích cách event loop hoạt động ở đoạn code trên
> Note: Javascript chạy code từ trên xuống dưới


- Step 1: chạy đoạn code:
  ```js
    setTimeout(function log1() {
      console.log(1) // 1
    }, 3000);
  ```
  - Giải thích: đoạn code này có setTimeout (một web apis) chạy bất đồng bộ , vì nó là một web api nên nó sẽ đếm thời gian xong 3 giây rồi sẽ push vào callback queue, push cái function vào thôi
- Step 2: chạy đoạn code
  ```js
    console.log(2);
  ```
  - Giải thích: đoạn code này là đồng bộ cho nên nó chạy luôn vào call stack và thực thi luôn in ra màn hình số 2

- Step 3: chạy đoạn code

  ```js
    setTimeout(function log3() {
      console.log(3) // 3
    }, 0);
  ```

  - Giải thích: đoạn code này có setTimeout (một web apis) chạy bất đồng bộ , vì nó là một web api nên nó sẽ đếm thời gian xong 0 giây rồi sẽ push vào callback queue, push cái function vào thôi

- Step 4: chạy đoạn code:
  ```js
    console.log(4);
  ```
  - Giải thích: đoạn code này là đồng bộ cho nên nó chạy luôn vào call stack và thực thi luôn in ra màn hình số 2
- Step 5: event loop sẽ check xem trong call stack có đang trống không
  - Nếu trống thì sẽ bốc từ callback queue lên call stack. bốc thằng đầu tiên và thực thi hàm trong call stack

Referential document: <a href="https://www.jsv9000.app/" target="_blank">jsv9000</a> or
<a href="http://latentflip.com/loupe/" target="_blank">latentflip</a>