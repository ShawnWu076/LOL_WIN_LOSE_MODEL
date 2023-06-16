# **LOL Win Lose Model**

by Shuang Wu (shw076@ucsd.edu) , Yacheng Xiao (yaxiao@ucsd.edu)

---

## **Introduction**

### "Win or Not Win, That's a Question" 
In the game, players always work hard for various important resources, but which elements are the key to the victory of the game？
In short, we will use known data to predict whether a team will win or not.


In this model, we selected the one of the most competitive leagues, the **2022 LCK game** to predict result. Since our prediction are 
mainly focus on win or lose and there won't be the case two team are draw, we will use **Binary Classification** with response variable 
**Result(win or lose)**. The **Acuracy** will be the moset suitable metrics in predicting the result since the data set are balanced: 
there's equal amount win and lose, and we will treat both FP(False Positive) and FN(False Negative) equally important. Thus it is more 
suitable than F-1 score, precision and recall. 

In order to predict the rationality, the features we use are all derived from the data in the game, not after the game (such as MVP, SVP 
attribution, etc.), and the Features we focus on are neutral resources (dragons, elders , heralds, barons, etc.) and team gaps (vision 
score gap, damage per minute, gold gap, etc.)

---

## **Baseline Model**
In our Baseline model, we intend to predict whether the team wins or not based on the team's side and control of neutral resources.

**Quantitative Features**: Dragons, Barons, Heralds, Elders,

**Nominal Features**: Side(blue/red), First dragon(1/0), First baron(1/0), First herald(1/0)

**Response Variable**: Result(Win(1)/Lose(0))








