---
title: Day 8 - Rmarkdown .docx documents in R
date: 2022-02-14T14:20:23.587Z
draft: false
featured: false
image:
  filename: featured
  focal_point: Smart
  preview_only: false
---
Log: Today I used Rmarkdown and R to get data from a file, process it and create some custom charts. Then I knitted the .Rmd file using Rmarkdown and created a .docx file. 

Here is an code snipped that gets the data, plots it and creates some notes about the interpretation (auto-interpretation) given specific values from the data frame.

````r
```{r,echo=FALSE,warning=FALSE, message=FALSE,error=FALSE,fig.width=7}
# Buletin informativ Q4 2021------------
# FILTER DATES for Q4 -----------------
nov_2021_filter<-
  RNCISwDates%>%filter(RNCISwDates$`Data intrare dosar ( ZI/LU29-05-15/AN)`>="2021-07-01" & RNCISwDates$`Data intrare dosar ( ZI/LU29-05-15/AN)`<="2021-09-30")

nov_2021_filter<-filter(nov_2021_filter,nov_2021_filter$Status=="Inregistrat"|nov_2021_filter$Status=="Validat", is.na(nov_2021_filter$Arhivat))
nov_2021_filter<-count(nov_2021_filter,nov_2021_filter$Status)
names(nov_2021_filter)<-c("Status", "Distributie")
nov_2021_filter[,1]<-as.factor(nov_2021_filter$Status)
interpretare<-nov_2021_filter
p<-ggplot(nov_2021_filter, aes(x=as.factor(Status), y=Distributie)) + 
  geom_bar(stat = "identity",position = "identity",fill="#CF3536", width = 0.4) +
  geom_hline(yintercept = 0, size = 1, colour="#333333") +
  labs(title = "", subtitle = "")+
  geom_label(label=nov_2021_filter$Distributie, nudge_x = 0.25, nudge_y = 0.25)+
  anc_theme(legend_p = "none")+
  labs(title="",x="Numar programe",y="Status",)+
  coord_flip()
```

```{r,fig.show='hide',echo=FALSE,warning=FALSE, message=FALSE,error=FALSE}
final_plot<-text_left(p)
```

```{r,echo=FALSE,warning=FALSE, message=FALSE,error=FALSE}
final_plot <- grid.arrange(final_plot,add_footer("Sursa: RNCIS",img2),heights=c(9,0.6))

```

```{r,echo=FALSE,warning=FALSE, message=FALSE,error=FALSE,fig.width=7,results='asis'}
cat(paste0("* În trimestrul 3 din 2021 au fost validate ", interpretare[2,2]," calificări/programe de studii noi; Pentru aceste programe încă nu a fost finalizat procesul de înregistrare;"), sep = "\n")
cat(paste0("* În trimestrul 3 din 2021 au fost înregistrate ", interpretare[1,2]," calificări/programe de studii noi; în acest număr sunt incluse si actualizările programelor de studii realizate de către universităti "), sep = "\n")

```
````