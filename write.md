# 简单书写

gitbook 的基本用法非常简单，基本上就只有两步：

使用 `gitbook init` 初始化书籍目录

使用 `gitbook serve` 编译书籍

下面将结合一个非常简单的实例，来介绍 gitbook 的基本用法。


## 编辑器

可以用 VsCode、Typora 、Sublime 等自己喜欢的来编辑。

## 创建文章

GitBook 准备工作做好之后，我们进入一个你要写书的目录，输入如下命令。

```
$ gitbook init
warn: no summary file in this book
info: create README.md
info: create SUMMARY.md
info: initialization is finished
```

可以看到他会创建 README.md 和 SUMMARY.md 这两个文件，README.md 应该不陌生，就是说明文档，而 SUMMARY.md 其实就是书的章节目录，其默认内容如下所示：

```
# Summary

* [Introduction](README.md)
```

接下来，我们输入 `$ gitbook serve` 命令，然后在浏览器地址栏中输入 `http://localhost:4000` 便可预览书籍。

效果如下所示：

![](https://blankj.com/gitbook/gitbook/README/default_book.png)

运行该命令后会在书籍的文件夹中生成一个 _book 文件夹, 里面的内容即为生成的 html 文件，我们可以使用下面命令来生成网页而不开启服务器。

```
gitbook build
```

