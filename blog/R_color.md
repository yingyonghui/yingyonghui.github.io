## Set color in R

```
### 产生RGB颜色
 mycolor=rgb(248, 203, 173, max=255)

########################################
#  渐变色取色
########################################
# 两个渐变色包
viridis, wesanderson(https://github.com/karthik/wesanderson)

### ggplot2默认渐变色系
mycolors <- scales::hue_pal(c=100)(25)
scales::show_col(mycolors)

### viridis渐变色
### 紫色到黄色渐变
viridis::viridis(100)
colorRampPalette(c("#440154" ,"#21908C", "#FDE725"))(100)
### 蓝色-红色-黄色渐变
viridis::plasma(100)
### 其他可选渐变
viridis::magma(100)
viridis::inferno(100)

### RColorBrewer产生渐变色
### 深蓝到浅橙到深红
color.use <- rev(RColorBrewer::brewer.pal(n=10, name='Spectral'))
mycolors <- colorRampPalette(color.use)(99)

########################################
### 离散色取色
########################################
### RColorBrewer离散色系
library(RColorBrewer)
mycolors <- c(brewer.pal(name="Dark2", n=8), 
brewer.pal(name="Accent", n=7), 
brewer.pal(name="Set1", n=9), 
brewer.pal(name="Set3", n=12), 
brewer.pal(name="Set2", n=8), 
brewer.pal(name="Paired", n=10),
brewer.pal(name="Pastel1", n=9),
brewer.pal(name="Pastel2", n=7))
mycolors <- unique(mycolors)

########################################
### 如何设置渐变色
########################################
# 设置图注中渐变颜色的显示和范围
scale_color_gradient(low="red", high="green", limits=c(0,1))
# 设置图注中3个渐变颜色的显示和范围
scale_colour_gradient2(low="red", mid='lightgreen', high ="purple", 
midpoint=0.125, limits=c(0,0.25))
# 设置图注中n个渐变颜色的显示和范围
scale_colour_gradientn(colours=c("red",'lightgreen','lightblue','purple'), 
limits=c(0,0.05))

```
