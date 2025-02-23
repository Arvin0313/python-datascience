## 软件简介

[__samtools depth__](https://www.htslib.org/doc/samtools-depth.html)可用于计算每一个位点或者区域的测序深度并在标准显示设备中显示。

## samtools depth教程

在运行`samtools-depth.cwl`前您需要将相关的运行参数写入一个Yaml文件中。当准备好CWL流程和对应的Yaml文件后，您可以使用sixbox命令行运行使用samtools depth相关相关功能。

```text
sixbox run samtools-depth.cwl samtools-depth.yaml
```

有关Yaml文件的配置，您可以利用通过点击网站右上方‘设置运行’按钮进行可视化设置，我买将自动为您生成运行所需的Yaml文件；当然您也可以自己编写运行需要的Yaml文件。

下面将向您介绍`samtools-depth.cwl`中相关参数。


| CWL参数      | 可视化参数 | 原软件参数 | &nbsp; &nbsp;&nbsp; &nbsp; &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;是否必选&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp; | 参数说明                                                       |
| ---------- | --------------------- | ----- | ---- | ------------------------------------------------------------------------------------- |
| bam_sorted | bam sorted file       |  null  | 是    | 输入文件                                                                                  |
| all_pos    | output all positions  | -a    | 否    | 参数类型为布尔值，默认值为false，当该选项为true时，将输出所有位置上的测序深度（即使该位置上的测序深度为0）                            |
| bed        | positions or regions  | -b    | 否    | 参数类型为字符串，该选项可以在指定的bed file中计算位置或区域列表的深度。Bed文件每行至少包括 chrom ， chromStart ， chromEnd 三列。 |
| f          | BAM filenames         | -f    | 否    | 参数类型为字符串，可以用该参数给定一个含有多个bam文件路径的列表文件，其中每个bam文件路径占一行。                                   |
| l          | read length threshold | -l    | 是    | 参数类型为整数，用于指定reads最短的长度。                                                               |
| r          | region                | -r    | 否    | 参数类型为字符串，用该参数指定一些区域来生成指定区域的深度情况（chr:from-to）                                          |


## 可视化配置案例

点击右上角设置运行按钮，进入可视化配置界面：

![](https://tcs.teambition.net/storage/312c5cbce8a222c824d4b3f432ef2793bdfc?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IjYwZDVkMzRiYzM5MWMwZWY4M2E4YTdiYSIsImV4cCI6MTYzOTcxMjY0MywiaWF0IjoxNjM5NzA5MDQzLCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzMxMmM1Y2JjZThhMjIyYzgyNGQ0YjNmNDMyZWYyNzkzYmRmYyJ9.BMUSmpMjt_CSCtBsbxmjex-RTSl5hl5CVTj-0Yvpxy8&download=image.png "")

双击`bam sorted file`按钮配置输入文件：

![](https://tcs.teambition.net/storage/312c38fa29f026c795bbbb2e8a8bf4204f2c?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IjYwZDVkMzRiYzM5MWMwZWY4M2E4YTdiYSIsImV4cCI6MTYzOTcxMjQzMywiaWF0IjoxNjM5NzA4ODMzLCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzMxMmMzOGZhMjlmMDI2Yzc5NWJiYmIyZThhOGJmNDIwNGYyYyJ9.5dVzJLgFYulphMQVBRSrYKbW2p9xFQM_Nx_C-NR-s7Q&download=image.png "")

配置完输入文件后点击`samtools depth`按钮配置其他参数：

![](https://tcs.teambition.net/storage/312c02b078ed526a67ddf2c25f47826b97cf?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IjYwZDVkMzRiYzM5MWMwZWY4M2E4YTdiYSIsImV4cCI6MTYzOTcxMjg0OSwiaWF0IjoxNjM5NzA5MjQ5LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzMxMmMwMmIwNzhlZDUyNmE2N2RkZjJjMjVmNDc4MjZiOTdjZiJ9.6m9FcWsyjYyNES-_gcmPZc4CB-jtCLsq0raDbDMzcQ0&download=image.png "")

配置完其他参数后，点击下载按钮即可下载samtools-depth.cwl和配置好的Yaml文件。

按照上述方法得到的Yaml文件如下所示：

```text
bed: null  # type "string" (optional)
bam_sorted:  # type "File"
    class: File
    path: http://www.sixoclock.net/resources/data/NGS/Homo_sapiens/WGS/NA12878.WGS.chrM.bowtie2.sort.bam
all_pos: true  # type "boolean"
```

使用sixbox运行，可以得到在当前文件夹输出*.depth.txt的记录测序深度的文件。

```text
awk '$3!=0' NA12878.WGS.chrM.bowtie2.sort.depth.txt |head
chrM    3552    1
chrM    3553    1
chrM    3554    1
chrM    3555    1
chrM    3556    1
chrM    3557    1
chrM    3558    1
chrM    3559    1
chrM    3560    1
chrM    3561    1
```

## 关于sixbox

sixbox是六点了技术团队，为方便用户下载、管理、运行CWL流程编写的一款软件。您可以通过sixoclock网站[__下载sixbox__](http://www.sixoclock.net/download-center)，并查看[__sixbox详细的使用教程__](https://docs.sixoclock.net/clients/sixbox-linux.html#安装)。本教程的所有运行案例皆是利用sixbox运行。

## 关于CWL

通用工作流语言（CWL）是一个开放的标准，用于描述分析工作流和工具，使其可以在各种软件和硬件环境中移植和扩展，从工作站到集群、云和高性能计算（HPC）环境。CWL旨在满足数据密集型科学的需求，如生物信息学、医学成像、天文学、高能物理和机器学习。

有关CWL的更加详细介绍和使用教程，您可以访问[__sixoclock网站__](https://docs.sixoclock.net/dev_guide/CWL/introduction.html#简介)
