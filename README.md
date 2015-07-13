# Boost 库文档中文翻译

## 简介

最权威的 C++ 类库 Boost <http://www.boost.org> 的中文翻译。

Boost库由Boost社区组织开发、维护。其目的是为C++程序员提供免费、同行审查的、可移植的程序库。
Boost库可以与C++标准库完美共同工作，并且为其提供扩展功能。Boost库使用Boost License来授权使用，
根据该协议，商业的非商业的使用都是允许并鼓励的。

感谢 Boost 中文翻译小组 <https://code.google.com/p/boost-doc-zh/> ，感谢他们不计回报的工作，为我们带来如此优秀的项目。

## 文档编译

Boost 的文档很多是通过 QuickDoc 或 BoostBook（DocBook）的形式提供，这一节记录如何创建一个编译环境，以便从原始的 qbk 文件编译到 html 等格式。

首先，需要从 [docbook](http://docbook.sourceforge.net/ ”Docbook 的网站“) 下载 XSL 和 DTD，

下载地址：
* [Docbook XML DTD 4.2](http://www.oasis-open.org/docbook/xml/4.2/docbook-xml-4.2.zip "Docbook XML 的 DTD") *Boost 用的是这个版本*
* [Docbook XSL](http://sourceforge.net/projects/docbook/files/docbook-xsl/ "Docbook XSL") 目前最新版本是 [XSL 1.78.1](http://downloads.sourceforge.net/project/docbook/docbook-xsl/1.78.1/docbook-xsl-1.78.1.zip?r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fdocbook%2Ffiles%2Fdocbook-xsl%2F1.78.1%2F&ts=1436768044&use_mirror=nchc)

把它们分别解压，我们假设 DTD 解压在 **D:\docbook\docbook-xml-4.2** ,XSL 解压在 **D:\docbook\docbook-xsl-1.78.1**。

另外还需要下载 xsltproc，Windows 下可以在 <http://www.zlatkovic.com/pub/libxml/> 下载可文件的执行包（iconv, zlib, libxml2 和 libxslt 都需要）。也可以试试直接在 [这里下载](https://github.com/jadedrip/boost-doc-zh/releases/download/untagged-91599d7aa14867186cf3/xsltproc.7z) x64版本。

假设我们把 xsltproc 放在 **D:\docbook\xsltproc** 目录，我们需要把 D:\docbook\xsltproc\bin 加入 Windows 的环境变量 PATH 中。

进入 boost 的安装目录 BOOST_ROOT, 执行 bootstrap.bat 编译 b2.exe。然后进入 tools\quickbook 目录执行 b2.exe，以便编译 quickbook.exe。然后把 quickbook.exe 复制到 D:\docbook\xsltproc\bin\ 目录。

下面，我们需要写一个 user-config.jam 文件，内容如下：

···
    using xsltproc
      : "D:/Docbook/xsltproc/bin/xsltproc.exe"
      ;

    using boostbook
      : "D:/docbook/docbook-xsl-1.78.1"
      : "D:/docbook/docbook-xml-4.2"
      ;

    using quickbook
      : "D:/docbook/xsltproc/bin/quickbook.exe"
      ;

···

把这个文件放在 $BOOST_ROOT/tools/build/src 目录下。

*PS: 执行 b2 --debug-configuration 目录就可以查看 bjam 在哪里查找 user-config.jam 文件。*

这样编译环境就完成了，然后进入 $BOOST_ROOT/libs/function/doc 目录，删除 html 文件，然后执行 `b2.exe html`。如果一切正常，就会重新编译出 html 目录了。

*PS: 看到 `Cannot find function named 'checked_delete'` 这样的警告别紧张，这是正常现象，无视就好了。
