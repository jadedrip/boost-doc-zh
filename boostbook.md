# 简介 #

从文档格式来分，boost文档可分为两种：
  * 一种是直接用html格式编写
  * 另一种则是使用quickbook/boostbook格式编写然后生成html文件

前者更多见于较早期的子库，而较新的子库则基本上全都使用后一种格式。后一种格式是当前boost社区建议使用的新格式，早期使用旧格式的子库也会逐渐转换为新格式。

使用quickbook/boostbook格式的子库又分为两类：
  * 一类是每个子库单独建立一个项目，单独生成一个html文件的子目录，子目录通常为$BOOSTROOT/libs/_sub-lib_/doc/html
  * 另一类是多个子库共建一个项目，生成一个总的html目录，即$BOOSTROOT/doc/html

# 采用quickbook/boostbook格式的子库列表 #

以下子库共建一个boostbook项目，项目文件为 $BOOSTROOT/doc/Jamfile.v2：
| | **xml格式** | **qbk格式** |
|:|:----------|:----------|
| 子库 | any, array, concept\_check, date\_time, function, lambda, program\_options, ref, signals, signals2, string\_algo, tribool, variant | accumulators, foreach, hash, interprocess, intrusive, mpi, property\_tree, proto, random, static\_assert, thread, tr1, typeof, units, unordered, xpressive |
| 工具 | boostbook, build | quickbook, bjam |

以下子库每一个子库单独建立一个项目，各个项目的项目文件分别为 $BOOSTROOT/libs/_sub-lib_/doc/Jamfile.v2，它们全部采用\*qbk格式**：**| 子库 | asio, bimap, config, function\_types, functional/factory, functional/forward, fusion, integer, math, numeric\_conversion, optional, range, regex, scope\_exit, spirit, type\_traits |
|:---|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    | 1.46.0 新增：icl                                                                                                                                                                       |
| 工具 | bcp                                                                                                                                                                                 |