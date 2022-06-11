## pandoc
1. 参数介绍
> pandoc test1.md -f markdown -t html -s -o test1.html

其中 -s 表示创建一个独立文件，包含页眉页脚
-o test1.html 表示将输出文件放到 test1.html 中
-f markdown -t html 表示从 markdown 格式转到 html 格式



从网页转markdown

```
pandoc -s -r html http://www.gnu.org/software/make/ -o example12.text
```





Pandoc 程序的命令使用方式为：

> ```
> $ pandoc <files> <options>
> ```

其中 `<files>` 为输入的内容，其输入即可以来自文件，也可以来自标准输入甚至网页链接。而 `<options>` 为参数选项。主要的参数选项有：

- `-f <format>`、`-r <format>`：指定输入文件格式，默认为 Markdown；
- `-t <format>`、`-w <format>`：指定输出文件格式，默认为 HTML；
- `-o <file>`：指定输出文件，该项缺省时，将输出到标准输出；
- `--highlight-style <style>`：设置代码高亮主题，默认为 `pygments`；
- `-s`：生成有头尾的独立文件（HTML，LaTeX，TEI 或 RTF）；
- `-S`：聪明模式，根据文件判断其格式；
- -c : 输入 CSS 文件
- `--self-contained`：生成自包含的文件，仅在输出 HTML 文档时有效；  。重点。
- `--verbose`：开启 Verbose 模式，用于 Debug；
- `--list-input-formats`：列出支持的输入格式；
- `--list-output-formats`：列出支持的输出格式；
- `--list-extensions`：列出支持的 Markdown 扩展方案；
- `--list-highlight-languages`：列出支持代码高亮的编程语言；
- `--list-highlight-styles`：列出支持的代码高亮主题；
- `-v`、`--version`：显示程序的版本号；
- `-h`、`--help`：显示程序的帮助信息。
