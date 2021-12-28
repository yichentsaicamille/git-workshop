# 12/25 Node.js 上課筆記 & 心得

### 學習終端機指令

"我用 git.bash 寫指令，就可以練習 Linus 寫法"

```
. 現在的檔案夾位置
.. 上一層案夾
~ 我的目錄，就是目前這個使用者的目錄
touch a.txt 建立新檔案
cd 切換目錄
pwd 顯示目前所在路徑
ls 列出目前檔案夾所有檔案
mkdir 建立新資料夾
cp 複製檔案
mv 移動檔案
rm 刪除檔案
clear 清除bash內容
cat a.txt 檢視檔案內容(貓一下)
rm -rf * 刪除全部資料(很嚴重不可亂用!!)
```

## 進入 git

### 任務一 : 安裝 git

### 任務二 : 設定環境變數

```bash
$ git config --global user.name "yichentsaicamille"
$ git config --global user.email "a0983936190@gmail.com"

# 可以進code修改名稱
code ~/.gitconfig

# 確定設定的內容
$ git config --list

# cat 印出檔案內容
cat ~/.gitconfig

# 指令簡寫
[alias]
	co = checkout
	br = branch
	ci = commit
	st = status
        lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cd) %C(bold blue)<%an>%Creset' --abbrev-commit --date=iso
	l = log --oneline --graph
        la = log --all --oneline --decorate --graph
```

### 任務三 : 建立 repo

```bash
# 初始化一個檔案夾，讓git可以管理
$ git init
```

### 任務四 : git 新增、修改、刪除檔案

```bash
#查看git狀態
$ git status
$ git st

# 把檔案加入
$ git add test.txt

# 提交這次的修改
$ git commit -m "正確填寫這次 commit 的資訊"
$ git ci -m "正確填寫這次 commit 的資訊"

# 檢視這次修改的差異
$ git diff

# 已經加入過的檔案，又有修改的話，一樣要再 add 一次，才可以 commit
$ git add test.txt
$ git ci -m "xxxx"
# 針對已經加入過的檔案，可以直接用以下指令提交
$ git ci -am "xxxxx"

# 可以「反悔」加入暫存區
$ git restore --staged test.txt

# 反悔剛剛的修改
$ git restore test.txt

# 查看提交紀錄
$ git log

# 查看特定檔案的紀錄
$ git log test.txt

# 查看檔案修改細節
$ git log -p test.txt

# 可以針對 commit 訊息做搜尋
$ git log --grep="delete"

# 查看內容是誰編寫的
$ git blame test.txt
# blame有責怪意思xd
```

Q. 多久（寫多少程式）應該 commit 一次？

A.「團隊一致性」，原則上是盡量小、但要完整

###### 下班前請先 commit 一次

- 看進度
- 萬一電腦/人出問題

###### github 主要為工程師"個人"社群 & 作品集

\*\*面試前請先整理，還有 commit message 不要亂寫

### 任務五 : 建立分支與合併

```bash
# main
git branch -M main

#分支
git branch feat-login
git br feat-login

# 切換分支 （新版）
git switch <分支名稱>

# 合併分支
# 1. 切換回 main 分支
git switch main
# 2. 把 feat-login 合併進來
git merge feat-login

# 本地的分支推送到 github 上面去
git push -u origin feat-login

# 第二次之後只要 git push 就行了
```

###### [提醒]

「盡量」避免衝突  
\*\*可以頻繁地 merge 你的功能分支 （當然以保持完整性為前提）

---

#### 實務講解

##### SCRUM

- sprint

  1. 通常是 2 - 4 週
  2. 假設 srpint 是 2 週  
     -> 每兩週就要產出可以 demo 的成果  
     -> 做錯的損失比較少  
     -> 盡快回應市場變化  
     -> 每兩週就會改善

- 反省會議：

  - 這個 sprint 當中，有沒有哪些地方做得好的？ --> 持續加強好的地方
  - 這個 sprint 當中，有沒有哪些地方做得不好的？ --> 怎麼改善？
  - 感謝誰...

- PM: 如時如質如預算  
  時間 vs 品質 vs 範疇  
  –> 通常會犧牲品質 （通常犧牲工程師）

###### \*\*SCURM 就是希望維持時間、品質，用範疇的變動來討論

---

### 任務六 : 建立 Github 帳號

### 任務七 : 建立 github repo

### 任務八 : 撰寫 readme

```
[markdown語法] (https://markdown.tw/)

# 標題 --> h1

## 副標題 --> h2

### 小標題 --> h3

- 第一點
	- 第一小點
- 第二點

> 這是引言

```

markdown 語法參考:
https://gist.github.com/billy3321/1001749662c370887c63bb30f26c9e6e

### 任務九 : 了解 git flow

#### pull requests

在 develop / main / production ..等團隊分支上，不會直接下 merge 指令，通常都會在 github 上發 pull requests，然後請同事幫忙 review，同事 review 完成之後，才會按下 merge。

#### code review

檢查別人的程式碼？ --> 確保程式跟專案的品質

- coding style 是否有符合規範
- 功能開發的是否符合需求
- 測試功能是否正確
  - 有可能是用眼睛看
  - 可能需要在本機切換到這個分支執行看看
- 效能？安全性？...
- 對事不對人

#### [重點]

及早發現問題，這樣處理問題的成本才會低！

# 12/26 Node.js 上課筆記 & 心得
