## ggplot散点图常用主题

```
geom_point(size=1.5) + 
        labs(title='xxx') + 
        scale_color_gradientn(colours=viridis:: plasma(100)) +
        theme(axis.line=element_blank(), axis.text=element_text(size=14,color='black'), axis.title=element_text(size=14,color='black'), axis.ticks=element_line(color='black'), panel.background=element_rect(fill=NA), panel.border=element_rect(fill=NA, color='black'),legend.position='none', plot.title=element_text(size=14, hjust=0.5))
```
