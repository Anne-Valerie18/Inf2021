library(rvest)
library(ggplot2)
library(dplyr)


url_skysports="https://www.skysports.com/world-cup-table"
dataread=read_html(url_skysports)
dataread

table=html_table(dataread)
length(table)



# Creations du data frame combine!
sport<-function(){
  url_skysports="https://www.skysports.com/world-cup-table"
  dataread=read_html(url_skysports)
  table=html_table(dataread)
  tabsport1=table[[1]]
  tabsport2=table[[2]]
  tabsport3=table[[3]]
  tabsport4=table[[4]]
  tabsport5=table[[5]]
  tabsport6=table[[6]]
  tabsport7=table[[7]]
  tabsport8=table[[8]]
  data<-list(tabsport1,tabsport2,tabsport3,tabsport4,tabsport5,tabsport6,tabsport7,tabsport8)
  
  tablesport=do.call(rbind,data)
  tablesport
  
  return(tablesport)
}
df_sport<-sport()
df_sport<-df_sport[,-c(11)]
df_sport<-df_sport[,-c(1)]

#Diagramme en baton des 10 equipes ayant les points les plus eleves
df_sport%>%group_by(`Team`)%>%count(Pts)%>%arrange(desc(Pts))%>%head(10)%>%ggplot(aes(y=`Team`,x=`Pts`))+geom_bar(stat = 'identity',fill='pink')
