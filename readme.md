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

![](https://i.imgur.com/iYbhwu4.png)

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

![](https://i.imgur.com/1IHb1J1.png)

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

![](https://i.imgur.com/rV7GdFn.png)

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

## 心得

上了一堂很有意義的課，可以感受到老師教學的熱忱，喜歡實務和實作交錯著上，上得很開心也覺得有練習到，時間一下子就過了，很喜歡小賴老師的教學方式！  
這堂課也學會了用指令對電腦下各種動作，還有操作 github，感覺很有工程師的樣子 XD 努力記起來各種指令，融會貫通後說不定上班打指令會被說很屌哈哈哈。

# 12/26 Node.js 上課筆記 & 心得

```
先以現階段的課程內容學精為主，工作一段時間後會遇到各種狀況，都需要其他學科的知識，所以未來遇到問題，要花時間去查緣由
、趁機補充相關知識，以下是會用到的相關學科:

1. 資料結構 Data Structure (DS)
2. 演算法 Algorithm (Algo)
3. 資料庫 Database (DB)
  正規化 <-- 怎麼設計 table schema
  （這不是一定非得要遵守的法律，但是我們會盡量遵守，的確有時候會因為一些商業邏輯特殊的設定，會違反正規化）
4. 網路 Networking
5. 作業系統 Operating System (OS)
```

## Node.js

什麼是 Node.js?

- 不是框架
- 後端在用的？
- 不是程式語言

到目前為止，你們寫的 Javascript 都在哪裡「執行」？ 瀏覽器

—> NodeJS 另外一個可以執行 Javascript 的地方

### 產品版本開發生命週期

- Current: 最新的 NodeJS 版本
- Active: 正在積極維護和升級的版本
- Maintenance: 維護中的 LTS，直到生命週期結束
- LTS: Long-Term Support 長期維護版
- EOL: end of life，生命週期結束、不再維護

### 使用 nvm 執行 Node.js

1. 安裝 nvm
2. 檢視版本號 (需用系統管理員開啟 git bash)
3. 安裝最新版本
4. 切換要使用的 node 版本
5. 確認目前安裝的版本

### nvm 指令

```bash
# 查詢 nvm 指令
nvm ??

# 列出可以安裝的版本
nvm ls-remote 16
# windows版本
nvm list available

# 安裝最新版本號
nvm install 16.13.1

# 切換要使用的 node 版本
nvm use 16.13.1

# 確認目前執行的版本
node -v

# 列出你目前主機安裝的版本
nvm ls
# windows版本
nvm list

# 設定預設的版本
nvm alias default 16.13.1
```

\*\*\*練習  
建立好 repo 資料夾後 clone 下來再建立 basic 資料夾，建立 hello.js 檔案後，到 bash cd 到 js 同層級，執行 hello.js 檔案

```bash=
node hello
```

## NodeJS 是？

- NodeJS 是不是一個程式語言？ No
- NodeJS 是不是一個框架？ No
- NodeJS 可以讓我們脫離瀏覽器執行 JS 的環境 ==> 讓你可以在伺服器端執行程式
- NodeJS 是以 Chrome 的 V8 引擎為核心
  https://github.com/nodejs/node/tree/master/deps/v8

JS 的執行環境

- 瀏覽器
- NodeJS

![](https://i.imgur.com/JcXqMC2.png)

==> document, window,... 這些都是屬於瀏覽器提供的物件，所以這些物件不可以在 nodejs 裡面用

## NodeJS 的特色 (JS)

- 單執行緒
- 非阻塞
- 非同步 IO
- 事件循環 (event loop)

### 單執行緒 single-thread

thread --> 作業系統

- Process vs Thread (multi-thread)
- 排程演算法, FIFO, SJF
- Thread pool
- Deadlock
- Context Switching
- Race Condition \*\*

## 心得

今天後半段講解作業系統的部分有點飄走(先跟老師跪...)，後面會補上課錄影檔><
上午在安裝 nvm 的時候卡住很久，後來搞定成就感滿滿(不過只是用系統管理員身分下指令就 ok 啦)
