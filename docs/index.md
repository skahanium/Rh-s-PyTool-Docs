<center>

![logo](assets/icon_logo/logo.svg)
</center>
## 关于Rh-s-PyTool

^^Rh-s-PyTool^^ 是一系列python工具方法的合集，包含了行政区域名称查询与补全、行政区域坐标查询以及综合指标评价方法等方面的内容。


## 主要功能

当前，^^Rh-s-PyTool^^ 主要包含了两个大的模块：[cp_lookup](api/cp_lookup.md) 和 [index_calmeth](api/index_calmeth.md) ，二者又分别包含了若干个小模块。前者的功能描述大致描述如下：

+ 将区域简称补完为全称

+ 根据地区（省、市、区县）名称获取行政中心的经度和纬度

+ 计算两个地区（省、市、区县）行政中心间的球面距离

后者则主要包含以下功能：

+ 将非正向指标转换为正向指标

+ 使数据指标无量纲化

+ 计算指标权重

+ 计算评估对象的综合评价分数分数

## 下载

如果对 ^^Rh-s-PyTool^^ 有一定的兴趣，或者希望尝试使用其中的某些方法，可以使用如下方法进行下载。

1. 可以从该项目的GitHub仓库中找到并下载最新的[release](https://github.com/skahanium/Rh-s-PyTool/releases)本地安装，

2. 或者从[PyPI](https://pypi.org/project/Rh-s-PyTool/)获取该模块：

```
pip3 install Rh-s-PyTool
```

3. 也可以使用[pdm](https://pdm.fming.dev)包管理系统（推荐）：

```
pdm add Rh-s-PyTool
```

(注：本模块适用于python3.10及以上版本。)