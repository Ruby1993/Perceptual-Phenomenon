# Statistics Project-Stroop task


## Background Information

In a Stroop task, participants are presented with a list of words, with each word displayed in a color of ink. The participant’s task is to say out loud the color of the ink in which the word is printed. The task has two conditions: a congruent words condition, and an incongruent words condition. In the congruent words condition, the words being displayed are color words whose names match the colors in which they are printed: for example RED, BLUE. In the incongruent words condition, the words displayed are color words whose names do not match the colors in which they are printed: for example PURPLE, ORANGE. In each case, we measure the time it takes to name the ink colors in equally-sized lists. Each participant will go through and record a time from each condition.

## Investigation
### Variables

Independent variable is the words conditions with congruent or incongruent color and meaning

Dependent variable is the time recorded for the test

### Hypothesis
Null hypothesis: there is no difference in the population mean time spent between congruent words task and incongruent words task.

H0: mean(congruent) = mean(incongruent)

Alternative hypothesis: the mean time spent for the congruent words task is different from the mean time spent for the incongruent words task.

Ha: mean(congruent) != mean(incongruent)

Here, mean(congruent) is the population mean of time spent on congruent words tasks, and $\mu(incongruent)$ is the population mean of time spent on incongruent words tasks.

Type of Hypothesis: two-tailed t-test with dependent samples

### Descriptive Statistics

```{r}

getwd()
data=read.csv('stroopdata.csv')
str(data)
summary(data)

#measure of central tendency and variability
library(psych)
describe(data)

```
### Distribution
```{r}
library(reshape2)
library(ggplot2)
data.1<-melt(data)
ggplot(aes(x=value,fill=variable),data=data.1)+
  geom_histogram(binwidth = 2,alpha=0.3)+
  scale_x_continuous(limits = c(0,40),breaks = seq(0,40,10))+
  facet_wrap(~variable)

```


###Statistic Test- two tailed t test

Set  significance level $$\alpha=0.05$$ And its critical statistic $$ t-value=\pm2.069 $$ with sample size n=24

```{r}

t.test(data$Congruent,data$Incongruent,paired=TRUE)

```
### Conclusion

T-test: t(23)=-8.0207,p=0, two-tailed

Confidence Interval: 95%CI=(-10.019028,-5.910555)

As statistic t < critical t, the test result is statistically significant and we could reject the null hypothesis. 
From the CI, we could come to the conclusion that the mean of time spent on the congruent words test is less than the time spent on the incongruent words test.

### Optional

For the reasons behind effects observed, it could be the human processing mechanism on the images.

The similar task I could think about is that 

The test works by examining the response time of the participant to say out loud the meaning other than the color the ink printed. 

