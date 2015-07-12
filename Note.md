# 翻译须知 #
2008/7/1 之后认领的子库请务必按照以下标准翻译。之前认领的子库，如果有时间，也请修改使之符合以下标准。

2010/1/1 从boost 1.42.0版本起，对于使用quickbook或boostbook生成的html文档，全部改为对qbk或xml文件进行翻译，再使用相关工具生成html文档，而不再直接翻译html文件。具体说明，请查看[boostbook](boostbook.md)

## 翻译之前 ##
目前原 boost 文档是采用 html 格式发布的。翻译前 **请先把文件改为 utf-8 编码** ，包括 **html 头中的 meta 信息\*要改为：**

&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"&gt;



你可以直接修改源码，也可以使用网页编辑器。
在原文件的版权声明后面请加上自己的版权声明；请参照 http://boost-doc-zh.googlecode.com/svn/trunk/libs/random/index.html。

请务必签出版本库根目录下的 glossary 目录 (boost-doc-zh.googlecode.com/svn/trunk/glossary)，并尽量按词汇表翻译。

## 翻译 ##
可以保留原文，也可以只留中文。如果你决定采用双语对照，请注意一下页面的美观。翻译时记住 boost 文档面向的对象是 **C++ 程序员** 。

## 文件提交 ##
**请尽量填写日志，日志可以使用中文或英文 (请尽量确保没有错别字和/或语法错误)** 。Google Code 允许修改过去的日志。

## 完成后 ##
翻译完成后请在论坛发帖说明。