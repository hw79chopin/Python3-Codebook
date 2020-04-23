############# Association rule #############

install.packages('arules')

library(arules)

setwd("/Users/junghyunwoo/Downloads")

df <- read.csv("concated_5.csv", header=T, encoding = 'UTF-8-BOM')

df

df$grade_categories <- as.factor(df$grade_categories)
df$studytime <- as.factor(df$studytime)
df$failures <- as.factor(df$failures)
df$activities <- as.factor(df$activities)
df$paid <- as.factor(df$paid)
df$freetime <- as.factor(df$freetime)
df$internet <- as.factor(df$internet)
df$romantic <- as.factor(df$romantic)
df$famrel <- as.factor(df$famrel)

rules <- apriori(df, parameter = list(supp=0.5, conf=0.5))

inspect(rules)

rules <- subset(rules, subset = lift >= 1) # lift > 1

rules.sorted <- sort(rules, by="lift")

inspect(rules.sorted)

rules.sorted <- sort(rules, by="confidence")

inspect(rules.sorted)

