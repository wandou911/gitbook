# 将电子书部署到GitHub


## 概述

发布电子书到github 分为4步

1 GitHub 创建repository

2 生成电子书

3 上传源文件到master分支 方便以后修改

4 上传html文件到gh-pages分支 这个分支为发布分支 为了网页查看 注意名称只能用`gh-pages`


## 发布流程

### 1 GitHub 创建repository

创建成功后 可以看到如下信息

```
or create a new repository on the command line
 echo "# gitbook" >> README.md

git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/wandou911/gitbook.git
git push -u origin master
                
…or push an existing repository from the command line

 git remote add origin https://github.com/wandou911/gitbook.git
git push -u origin master
```


### 2 生成电子书

* 创建目录 和github 一致

`mkdir gitbook`

* 进入`gitbook` 目录

`cd gitbook`

*  生成电子书 `gitbook init`

```
$ gitbook init
warn: no summary file in this book 
info: create README.md 
info: create SUMMARY.md 
info: initialization is finished 
```

打开服务器查看 `gitbook serve`

```
$ gitbook serve
Live reload server started on port: 35729
Press CTRL+C to quit ...

info: 7 plugins are installed 
info: loading plugin "livereload"... OK 
info: loading plugin "highlight"... OK 
info: loading plugin "search"... OK 
info: loading plugin "lunr"... OK 
info: loading plugin "sharing"... OK 
info: loading plugin "fontsettings"... OK 
info: loading plugin "theme-default"... OK 
info: found 1 pages 
info: found 0 asset files 
info: >> generation finished with success in 2.5s ! 

Starting server ...
Serving book on http://localhost:4000
```
在浏览器输入 `http://localhost:4000` 即可查看生成的电子书

Ctrl + c 退出 

### 3 上传本地电子书文件到master分支 

git初始化

```
$ git init
Initialized empty Git repository in /Users/wandou/Documents/BOOK/gitbook/.git/
$ ls -al
total 32
drwxr-xr-x   7 wandou  staff   224 May  7 10:25 .
drwxr-xr-x   7 wandou  staff   224 May  7 10:48 ..
-rw-r--r--@  1 wandou  staff  6148 May  7 10:33 .DS_Store
drwxr-xr-x  13 wandou  staff   416 May  7 10:25 .git
-rw-r--r--   1 wandou  staff    16 May  7 10:25 README.md
-rw-r--r--   1 wandou  staff    40 May  7 10:25 SUMMARY.md
drwxr-xr-x   5 wandou  staff   160 May  7 10:25 _book
```
可以看到生成了一个.git 文件

提交本地文件 并推送到master 分支

主要命令

```
$ git add .
$ git commit -m"初始化gitbook"
$ git remote add origin https://github.com/wandou911/gitbook.git
$ git push -u origin master
```

详细步骤图片

```
$ git add .
$ git commit -m"初始化gitbook"
[master (root-commit) c6ce95a] 初始化gitbook
 27 files changed, 2503 insertions(+)
 create mode 100644 README.md
 create mode 100644 SUMMARY.md
 ...
 create mode 100644 _book/index.html
 create mode 100644 _book/search_index.json
$ git remote add origin https://github.com/wandou911/gitbook.git
$ git push -u origin master
Counting objects: 39, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (34/34), done.
Writing objects: 100% (39/39), 624.96 KiB | 8.33 MiB/s, done.
Total 39 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/wandou911/gitbook.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.
```

这时候已经上传完成

打开github网页刷新 即可看到刚刚上传的文件


### 4 上传html文件到gh-pages分支

```
$ git checkout -b gh-pages
$ git add .
$ git commit -m "上传gf-pages"
$ git push origin gh-pages
```

详细步骤图片

```
$ git checkout -b gh-pages
Switched to a new branch 'gh-pages'
$ git add .
$ git commit -m"上传gf-pages"
[gh-pages d33ee86] 上传gf-pages
 27 files changed, 6 deletions(-)
 delete mode 100644 README.md
 delete mode 100644 SUMMARY.md
 ...
 rename _book/index.html => index.html (100%)
 rename _book/search_index.json => search_index.json (100%)
$ git push origin gh-pages
Counting objects: 1, done.
Writing objects: 100% (1/1), 192 bytes | 192.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0)
remote: 
remote: Create a pull request for 'gh-pages' on GitHub by visiting:
remote:      https://github.com/wandou911/gitbook/pull/new/gh-pages
remote: 
To https://github.com/wandou911/gitbook.git
 * [new branch]      gh-pages -> gh-pages
```

至此已经上传html文件到 `gh-pages` 分支

刷新github网页 即可看到刚才上传的html文件

### 后记

这里有两个分支 master分支和gh-pages分支 

master分支：书写文件分支 所有的修改或者新增文件都在master分支 

gh-pages分支 ：发布分支 

书写文章和发布文章步骤

切换到master分支

`$ git checkout master` 

新增md文件或者修改md文件 

运行  `gitbook build` 生成html文件

`gitbook build` 

推送到master分支

```
$ git add .
$ git commit -m "更新备注"
$ git push
```

复制  `_book` 目录到别的地方 做备用

切换到gh-pages分支

`$ git checkout gh-pages`

进入`_book`目录,复制里面所有的文件到gitbook目录

推送到 `gh-pages` 分支

```
$ git add .
$ git commit -m "更新备注"
$ git push
```


