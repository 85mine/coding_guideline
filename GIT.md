Quy trình sử dụng git
==================
- Tạo project
- Project phải có tối thiểu 2 branch
  - ```master```
  - ```develop```

> *Các branch này phải được bảo vệ chống xóa và push -f.*

### Khởi tạo branch phát triển của task

```Tạo một "feature branch" từ latest "develop"```.

```git
git checkout develop
git pull
git checkout -b feature/new_feature # thay thế bằng task
```

# Commit
```java
git add .
git commit
```
Sau khi hoàn thành việc phát triển, rebase và tạo pull request.

```git
git fetch
git rebase -i origin/develop # Nhớ bỏ đi commit không cần thiết.
git push -f
```
# Tạo pull request mới
Trường hợp nhiều thành viên cùng tham gia vào feature

```
- git checkout -b feature/new_feature/my_part # tạo branch cho task của bạn.
```

Sau khi hoàn thành, tạo pull request và gửi cho phụ trách chung để merge. Nhớ bỏ đi commit không cần thiết.

```
git fetch
git rebase -i feature/new_feature # Nhớ bỏ đi commit không cần thiết.
git push -f
```
# Merge vào develop
Khi toàn bộ công việc đã xong, team leader phụ trách việc tạo và gửi pull request

```
git checkout feature/new_feature
git rebase -i origin/develop # Nhớ bỏ đi commit không cần thiết.
git push -f
```

# Release
Tạo ``release branch``.

```
git checkout develop
git pull
git checkout -b release/v1.5
git push -u origin release/v1.5
```
Gửi pull request đến reviewer

## Fixbug
```
git add .
git commit
```
Tiến hành merge tới master sau khi fixbug

```
git checkout master
git merge --no-ff release/v1.5 # --no-ff là bắt buộc.
git push
```
Merge lại vào develop sau khi fixbug

```
git checkout develop
git merge --no-ff release/v1.5 # --no-ff là bắt buộc.
git push
```
Set "tag" cho master
```
git checkout master
git tag -a "v1.5" -m "released on 15 April 2017" HEAD
git push --tags
```
# Revert release
Nếu sai sót trong quá trình release, hãy revert nó.
```
git checkout master
git revert -m 1 a4tsdfgq345 # a4tsdfgq345 là merge commit của release branch
git push
```
# Hotfix
Tạo ``hotfix`` branch từ ``master``.
```
git checkout master
git pull
git checkout -b hotfix/black_bug
```
Apply fix
```
git add .
git commit
```
Sau khi fix xong, merge vào master
```
git checkout master
git merge --no-ff hotfix/black_bug # --no-ff là bắt buộc.
git push
```
Sau khi hotfix đã được apply, nhớ merge lại vào develop để cập nhật thay đổi
```
git checkout develop
git merge --no-ff hotfix/black_bug # --no-ff là bắt buộc.
git push
```

Ghi chú :
- Các commit đều phải ghi rõ ràng làm gì.
- Tất cả các pull request chứa commit thừa thãi hoặc vô nghĩa sẽ bị reject ngay.
- Trong quá trình review đừng push -f cái gì lên
- Tôn trọng nguyên tắc ``Một feature, một pull request``.

Tại sao :

- --no-ff là bắt buộc : Đảm bảo rằng có thể truy vế được các commit nào liên quan đến nhau khi đã merge vào master
