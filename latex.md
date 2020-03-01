# latex 

主要是在高清与打印方面上具有独特的优势

## 命令

- % 注释符号
- 用\\开始的一串字母来表示命令，{}表示参数
- 正文，介于\begin{document}和\end{document}的区域
- 导言区，介于\documentclass和\begin{document}的区域，用于引用宏包
- 环境，形如\begin{Name}...\end{Name}，为Name环境的区域

### 段落

使用

- 空行
- \par

可以开始新段落，同时默认有缩进。如果不想缩进，也强制换行

- \\\\
- \newline

#### 居中对齐
```
\begin{center}
.....
\end{center}
```
#### 单侧对齐
```
\begin{flushleft}
\end{flushleft}

\begin{flushright}
\end{flushright}

```

#### 调整页面布局

```
\usepackage[text={125mm,195mm},centering]{geometry}
```

### 列表

有三种列表形式
- 无序列表itemize
- 有序列表enumerate
- 描述列表description

序列表可以添加参数，用于缩减行间距离，同样可用于参考文献的样式。样例中的是每行缩进-1.5ex

```latex
\begin{itemize}\addtolength{\itemsep}{-1.5ex}
    \item a 
    \item b 
    \item c 
\end{itemize} 
\begin{enumerate}
    \item a 
    \item b 
    \item c 
\end{enumerate} 
\begin{description}
    \item [a] a's context 
    \item [b] b's context 
    \item [c] c's context  
\end{description} 

```

### 章节目录
在book和report文档类中，可以使用
1. \\part
2. \\chapter
3. \\section
4. \\subsection
5. \\subsubsection
6. \\paragraph
7. \\subparagraph

### 参考文献

- 显示符号，默认是1，2，3，可不填
- 引用标签，在文档内部引用时\\cite{引用标签}.

```
\begin{thebibliography}{123456最大标号值}
\bibitem[显示符号]{引用标签} Book Title, Author
\bibitem {JW1}Jingwhale, T.A.O.C.P. , Yunlong Zhang , 2015,Vol. 1.
\bibitem {JW2}Jingwhale, T.A.O.C.P. , Yunlong Zhang , 2015,Vol. 6.
\bibitem {JW2}Jingwhale, T.A.O.C.P. , Yunlong Zhang , 2015,Vol. 8.
\end{thebibliography}
```

为了更好的管理，可以单独使用一个文件来编写。

bibtex是一个引用数据库，后缀文件名为bib，各大论文网站都会提供bibtex格式的文献引用。

### 插入图片

#### 图文混排

```
\usepackage{graphicx}

\begin{document}

排版软件
\raisebox{-2mm}{\includegraphics[scale=0.8]{picture/tupian.jpg}}
排版文档。

\end{document}
```

#### 图文分开

```
\usepackage{graphicx}

\begin{document}

排版软件
\begin{center}
\includegraphics{picture/tupian.jpg}
\end{center}
排版文档。

\end{document}
```

#### 浮动图片


```
\usepackage{graphicx}

\begin{document}

排版软件
\begin{figure}[h]
  \centering
  % Requires \usepackage{graphicx}
  \includegraphics{picture/tupian.jpg}\\
  \caption{latex}
\end{figure}
排版文档。

\end{document}
```

### 插入公式

#### 行内公式
行内公式与正文一行

```
$a+b>c$
```

#### 行间公式
单独占一行，居中

```
\[ x^n + y^n = z^n, \]
```

#### 公式编号

```
$$x_1+y_1>z_1 \eqno{(1)}$$

\begin{equation}
x^n+y^n=z^n
\end{equation}

```

#### 数学函数

```
\[
\int\frac{1}{x} dx = \ln |x| + C
\]
```

#### 配对括号

```
\[ \Bigg< \bigg\{ \Big[ \big( xyz \big) \Big] \bigg\} \Bigg> \]
```

#### 多行公式

引入美国数学会的包
gather和align会自动编号，如果不需要改成gather\*或align\*

```
\usepackage{amsmath}

\begin{align}
x + y &= 5 \\
2x + 3y &= 8
\end{align}

\begin{gather}
x + y = 5 \\
2x + 3y = 8
\end{gather}
```

#### 拆行公式

```
\begin{equation}
\begin{split}
(3+3)\cdot111 &= 3\cdot111 + 3\cdot111 \\
&= 666
\end{split}
\end{equation}
```

#### 复杂公式

```
\begin{equation}
\left.
\begin{aligned}
x+y &> 5 \\
y-y &> 11
\end{aligned}
\ \right\}\Rightarrow x^2 - y^2 > 55
\end{equation}
```

#### 定理环境

对文档类来说，如果是book的，把subsection改成section

```
\newtheorem{thm}{Theorem}[subsection]
\newtheorem{cor}[thm]{Corollary}
\begin{thm}
This is a theorem.
\end{thm}
\begin{cor}
This is a corollary.
\end{cor}
```

### 插入表格

#### 环境插入表格

```
\begin{tabular}{||||}
  \hline
  % after \\: \hline or \cline{col1-col2} \cline{col3-col4} ...
   &  &  \\
   &  &  \\
   &  &  \\
  \hline
\end{tabular}
```
- lcr指明对齐的方式分别为左对齐，居中，右对齐
- 竖线表明各列直接有竖线分隔，可去掉
- 各行元素用&分离，各列使用\\分离

#### 跨列表格

```
\begin{tabular}{|l|c|r|}
  \hline
  % after \\: \hline or \cline{col1-col2} \cline{col3-col4} ...
  左列 & 中列 & 右列 \\
  \hline
  2行1列 & 2行2列 & 2行3列 \\
  \hline
  \multicolumn{2}{|c|}{跨越2015} & 3行3列 \\
  \hline
  4行1列 & 4行2列 & 4行3列 \\
  \hline
\end{tabular}
```

#### 浮动表格
```
\begin{table}[htbp!]
  \centering

  \begin{tabular}{|l|c|r|}
  \hline
  % after \\: \hline or \cline{col1-col2} \cline{col3-col4} ...
  左列 & 中列 & 右列 \\
  \hline
  2行1列 & 2行2列 & 2行3列 \\
  \hline
  3行1列 & 3行2列 & 3行3列 \\
  \hline
  4行1列 & 4行2列 & 4行3列 \\
  \hline
\end{tabular}

  \caption{示例表格}\label{we}
\end{table}
```

### 引用

#### 脚注

```
\footnote{}
```

#### 引用
```
\begin{quote}
\end{quote}
```

#### 交叉引用
对图片进行引用

```
\section{标题}
从图\ref{Name}中，可以看到...
\begin{figure}[htbp]
\centering
\includegraphics[height=10cm]{xyj2.jpg}
\caption{Name}\label{Name}
\end{figure}
```

## 其他细节

#### 公式中空格

```
$a\qquad b$ // 两个m的空格
$a\quad b$ // 一个m的空格
$a\ b$ // 1/3 m空格
$a\;b$ // 2/7m空格
$a,b$ // 1/6m空格
$a!b$ // 缩紧1/6m空格
```