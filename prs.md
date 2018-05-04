Hướng dẫn sử dụng tool support coding chuẩn PSR
==================

### Cài đặt

- Copy nội dung từ file pre-commit.sh.windows/linux tương ứng với
- Chạy ```composer install``` để cài đặt.

# Tiến hành commit
```java
git add .
git commit
```
Sau khi commit, hệ thống sẽ bắn lỗi ra console nếu có + kèm sửa lỗi.
Tiến hành fix lỗi và commit thêm 1 commit với nội dung :
```
[PRS-FIX] 20180503 //20180503 là ngày hiện tại
```
# Hướng dẫn sửa lỗi PSR

```
phpcbf /path/of/file #Tự động sửa 1 phần
phpcs /path/to/file #Check lỗi
```
Sau khi sửa lỗi thì tiến hành commit lên
