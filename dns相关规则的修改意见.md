### dns_domainlength.rule ###

	不应该计算当前系统内DNS数据包的domain长度，最好计算整个Internet内合法域名的长度的数学期望

### dns\_error\_format.rule ###

	单位时间内DNS query failure的数目超过阈值再报警	

### dns\_illegal\_dip.rule ###

	
	根据部署环境的实际流量，增加相应DNS Server的IP地址；
	
	增加合法DNS Server的IP地址，如各类运营商和互联网公司的DNS Server

### dns\_max_min.rule ###

	不太明白规则含义
	
### dns\_response\_request_ratio.rule ###

	阈值0.7是否准确，是不是有更好的计算方法？

### dns\_toomuch\_request_parallel.rule ###

	不太明白规则含义

### dn\_toomuch\_request_vertical.rule ###

	“5分钟内DNS请求数目超过10内DNS请求数目的5/6，并且总数大于500就报警”，这个条规则可以斟酌一下，最好根据统计学建模，然后再决定具体参数

### dns\_uncommon_rcdtype.rule ###
	
	进一步调研非常见DNS请求类型;

	对于非常见类型的DNS请求包，设置一个阈值