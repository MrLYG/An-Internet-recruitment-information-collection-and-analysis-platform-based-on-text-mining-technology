# An-Internet-recruitment-information-collection-and-analysis-platform-based-on-text-mining-technology

Project Background:
  The goal of the Internet recruitment information collection and analysis platform based on text mining technology is to provide data support for the professional development and positioning of colleges and universities, solve the phenomenon that the abilities of recent graduates are inconsistent with social needs, and crawl well-known recruitment websites through big data technology It conducts multi-dimensional statistics and analysis of recruitment information, uses text mining technology to automatically classify recruitment positions, and visualizes the results. At the same time, it can also compare the analysis results with the current course settings and provide text reports.









项目背景:
  基于文本挖掘技术的互联网招聘信息采集与分析平台的目标是为高校专业发展和定位提供数据支撑，解决应届毕业生所具备的能力与社会需求不统一的现象，通过大数据技术爬取知名招聘网站的招聘信息，对招聘信息进行多维度的统计与分析，使用文本挖掘技术对招聘岗位进行自动分类，并对结果进行可视化展示。同时还能根据分析结果与当前课程设置进行比对，提供文本报告。

本项目的基本功能：
4.1数据采集功能
该功能负责通过增量式爬虫的方式获取前程无忧招聘网站的信息，去除网站信息中的Html文本标签，将所需要的数据存入MongoDB数据库中的原数据数据库（未清洗数据的数据库）等待数据清洗，具体子功能如下。
4.1.1网络爬虫功能
本系统采用增量式网络爬虫，该方式使用布隆过滤算法（Bloom Filter）对重复的招聘信息进行过滤。布隆过滤算法是通过HashSet的方式存储需要过滤的数据，所以在程序运行时只需接近O(1)的代价就可以查到一个该招聘信息是否被爬取，很大程度上提高了程序的运行效率。对爬取的数据进行去重，尽可能的保证获取数据的真实可靠。
4.1.2定时网络爬虫功能
对爬虫程序设置定时工作周期。
4.1.3数据存储功能
将获取的数据存入到MongDB数据库中。
4.1.4反爬虫功能
有些网站会对爬虫程序进行限制，所以需要加入反爬虫的程序，以突破网站限制。
4.2数据预处理
4.2.1数据清洗
数据清洗是对数据进行重新审查和校验的过程，目的在于删除重复信息、纠正存在的错误，并提供数据一致性。对于获取到的招聘信息，本文在研究了数据内容和结构的基础上，首先对其进行了数据清洗，主要包括结构化处理、信息去重、剔除无效信息等。
4.2.2数据转换
数据转换主要是对数据进行规格化操作。由于借助爬虫程序获取的招聘信息中的数据格式较为混乱，不利于后续进行数据分析时的使用，因此需要将数据进行转换。
4.2.3文本分词功能(中文分词）
对于一段杂乱无章的文本首先需要除文本中的停用词，以及对文本进行分词。本系统将使用的是国内分词的开源技术-结巴分词技术，采用结巴中文分词的精确模式进行分词，这种模式的分词好处是可以将句子最精确的切开，适用于文本分析。
4.3文本挖掘
本系统需要对每条数据大段的文本进行文本挖掘，并提取所需的关键字，然后给该数据的打上岗位类别的标签（标记该岗位的岗位类别）。
4.3.1关键词提取与选择
对文本的关键词进行选择，减少文本分类特征数量，便于程序运行。从文本提取出与计算机专业相关的词汇。
4.3.2搭建文本分类器
运用文本分类算法对训练样本进行训练，搭建文本分类器。该文本分类器会自动识别某段文本的职位描述是属于计算机专业哪一类别岗位的。
4.3.3文本自动分类
每一条新的数据通过文本分类器的处理后，该数据会被自动分类。
4.4数据分析
根据系统所想要到达的分析结果，需要对进行分析建模。通过观察爬取的数据和网站展示的信息，根据岗位的发布数量、招聘人数、薪酬水平、技术需求和所属公司的性质、规模及行业等维度进行深度挖掘、分析，并预先建立分析模型以便于制定合适的数据清洗规则。（因为从网上爬的数据不能直接用，所以我们要根据建立的分析模型来创建一些针对数据清洗规则）
4.5数据可视化
该项目需要把后台爬来的数据进行可视化展示，需要把数据通过图表的方式展示出来。以及为了更好的展示研究结果，需要报告导出的功能。
4.5.1web网页可视化展示
4.5.2报告导出功能
使用jfreechart的图形制作功能，通过该模板，制作了一系列图形：柱状图，条形图，堆积柱状图和扇形图等，并根据easypoi的模板读取，填空的方法，即可导出了相关报告。
