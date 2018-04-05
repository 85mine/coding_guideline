Hướng dẫn về Coding Style - Coding Style Guide
==================

Bộ quy tắc này được tạo ra nhằm giảm bới những khó khăn trong việc đọc code
của người khác. Nó thực hiện điều đó bằng cách đặt ra những quy định hay gợi
ý về việc format PHP code.

[PSR-1]: https://github.com/wataridori/php-coding-standard-vietnamese/blob/master/PSR-1.md
[PSR-2]: https://github.com/wataridori/php-coding-standard-vietnamese/blob/master/PSR-1.md


1. PHP
-----------

- Code phải tuân theo "coding style guide" PSR [[PSR-1]] và PSR [[PSR-2]].

- Tóm lược một số style cơ bản cần ghi nhớ như sau :

  - Code không dùng tab, mà phải sử dụng **4 dấu cách làm indent**.

  - **Dấu mở ngặc nhọn** dùng khi khai báo class phải được viết ở **dòng mới** (không viết cùng dòng với phần khai báo tên class),
  và **dấu đóng ngoặc nhọn** của một class phải được viết ở **dòng mới** sau khi kết thúc body của class.
  - Tên Method **không được prefix bởi dấu gạch dưới `_`** để biểu thị tính protected hay private.

  - Tất cả method và biến đều phải khai báo theo **camelCase**

#### 1.1 Hướng dẫn config trong phpStorm

![alt text][logo]

[logo]: http://laraveldaily.com/wp-content/uploads/2015/06/phpstorm_psr2.png "Config phpStorm"
