# R-logit-

###default.glm
default2003<-glm(result~score+dti+ltv+i_rate,data=result2003,family=binomial(link="logit"))
default2003<-na.omit(default2003)
idiffer<-mean(result2003$i_rate, na.rm = TRUE)

####create idifferential 
result2003<-data.frame(result2003)
result2003$idiffer<-log(result2003$i_rate/mean(result2003$i_rate))
###run glm with idifferential

default2003<-glm(result~score+dti+ltv+idiffer,data=result2003,family=binomial(link="logit"))
result2003$i_rate<-NULL
head(result2003)

summary(default2003)


##get summary
glm1999<- summary(default)



