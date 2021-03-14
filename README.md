# defines
预定义查询字典
***
无论是river-node中的原始event结构类、error结构类，还是某个自定义包中的新的event结构类、error结构类，可以简单的理解成他们的使用方式都是没区别的。  
而具体的使用规则又分为“创建规则”与“返回值规则”  
对于创建规则，任何地方的任何event与error都是相同的，都使用的是NewError或NewEvent函数，入参3个参数，分是别：  

    第一个code int：为预定义的常量值
    第二个uniqueid string：为其所属的数据流动节点的唯一名称标识
    第三个commit string：为一些汉字说明
    
对于返回值规则：  
    error结构类与golang内置类型的Error()方法相同，只返回一个string
    event结构类拥有Description()方法，分别返回四个值，分别是：uniqueid string, code int(事件常量的整数表达), conststring string(事件常量的字符串表达), commit string(同上)  
    error内部组合了对应event实体，的Error()方法内部调用了event实体的Description()方法进而合成了最终的string类型返回值，具体调用方式代码片段如下：  
    *_, _, conststring, commit  := p.Description()*
***
  **2021年3月14日12点21分:**  
	ANOTHEREXAMPLE_TEST1 = 999999  
	ANOTHEREXAMPLE_TEST2 = 999998  
	ANOTHEREXAMPLE_TEST3 = 999997  
	ANOTHEREXAMPLE_ERR = 999996  

  **当前原始river-node占用0~200:**  
	HEARTBREATING_RUN = iota  
	HEARTBREATING_FUSED  
	HEARTBREATING_TIMEOUT //一般为ERROR  
	HEARTBREATING_TIMERLIMITED //一般为ERROR  
	HEARTBREATING_RECOVERED  
	HEARTBREATING_REACTIVEDESTRUCT  
	HEARTBREATING_PROACTIVEDESTRUCT  
	CRC_RUN  
	CRC_FUSED   
	CRC_UPSIDEDOWN //一般为SIGNAL  
	CRC_NOTPASS //一般为ERROR  
	CRC_RECOVERED  
	CRC_NULLTAIL  
	CRC_REACTIVEDESTRUCT  
	CRC_PROACTIVEDESTRUCT  
	STAMPS_RUN  
	STAMPS_REACTIVEDESTRUCT  
	STAMPS_PROACTIVEDESTRUCT  
	RAWSIMULATOR_RUN  
	RAWSIMULATOR_REACTIVEDESTRUCT  
	RAWSIMULATOR_PROACTIVEDESTRUCT  

  **river.usrio-808占用编码范围200~219:**    
	RIVER_USRIO808_INITSUCCESS =200  
	RIVER_USRIO808_INITFAIL = 201  
	RIVER_USRIO808_RUN = 202  
	RIVER_USRIO808_RESOLVESRCFAIL = 203 //一般为Error  
	RIVER_USRIO808_READCONNERR =204  
	RIVER_USRIO808_NEWUSRIO808 =205  
	RIVER_USRIO808_REACTIVEDESTRUCT =206  
	RIVER_USRIO808_PROACTIVEDESTRUCT =207  

  **river.bytesliceasker占用编码范围220~229:**  
	RIVER_BYTESLICEASKER_INITSUCCESS =220  
	RIVER_BYTESLICEASKER_INITFAIL = 221  
	RIVER_BYTESLICEASKER_RUN = 222  
	RIVER_BYTESLICEASKER_NEWBYTESLICEASKE =223  
	RIVER_BYTESLICEASKER_REACTIVEDESTRUCT =224  
	RIVER_BYTESLICEASKER_PROACTIVEDESTRUCT =225  
  
  **自定义适配器river.usr-io808_prefilter占用编码范围230~239:**    
