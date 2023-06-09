## 个人简历

You can use the [editor on GitHub](https://github.com/yingyonghui/yingyonghui.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for
```
theme(
### 图title字号、加粗、居中
plot.title=element_text(size=18, face="bold", hjust=0.5)

### 坐标轴
#坐标轴刻度字体
axis.text=element_text(size=16, colour='black'),
#x轴标签旋转90度，并做垂直和水平方向的位置微调
axis.text.x=element_text(angle=90, hjust=1, vjust=0.5)
#坐标轴标度
axis.ticks.x=element_blank(),
#坐标轴线条
axis.line.x=element_blank()
#坐标轴倾斜45度后对齐
axis.text.x=element_text(angle=45, hjust=1, vjust=1),
#坐标轴title
axis.title=element_text(size=16),
#坐标轴的粗细和颜色
axis.line=element_line(size=0.5, colour='black'),

### 坐标轴标签内容修改
scale_x_continuous(breaks=1:5, labels=c('T0','T1','T3','T7','T14')) 

### 画布背景
#白色画布背景，四周黑色边框（位于图层底层）
panel.background=element_rect(fill="white", color="black")
#无背景板，四周黑色边框（位于图层顶层，且坐标轴tick处不会有间断）
panel.border=element_rect(fill=NA, colour="black"),
panel.border=element_blank(),
#画布网格为空
panel.grid=element_blank()
#画布网格为灰色，粗细为1，虚线
panel.grid=element_line(colour='gray', size=1, linetype =3),
#主网格与次网格
panel.grid.minor=element_line(size=1, linetype=3, color="purple"),
panel.grid.major=element_line(size=2, linetype=3, color="grey70"),
#长宽比
aspect.ratio=1,

### 图注
#legend title
legend.title=element_blank(),
#legend 字体
legend.text=element_text(size=14),
#legend位置
legend.position='right',
legend.position = c(0.1, 0.2)s,
#去掉图注所用的标志的灰色背景
legend.key=element_blank()
)
#图注分成两列
#点图分类图注设置，更多设置查看https://ggplot2.tidyverse.org/reference/guide_legend.html
guides(color=guide_legend('Celltype',override.aes=list(size=3), ncol=2))
#点图渐变颜色图注设置，更多设置查看https://ggplot2.tidyverse.org/reference/guide_colourbar.html
guides(color=guide_colorbar(barwidth=1, barheight=4,order=2))


### 渐变色
#两个渐变色包
viridis, wesanderson(https://github.com/karthik/wesanderson)
#设置图注中渐变颜色的显示和范围
scale_color_gradient(low="red", high="green", limits=c(0,1))
#设置图注中3个渐变颜色的显示和范围
scale_colour_gradient2(low="red", mid='lightgreen', high ="purple", midpoint=0.125, limits=c(0,0.25))
#设置图注中n个渐变颜色的显示和范围
scale_colour_gradientn(colours=c("red",'lightgreen','lightblue','purple'), limits=c(0,0.05))

### 柱形图分组，X轴分组
facet_grid(~manufacturer, scales="free") + 
### 柱形图分组，Y轴分组
facet_grid(manufacturer~., scales="free") + 
### 柱形图分组，调整注释条上字体字号颜色角度与背景边框
theme(strip.text.x=element_text(size=8, colour="red", angle=90), strip.background =element_rect(fill=NA,color=NA))
### 散点图控制点的大小范围
scale_size(range = c(1, 4))
### 坐标轴
#x,y轴范围与刻度显示
scale_x_continuous(limits=c(-50,40), breaks=c(-40,-20,0,20,40))
scale_y_continuous(limits=c(-50,40), breaks=c(-40,-20,0,20,40))
#刻度线从0开始
scale_x_continuous(expand = c(0, 0))

### 添加垂直线段
geom_vline(xintercept=0, size=0.3, linetype=2, colour='grey')
geom_hline(yintercept=0, size=0.3, linetype=2, colour='grey')

### 将同一组的散点圈起来（待验证）
stat_ellipse(aes(x=tSNE_1,y=tSNE_2,fill=cellname),
               geom="polygon", level=0.95, alpha=0.2)

### ggplot 默认渐变色系
mycolors <- scales::hue_pal(c=100)(25)
scales::show_col(mycolors)

###RColorBrewer产生渐变色
###深蓝到浅橙到深红
color.use <- rev(RColorBrewer::brewer.pal(n=10, name='Spectral'))
mycolors <- colorRampPalette(color.use)(99)

###RColorBrewer对比色系
library(RColorBrewer)
mycolors <- c(brewer.pal(name="Dark2", n=8), brewer.pal(name="Accent", n=7), brewer.pal(name="Set1", n=9), brewer.pal(name="Set3", n=12), brewer.pal(name="Set2", n=8), brewer.pal(name="Paired", n=10),brewer.pal(name="Pastel1", n=9),brewer.pal(name="Pastel2", n=7))
mycolors <- unique(mycolors)

###产生RGB颜色
 mycolor=rgb(248, 203, 173, max=255)

###紫色到黄色渐变
viridis::viridis(100)
colorRampPalette(c("#440154" ,"#21908C", "#FDE725"))(100)
###蓝色红色黄色渐变
viridis:: plasma(100)
###其他可选渐变
viridis:: magma(100)
viridis:: inferno(100)
### X轴标签旋转角度与高度自动调整
rotatedAxisElementText = function(angle,position='x'){
    angle <- angle[1]
    position <- position[1]
    positions <- list(x=0, y=90, top=180, right=270)
    if(!position %in% names(positions)){
        stop(sprintf("'position' must be one of [%s]",paste(names(positions),collapse=", ")), call.=FALSE)
    }
    if(!is.numeric(angle)){
        stop("'angle' must be numeric",call.=FALSE)
    }
    rads  <- (-angle - positions[[ position ]])*pi/180
    hjust <- 0.5*(1 - sin(rads))
    vjust <- 0.5*(1 + cos(rads))
    element_text(angle=angle,vjust=vjust,hjust=hjust)
}

```

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/yingyonghui/yingyonghui.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### 自我评价
- 特别能吃
- 特别能睡

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
