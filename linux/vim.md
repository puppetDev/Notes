# vi 常用

```bash
    Ctrl+u：向文件首翻半屏；
    Ctrl+d：向文件尾翻半屏；
    Ctrl+f：向文件尾翻一屏；
    Ctrl+b：向文件首翻一屏；
    Esc：从编辑模式切换到命令模式；
    ZZ：命令模式下保存当前文件所做的修改后退出vi；
    :行号：光标跳转到指定行的行首；
    :$：光标跳转到最后一行的行首；
    x或X：删除一个字符，x删除光标后的，而X删除光标前的；
    D：删除从当前光标到光标所在行尾的全部字符；
    dd：删除光标行正行内容；
    ndd：删除当前行及其后n-1行；
    nyy：将当前行及其下n行的内容保存到寄存器？中，其中？为一个字母，n为一个数字；
    p：粘贴文本操作，用于将缓存区的内容粘贴到当前光标所在位置的下方；
    P：粘贴文本操作，用于将缓存区的内容粘贴到当前光标所在位置的上方；
    /字符串：文本查找操作，用于从当前光标所在位置开始向文件尾部查找指定字符串的内容，查找的字符串会被加亮显示；
    ？name：文本查找操作，用于从当前光标所在位置开始向文件头部查找指定字符串的内容，查找的字符串会被加亮显示；
    a，bs/F/T：替换文本操作，用于在第a行到第b行之间，将F字符串换成T字符串。其中，“s/”表示进行替换操作；
    a：在当前字符后添加文本；
    A：在行末添加文本；
    i：在当前字符前插入文本；
    I：在行首插入文本；
    o：在当前行后面插入一空行；
    O：在当前行前面插入一空行；
    :wq：在命令模式下，执行存盘退出操作；
    :w：在命令模式下，执行存盘操作；
    :w！：在命令模式下，执行强制存盘操作；
    :q：在命令模式下，执行退出vi操作；
    :q！：在命令模式下，执行强制退出vi操作；
    :e文件名：在命令模式下，打开并编辑指定名称的文件；
    :n：在命令模式下，如果同时打开多个文件，则继续编辑下一个文件；
    :f：在命令模式下，用于显示当前的文件名、光标所在行的行号以及显示比例；
    :set number：在命令模式下，用于在最左端显示行号；
    :set nonumber：在命令模式下，用于在最左端不显示行号；
```