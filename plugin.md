# 插件

GitBook 有 [插件官网](https://www.npmjs.com/package/gitbook-plugin)，默认带有 5 个插件，highlight、search、sharing、font-settings、livereload，如果要去除自带的插件， 可以在插件名称前面加 -，比如：

```
"plugins": [
    "-search"
]
```

如果要配置使用的插件可以在 book.json 文件中加入即可，比如我们添加 plugin-github，我们在 book.json 中加入配置如下即可：

```
{
    "plugins": [ "github" ],
    "pluginsConfig": {
        "github": {
            "url": "https://github.com/your/repo"
        }
    }
}
```

然后在终端输入 `gitbook install ./` 即可。

如果要指定插件的版本可以使用 plugin@0.3.1，因为一些插件可能不会随着 GitBook 版本的升级而升级。

以下是我个人常用的插件:

gitbook-plugin-donate(打赏按钮): https://www.npmjs.com/package/gitbook-plugin-donate

gitbook-plugin-github-buttons(GitHub按钮): https://www.npmjs.com/package/gitbook-plugin-github-buttons

gitbook-plugin-edit-link(GitHub编辑按钮): https://www.npmjs.com/package/gitbook-plugin-edit-link


