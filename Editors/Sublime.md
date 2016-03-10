## 1. 好用插件推荐
### 1.1 HtmlBeautify
html页面的美化，直接ctr+shift+p输入htmlB调用即可。

### 1.2 JsFormat
快捷方式ctr+alt+F，js的格式化。

### 1.3 SideBarEnhancements
增强的侧栏功能，添加就知道怎么好了

### 1.4 AdvancedNewFile
快捷方式ctr+alt+N，New新的文件，支持tab自动补全文件夹，非常方便。

### 1.5 SyncedSideBar
自动同步当前打开文件的side bar位置。

### 1.6 phpfmt
直接安装就行。
https://packagecontrol.io/packages/phpfmt
注意确保php在系统的PATH中，因为这个功能具是php写的，需要php执行。

另外，在Preferences----Package Settings----phpfmt----Settings - User中添加如下内容

```
{
    "autocomplete": true,
    "autoimport": true,
    "passes":
    [
        "AlignEquals",
        "AlignDoubleArrow",
        "AlignDoubleSlashComments",
        "AlignGroupDoubleArrow",
        "LongArray",
    ],
    "psr2": true,
    "smart_linebreak_after_curly": true,
    "version": 3
}
```

要执行，直接使用`ctrl+shitf+p phpfmt: format now`.
### 1.7 sublime_phpcs
这个是检查php代码错误的插件，推荐。
安装PHP_CodeSniffer:
```
pear ：  下载 http://pear.php.net/go-pear.phar
执行： php go-pear.phar
执行：pear install PHP_CodeSniffer
cpi ------->  sublimilinter_phpcs
```
### 1.8 DocBlockr
sublime的php doc插件 DocBlockr，应该大家已经在用，现在需要修改一下配置，避免到处是[description]而实际上没有任何有效的description被添加的情况。
Preferences --> Package Settings --> DocBlockr -> Settings -User:
```
{
    "jsdocs_function_description": false,
    "jsdocs_return_description": false,
    "jsdocs_param_description": false,
    "jsdocs_param_name": true,
    "jsdocs_align_tags": "shallow",
    "jsdocs_spacer_between_sections": true
}
```

一个示例如下：

```
    /**
     * Send wechat message and notice for purchasing order finished.
     *
     * @param  App\Shop $shop
     * @param  App\PurchasingOrder $purchasingOrder
     *
     * @return void
     */
```

**注意** 
* `@param` 后面有两个空格，而类型后面有一个空格，不需要对齐。
* 方法说明后一个空行，`@param`块后一个空行。`@return`后不允许有空行。

### 1.9 Cobalt2
这是一个color scheme，关注于把注意力放在代码本身，试用几个周后确实发现这种scheme有其优势。建议大家体验。

## 2. 使用技巧
### 2.1 关于代码折叠：
```
ctrl+shift+[    折叠代码块(光标所在位置)
ctrlshift]      取消折叠(光标所在位置)

ctrl+k,0        取消所有折叠
ctrl+k, 1 (-9)  设置折叠等级：1是类层面，2，就是类的所有函数了。

例如如果要将所有函数都折叠，可以这样操作：ctrl+k，2
```




