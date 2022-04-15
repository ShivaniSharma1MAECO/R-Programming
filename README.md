# R-Programming


1. 

Question - scatterplot matrix of family wealth WEALTH and science scores science by gender sex and region region


Code :



ggplot(data = dat_small,
       mapping = aes(x = WEALTH, y = science)) +
  geom_point(aes(color = sex)) +
  facet_wrap( ~ Region) +
  labs(x = "Family Wealth", y = "Science Scores") +
  theme_bw() +
  theme(legend.title = element_blank())

 ![ch4-18-1](https://user-images.githubusercontent.com/100988969/163621591-1553a1dc-eef0-4c75-ab5d-6acf47915dda.png)


2.



Question : average science scores and N counts by both gender and country and save the dataset as science_summary


Code : 



science_summary <- dat[, 
                       .(Science = mean(science, na.rm = TRUE), 
                         Freq = .N),
                       by = c("sex", "CNT")]


head(science_summary)
##       sex       CNT Science  Freq
## 1: Female Australia   498.0  7163
## 2:   Male Australia   499.4  7367
## 3:   Male    Brazil   400.8 11068
## 4: Female    Brazil   396.3 12073
## 5: Female    Canada   515.3 10022
## 6:   Male    Canada   517.3 10036

ggplot(data = science_summary,
       mapping = aes(x = CNT, y = Science, fill = sex)) +
  geom_bar(stat = "identity", position = "dodge") +
  coord_flip() +
  labs(x = "", y = "Science Scores", fill = "Gender") +
  theme_bw()


![ch4-21-1](https://user-images.githubusercontent.com/100988969/163621739-3e7be0ac-13e7-47d8-ae27-064db9d9bfee.png)

3.
Question- number of students from each country) to determine the size of the dots in the plot, using size = Frequency

Code :



ggplot(data = science_summary,
       mapping = aes(x = CNT, y = Science, size = Freq, fill = sex)) +
  geom_point(shape = 21) +
  coord_flip() +
  theme_bw() +
  labs(x = NULL, y = "Science Scores", fill = "Gender",
       size = “Frequency")


![ch4-22-1](https://user-images.githubusercontent.com/100988969/163621851-513c43fe-22a0-4860-8d79-e45f94e64266.png)
