# **LOL Win Lose Model**

by Shuang Wu (shw076@ucsd.edu) , Yacheng Xiao (yaxiao@ucsd.edu)

---

## **Introduction and Problem Identification**

### "Win or Not Win, That's a Question" 
In the game, players always work hard for various important resources, but which elements are the key to victory of the game？
In short, we will use the data to predict whether a team will win.


In this model, we selected one of the most competitive leagues, the **2022 LCK game**, to predict the result. Since our predictions are mainly focus on win or loss, and there won't be the case of two teams are draw, we will use **Binary Classification** with the response variable 
**Result(win or lose)**. The **Accuracy** will be the most suitable metric in predicting the result since the data set are balanced: 
There's an equal amount of win and lose, and we will treat both FP(False Positive) and FN(False Negative) as equally important. Thus it is more 
suitable than the F-1 score, precision, and recall. 

To make predict rational, the features we use are all derived from the data in the game, not after the game (such as MVP, SVP 
attribution, etc.), and the Features we focus on are neutral resources (dragons, elders, heralds, barons, etc.) and team gaps (vision 
score gap, damage per minute, gold gap, etc.)

---

## **Baseline Model**
In our Baseline model, we intend to predict whether the team wins or not based on the team's side and control of neutral resources.

**Quantitative Features**: Dragons, Barons, Heralds, Elders,

**Nominal Features**: Side(blue/red), First dragon(1/0), First baron(1/0), First herald(1/0)

**Response Variable**: Result(Win(1)/Lose(0))

We encode **side** by OneHotEncoder() while other features remain the same since for other nominal features, there's already exist as 1(have) or 
0(not have). For quantitative features, are all of them are discrete values.

### **Conclusion based on Baseline Model**

We've reach accuracy of around 0.85, which is reasonably a good performance. We believe this is good model not only because relatively high accuracy 
but also intuitively, the more neutral resources also means giving heroes more buffs and more gold. And these can better strengthen heroes, making 
them easier to win in team battles.

---
## **Final Model**

**Gold** and **experience** are the keys to snowballing and winning in League of Legends. Because gold allows heroes to buy more items, the 
experience can strengthen the champion's skills, passive, health, etc., improving the champion's ability to fight against opponents.

### **What we have in baseline**

Neutral resources (variables in the Baseline Model) make sense because it immediately gives each champion a portion of gold and a temporary 
boost to almost all stats. This enhancement allows heroes to buy items with gold while their attributes increase, which will also improve their 
ability to fight against the opposing heroes or team fight to be close to the game's victory.

### **Gold XP Status**

In addition to neutral resources, there are other things that can track the player's gold and experience status. And these can be intuitively
reflected in **gold diff**, **xp diff** at different time, **first blood**(100 bonus gold), **first tower**(150 bonus gold), **turret plates**(175 
bonus gold for each plates, 875 for each tower). 

### **Importance of Turret**

The game's victory comes from dismantling the Nexus on the opposite side. However, if the team wants to destroy the Nexus on the opposite side, it 
must destroy the turret and inhibitors on the opposite side. If one side destroys 0 inhibitors in a game, we can be sure that the team loses
(because the opponent's Nexus is invincible if the opponent's inhibitor is not destroyed). Therefore, the number of demolished towers and inhibitors 
is also important to the game's victory, so we added **towers**, **inhibitors**, and **first three towers** to predict whether a team will win.

### **Team Performance**

The team's contribution also plays a vital role in the game's victory. If one side dies a lot in a short period, the team battle is basically lost. 
The trend of victory in team battles can be seen from **double kills**, **triple kills**. We didn't choose quadra kills and **pentakills** because 
they are rare in all matchups. In addition, we also passed **team kpm**(kill per minute), **team dpm**(death per minute), **vspm**(visual score per 
minute), and **dpm**( team damage per minute) to analyze the overall performance of the team, which can be used to predict the victory of the game.

New Features We Add Base on Baseline Model: doublekills, triplekills, quadrakills, firstblood, team kpm, 'firsttower', 'towers', 
'firsttothreetowers', 'turretplates', 'inhibitors', 'dpm', 'vspm', 'golddiffat10', 'xpdiffat10', 'golddiffat15', 'xpdiffat15'













