## R中常用的小函数

grep 查询某一pattern在字符串向量中出现的位置
```
> haystack <- c("red", "blue", "green", "blue", "green forest")
> grep("r", haystack)
[1] 1 3 5
```
grepl 同grep，返回T或F
```
> haystack <- c("red", "blue", "green", "blue", "green forest")
> grepl("r", haystack)
[1]  TRUE FALSE  TRUE FALSE  TRUE
```

melt函数
```
reshape2::melt(time_cell,varnames=c('Time','Celltype'),value.name="number")
```

sub替换字符串
```
rownames(doublet.score) <- sub(pattern='\\-1$',replacement='',x=rownames(doublet.score))
```
gsub同sub，但sub仅替换匹配到的第一个pattern，gsub替换所有匹配的pattern

map values
```
Time <- plyr::mapvalues(Time, from=c('T0','T1','T3','T7','T14'), to=c('0','1','3','7','14'))
```

tiff格式画图
```
tiff(file="xxx.tiff",height=500,width=600,res=100,compression="lzw")

dev.off()
```

保存变量
```
#保存某几个变量
save(mergedMEs, mergedLabels, mergedColors, file="WGCNA.RData")
#保存全部变量
save.image(file="file.RData")
```

压缩模式保存
```
save(data1, file = "data.RData",compress="xz")
```
