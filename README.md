# GIT TUTORIAL

[Git docs](https://git-scm.com/docs/)

![enviroment](./git-workflow.jpg)

## Git init

`git init` Tạo một kho lưu trữ Git trống hoặc khởi động lại kho hiện có

## Git clone

`git clone` Sao chép một kho lưu trử Git và tạo một thư mục mơi

* Sao chép một remote repo:
  
```console
git clone https://github.com/Qaker-VN/Git-tutorial.git
```

## Git add

`git add` thêm nội dung file vào chỉ mục (staging)

```console
git add .            ## thêm nội dung tất cả các file
git add <file-path>  ## thêm nội dung của một file
```

## Git commit

Tạo một cam kết mới chứa nội dung hiện tại của chỉ mục (nội dung staging chưa được commit) và thông báo nhật ký mô tả các thay đổi.

* `git commit -a` tạo commit cho tất cả nội dung file chưa được commit trong chỉ mục vs show trình edit để viết message cho commit
* `git commit -m "msg"` tạo commit cho tất cả nội dung file trong chỉ mục chưa được commit kém với message
* `git commit -C <commit_ID>` tạo commit cho các nội dung file trong chi mục chưa được commit và Lấy message của commit_ID làm message cho commit mới
* `git commit -c <commit_ID>` Gần giống như -C, tạo commit cho các nội dung trong chi mục chưa commit và lấy message của commit_ID, show trình chỉnh sửa message
* `git commit --amend` các nội dung file trong chi mục chưa được commit sẽ được gộp chung vào commit cuối cùng trong git tree vs show trình edit để có thể thay đổi lại message. `git commit --amend -m "msg"` thay đổi nhanh message hoặc --no-edit để không show trình edit message và giữ nguyên message cũ  

## Git remote

`Làm việc với remote repository`

## Git push

`Đẩy code từ local repository lên remote repository`

## Git fetch

Lệnh git fetch tải về dữ liệu từ Remote Repo (kho chứa từ xa - trên server/dịch vụ lưu repo, các dữ liệu như các commit, các file, refs). Các dữ liệu này được lấy về và nó lưu vào kho chứa local (trong Repository - thư mục .git), nó không tác động gì đến thư mục đang làm việc (Working Directory - Workspace). Bạn dùng git fetch khi cần lấy dữ liệu từ remote để lưu trữ, theo dõi các commit người khác đã cập nhật lên server, để có được thông thông tin khác nhau giữa remote và local mà không ảnh hưởng đến luồng công việc bạn đang thực hiện

* Kho chứa của bạn tên origin, tải về tất cả thông tin của nó từ remote:

```console
git fetch origin
```

* hoặc

```console
git fetch all
```

* Tải về thông tin của một nhánh cụ thể từ remote repo:

```console
git fetch origin master
```

Sau khi tải về, để có thể khám phá sự khác biệt giữa local và remote bạn có thể xem trạng thái của thư mục làm việc, xem log của một nhánh local và log của nhánh remote ...

```console
git log --oneline origin/master # xem log nhánh master của remote origin
git log --oneline master        # xem log nhánh master của local origin
git status                      # xem log nhánh master của local origin
```

## Git pull

Lệnh `git pull` lấy về thông tin từ remote và cập nhật vào các nhánh của local repo. Git tải về thông tin từ remote và ngay lập tức merge cho nhánh đang làm việc. Lệnh `git pull` nó tương đương thi hành luôn hai lệnh `git fetch` và `git merge`

* Khó chứa remote của bạn tên origin, Kéo code từ remote repo về local repo

```console
git pull origin
```

* hoặc chỉ cụ thể tên branch

```console
git pull origin <name-branch>
```

## Git revert

`Hoàn lại code của commit trước đó, và tạo một commit mới`

## Git reset

`Xóa một commit`

## Git rebase

`Set một nhánh làm nhánh cơ sở (base) cho nhánh muốn rebase`

## Git rm

`git-rm - Remove files from the working tree and from the index`

## Git status

`git-status - Show the working tree status`

## Git log

`show commit log`

## Gitignore

## Tip

### Change commit message using `git rebase -i`

* `git log --oneline`

```console
59cdd77 (HEAD -> master) commit 4
cef8eac commit 3
1288a45 commit 2
a794f7d commit 1
```

* `git rebase -i HEAD~3` auto open editor

```console
pick 1288a45 commit 2
pick cef8eac commit 3
pick 59cdd77 commit 4
```

* select the commit you want to change the message, use editor to change pick --> reword

```console
reword 1288a45 commit 2
pick cef8eac commit 3
pick 59cdd77 commit 4
```

* save editor, auto switch new editor

```console
commit 2 

# Please enter the commit message for your changes. Lines starting
```

* modify message and save --> change commit message success
