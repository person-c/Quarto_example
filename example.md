---
title: "Quarto example"
subtitle: "quarto example -------"
author: "cw"
date: '2024-03-20'
format:
  pdf:
    include-in-header: 
      text: |
        \usepackage{ctex}
        \usepackage{amsthm,mathrsfs}
        \usepackage{float}
        \let\origfigure\figure
        \let\endorigfigure\endfigure
        \renewenvironment{figure}[1][2] {
            \expandafter\origfigure\expandafter[H]
        } {
            \endorigfigure
        }
  docx:
    reference-doc: template/custom-reference-doc.docx
    fig-align: center
number-sections: true
link-citations: true
lang: zh
table-of-contents: true
echo: false
bibliography: ref/ref.bib
csl: nature.csl
keep-md: true
---




\pagebreak


对于样式的控制，可以通过yaml参数对每种输出类型的样式进行控制。或者设计对应的模板，更精细地控制可以通过Lua.

# 中文支持

yaml头部设置如下：

```yaml
pdf:
  include-in-header:
    text: |
      \usepackage{ctex}
      \usepackage{amsthm,mathrsfs}
  CJKmainfont: KaiTi
```

# 交叉引用


引用图片 @fig-example . （注意空行以及空格）

::: {#fig-example layout-ncol=2}

![图片引用示例a](figures/example.png){#fig-examplea width=2.5in}

![图片应用示例b](figures/example.png){#fig-exampleb width=2.5in}


图片example
:::

![图片引用示例c](figures/example.png){#fig-examplec width=50%}

图片引用 2 @fig-examplec

引用表格 @tbl-go .



::: {#tbl-go .cell tbl-cap='GO富集分析中线粒体相关'}
::: {.cell-output .cell-output-stderr}

```
Warning: package 'data.table' was built under R version 4.3.3
```


:::

::: {.cell-output-display}


|ONTOLOGY |ID         |Description                                    |  p.adjust|
|:--------|:----------|:----------------------------------------------|---------:|
|BP       |GO:0051881 |regulation of mitochondrial membrane potential | 0.0215593|
|CC       |GO:0005759 |mitochondrial matrix                           | 0.0396286|


:::
:::



引用公式 (@eq-example)

$$
y = x^2 +1
$${#eq-example}


引用文献 @li_exaggerated_2022 ， 这里还有 @noauthor_wgcna_nodate .


# 附录 {.appendix}

pdf的输出需要Latex， 用如下命令下载

```bash
quarto install
```

从[这里](https://www.zotero.org/styles)下载csl文件。

word的模板并不是普通的word，你必须从Pandoc生成该模板，然后再修改。

# 参考文献

::: {#refs}
:::

