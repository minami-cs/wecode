# git 명령어 정리

## 1. git init

> git을 사용한 버전 관리를 시작하기 위해 git 저장소를 생성/초기화하는 명령어

```bash
User@DESKTOP-TLFM8CE MINGW64 ~/Desktop/test/wecode (master)
$ git init
Initialized empty Git repository in C:/Users/User/Desktop/test/wecode/.git/
```

- `git init`에서 `init`은 initiate 즉, 초기화하다, 시작하다라는 뜻을 가진 단어이다.
- `git`은 버전 관리를 위해 사용하는 일종의 프로그램이고, 이를 이용하려면 버전 관리를 원하는 디렉토리에 가장 먼저 `git 저장소`를 생성해야 하기 때문에 `git init` 명령어를 입력해야 한다.
- `git init`을 입력하면 `.git` 이름의 숨겨진 디렉토리가 생성되고, 터미널의 `bash` 환경에서는 경로 뒤에 `(master)`라는 브랜치 이름이 나타난다.

## 2. git add

> git 저장소에서 일어난 변경사항을 임시 저장!

```bash
User@DESKTOP-TLFM8CE MINGW64 ~/Desktop/test/wecode (master)
$ git add .
```

- `git add`는 `git`으로 관리되는 해당 저장소 안의 파일들에 일어난 변경사항을 `staging area`에 저장하는 명령어로, 이메일이나 블로그 등 온라인으로 글을 작성하다가 중간에 임시 저장해주는 것과 비슷하다.
- `git add` 뒤에는 현재 디렉토리 전체를 뜻하는 `.` 외에도 특정 파일이나 폴더명을 직접 명기해서 원하는 파일이나 폴더만 add하는 것도 가능하다.
- **staging area**: commit으로 기록하려는 파일들의 목록

## 3. git commit

> git 저장소에서 일어난 변경사항들을 버전으로 기록!

```bash
User@DESKTOP-TLFM8CE MINGW64 ~/Desktop/test/wecode (master)
$ git commit -m 'Add: test.js 파일 생성'
[master (root-commit) aae5914] Add: test.js 파일 생성
 1 file changed, 9 insertions(+)
 create mode 100644 test.js
```

- `git commit`은 `git add`로 저장해둔 변경사항을 버전으로 기록하는 명령어이다.
- `-m` 옵션을 사용해서 커밋 메시지를 작성하는 것이 일반적이다.
- 커밋 메시지는 지금 하나의 버전으로 기록하려는 코드의 이력을 잘 나타낼 수 있도록 작성해야 한다.

## 4. git status

> git 저장소의 현재 상태를 확인하는 명령어

```bash
User@DESKTOP-TLFM8CE MINGW64 ~/Desktop/test/wecode (master)
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test.js

nothing added to commit but untracked files present (use "git add" to track)
```

- `git 저장소`의 변경사항들이 add 혹은 commit 되었는지 상태를 확인할 수 있어서 자주 쓰이는 명령어이다.
- 현재 내가 작업하고 있는 `branch`의 변경사항의 상태에 대해 알 수 있다.

## 5. git remote

### 5-1. git remote add origin ${주소}

> _github_같은 원격 저장소의 주소를 _origin_이라는 이름으로 추가할 때 사용하는 명령어

- 로컬에서 관리하던 `git 저장소`에 `git 원격 저장소`를 연결하여 사용하기 위해서는 반드시 원격 저장소의 주소를 추가해주어야 한다.

- 연결된 `git 원격 저장소`를 확인할 때에는 아래의 명령어를 사용한다.

  ```bash
  User@DESKTOP-TLFM8CE MINGW64 ~/Desktop/test/wecode (feature/README)
  $ git remote -v
  origin  https://github.com/minami-cs/wecode.git (fetch)
  origin  https://github.com/minami-cs/wecode.git (push)
  ```

### 5-2. git remote rm origin

> 기존에 _origin_이라는 이름으로 연결되어 있던 원격 저장소의 주소를 제거하는 명령어

```bash
git remote rm origin
```

- 원격 저장소의 주소를 잘못 연결했거나 원격 저장소의 주소를 변경하고 싶을 때에는 기존에 추가되어 있던 원격 저장소와의 연결을 제거해줘야 한다.

## 6. git push origin ${브랜치명}

> 연결된 원격 저장소에 해당 브랜치를 업로드하는 명령어

```bash
User@DESKTOP-TLFM8CE MINGW64 ~/Desktop/test/wecode (master)
$ git push origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 351 bytes | 351.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/minami-cs/wecode.git
 * [new branch]      master -> master
```

- `git remote add` 명령어로 추가해둔 원격 저장소에 해당 브랜치를 업로드할 때에 사용한다.
- `git push -u origin ${브랜치명}`으로 `-u` 옵션을 주게 되면 이후에 `git push`만 입력해도 해당 브랜치를 원격 저장소에 push할 수 있다.

## 7. git checkout ${브랜치명}

> 다른 브랜치로 이동할 때 사용하는 명령어

```bash
User@DESKTOP-TLFM8CE MINGW64 ~/Desktop/test/wecode (master)
$ git checkout -b feature/README
Switched to a new branch 'feature/README'
```

- `-b` 옵션을 주면 뒤에 입력한 브랜치명으로 새로운 브랜치를 만들어서 새로 만들어진 해당 브랜치로 바로 이동할 수 있다!
