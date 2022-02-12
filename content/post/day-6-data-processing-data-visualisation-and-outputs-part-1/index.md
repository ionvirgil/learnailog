---
title: "Day 6 - Data processing, Data visualisation and outputs - Part 1 "
date: 2022-02-11T06:48:42.295Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Log: Today I used R to process, visualize and output the results. 

1. I used tidyverse to process data, and a few other packages for different, smaller needs. 
2. I used echarts4r to create interactive JavaScript charts using R.
3. I used Rmarkdown to output the results and a .html file and publish it on the web.

**Simple Bar Chart visualisation using echarts4r**

```r
count_by_cnc<-filter(RNCIS,RNCIS$Status=="Inregistrat"|RNCIS$Status=="Validat",is.na(RNCIS$Arhivat))
count_by_cnc<-count(count_by_cnc,count_by_cnc$`Nivel CNC`)
names(count_by_cnc)<-c("CNC", "Distributie")
count_by_cnc[,1]<-as.factor(count_by_cnc$CNC)
count_by_cnc |> 
  e_charts(CNC) |> 
  e_bar(Distributie, name = "") |> 
  #e_title("Programe de studii pe nivele CNC/EQF")|>
  e_tooltip()|>
  e_labels(show=TRUE, position = "right")%>%
  e_toolbox_feature(feature = "saveAsImage")
```



**Stacked Bar Chart visualisation using echarts4r**

```r
count_by_isced_cnc<-filter(RNCIS,RNCIS$Status=="Inregistrat"|RNCIS$Status=="Validat",is.na(RNCIS$Arhivat))
count_by_isced_cnc<-count(count_by_isced_cnc,count_by_isced_cnc$ISCED,count_by_isced_cnc$`Nivel CNC`)
names(count_by_isced_cnc)<-c("ISCED","Nivel_CNC", "Numar_programe")
count_by_isced_cnc<-count_by_isced_cnc %>% arrange(Numar_programe)
count_by_isced_cnc[57,1]<-"0388-Programe interdisciplinare in stiinte sociale"
count_by_isced_cnc[4,1]<-"0488-Programe interdisciplinare in administratie si drept"
count_by_isced_cnc[47,1]<-"0688-Programe interdisciplinare in TIC"
count_by_isced_cnc[68,1]<-"0388-Programe interdisciplinare in stiinte sociale"
count_by_isced_cnc[148,1]<-"0788-Programe interdisciplinare in inginerie"
count_by_isced_cnc[149,1]<-"0788-Programe interdisciplinare in inginerie"
count_by_isced_cnc<-count_by_isced_cnc%>%slice(80:151)



count_by_isced_cnc %>%
  group_by(Nivel_CNC)%>%
  e_charts(ISCED, height = 1000) %>%
  e_bar(Numar_programe,  stack="Nivel_CNC") %>% 
  #e_title("Frecventa grupe de baza COR/ESCO/ISCO in RNCIS")%>%
  e_tooltip()%>%
  e_labels(show=TRUE, position = "right")%>%
  e_flip_coords()%>%
  e_grid(
    left = "40%" # percentage = responsive
  )%>%
  e_toolbox_feature(feature = "saveAsImage")
```



**Function to align text left in ggplot2**

```r
#left text
text_left<-function(plot)
{
  g<-ggplotGrob(plot)
  idx<-which(g$layout$name=="title")
  idx2<-which(g$layout$name=="subtitle")
  g$layout$l[idx]<-2
  g$layout$l[idx2]<-2
  grid.newpage()
  grid.draw(g)
  return(g)
}
```

**Function to add footer to ggplot2 with caption for source and logo**

```r
add_footer<-function(sursa,logo)
{
  footer<-grobTree(#rectGrob(gp=gpar(fill="white",col=NA)),
    linesGrob(unit(c(0, 1), "npc"),unit(1.05, "npc"),gp = gpar(col = '#282A36', lwd = 3)),
    #rectGrob(x=unit(0.05, "npc"), y=unit(18.4, "npc"),height = unit(1.5,"cm"),width=unit(0.01,"npc"),gp=gpar(fill="#CF3536",col="#723843")),
    textGrob(sursa,x = 0.004,unit(0.5, "npc"),hjust=0,gp=gpar(col="gray20",fontsize=8,fontface="bold")),
    # textGrob("Surs\U0103: Eurostat",x=.78,hjust=-1.06,unit(1.6, "npc"),gp=gpar(col="gray20",fontface="bold",fontsize=8)),
    rasterGrob(logo, x = 0.850, hjust=0))
  return (footer)
}
```



**Custom theme function in ggplot2**

```r
anc_theme<-function(legend_p)
{
    theme(plot.subtitle = element_text(color="gray30",family = "serif", face="italic",size=16,margin=unit(c(0,0,0,0),units="mm")),
          plot.title = element_text(family = "serif",size=16,margin=unit(c(2,0,2,0),units="mm")),
          legend.title = element_blank(),
          plot.margin = unit(c(0,4,0,0), units = "mm"),
          legend.text = element_text(family = "serif", color = "black",size=10),
          axis.text.x = element_text(family = "serif",color="black",size=12,margin=unit(c(0,0,0,0),units="mm")),
          axis.text.y=element_text(family = "serif",color="black",size=12,margin=unit(c(0,0,0,0),units="mm")),
          axis.title.x = element_text(family = "serif", color = "black",size=12,margin=unit(c(4,4,4,4),units="mm")),
          axis.title.y = element_text(family = "serif", color="black",size=12,margin=unit(c(4,4,4,4),units="mm")),
          plot.background = element_blank(),
          panel.background = element_rect(fill="#ffffff"),
          legend.background = element_rect(color="white", fill="white"),
          panel.grid.minor.y = element_blank(),
          panel.grid.major.y = element_blank(),
          panel.grid.minor.x = element_blank(),
          panel.grid.major.x = element_line(color = "#bfbfbf"),
          axis.ticks=element_blank(),
          plot.caption = element_text(face="bold",color="gray20"),
          legend.position = legend_p,
          strip.background = element_rect( fill="white", linetype="solid"),
          strip.text =element_text(face=c("italic","bold"),size = 7))
}
```



**Single bar chart in ggplot2**

```r
count_by_cnc<-filter(RNCIS,RNCIS$Status=="Inregistrat"|RNCIS$Status=="Validat",is.na(RNCIS$Arhivat))
count_by_cnc<-count(count_by_cnc,count_by_cnc$`Nivel CNC`)
names(count_by_cnc)<-c("CNC", "Distributie")
count_by_cnc[,1]<-as.factor(count_by_cnc$CNC)
p<-ggplot(count_by_cnc, aes(x=as.factor(CNC), y=Distributie)) + 
  geom_bar(stat = "identity",position = "identity",fill="#CF3536", width = 0.4) +
  geom_hline(yintercept = 0, size = 1, colour="#333333") +
  labs(title = "", subtitle = "")+
  geom_label(label=count_by_cnc$Distributie, nudge_x = 0.25, nudge_y = 0.25)+
  anc_theme(legend_p = "none")+
  labs(title="Programe de studii pe nivele CNC/EQF",x="Numar programe",y="Nivel CNC",)+
  coord_flip()
final_plot<-text_left(p)
final_plot <- grid.arrange(final_plot,add_footer("Sursa: RNCIS",img2),heights=c(9,0.6))
```

**Grouped Bar Chart in ggplot2**

```r
CSC<-filter(RNCIS,RNCIS$Status=="Inregistrat"|RNCIS$Status=="Validat",is.na(RNCIS$Arhivat))
CSC<-count(CSC,CSC$`Nivel CNC`,Status)
names(CSC)<-c("CNC","Status" ,"Distributie")
p<-ggplot(CSC, aes(fill=Status, y=Distributie, x=as.factor(CNC))) + 
  geom_bar(position="dodge",stat = "identity",width = 0.2) +
  geom_hline(yintercept = 0, size = 1, colour="#333333") +
  labs(title = "", subtitle = "")+
  geom_label(label=CSC$Distributie, nudge_x = 0.25, nudge_y = 0.25)+
  scale_fill_manual(values=culori2)+
  anc_theme(legend_p = "bottom")+
  labs(title="Programe de studii pe nivele CNC/EQF si status",x="Nivel CNC",y="Distributie",)+
  coord_flip()
final_plot<-text_left(p)
final_plot <- grid.arrange(final_plot,add_footer("Sursa: RNCIS",img2),heights=c(9,0.6))
```