# EditorConfig

多编辑器公用编码风格配置

## .editorconfig

```conf
root = true
# 对所有文件生效
[*]
charset = utf-8
indent_style = space
indent_size = 4
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true

# 对后缀名为 md 的文件生效
[*.md]
trim_trailing_whitespace = false
```

-   indent_style: 缩进类型。space tab
-   end_of_line：换行符格式。lf
-   trim_trailing_whitespace：是否删除行尾的空格。true false
