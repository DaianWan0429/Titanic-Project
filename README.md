# Titanic-Project
import numpy as np
import pandas as pd
from pandas import Series,DataFrame

#load the datafile#
titanic_df = pd.read_csv("E:/python udemy/train.csv")
titanic_df.info() #overview the datafile#

#passangers on the Titanic#
import matplotlib.pyplot as plt
import seaborn as sns
%matplotlib inline

sns.factorplot('Sex',data=titanic_df) #plot group by gender,class#
sns.factorplot('Sex',data=titanic_df,hue='Pclass')
sns.factorplot('Pclass',data=titanic_df,hue='Sex')

#create a new column seperate male,female and children#
def male_female_children(passanger):
  Age,Sex = passanger  
  if Age < 16:
     return 'child'
  else:
     return Sex

titanic_df['person'] = titanic_df[['Age','Sex']].apply(male_female_passanger,axis=1

sns.factorplot('Survived',data=titanic_df,hue='person')
titanic_df['Age'].hist(bins=70)
titanic_df['person'].value_counts()

#analyze age distribution#
fig = sns.FacetGrid(titanic_df,hue='Person',aspect=4) #modify hue to get age distribution by other variables#
fig.map(sns.kdeplot,'Age',shade=True
oldest = titanic['Age'].max()
fig.set(xlim(0,oldest))
fig.add_legend()

#passangers' deck#
deck = titanic_df['Cabin'].dropna()
levels = []
for level in deck:
    levels.append(level[0])
cabin_df = DataFrame(levels)
cabin_df.columns = ['Cabin']
sns.factorplot('Cabin',data=titanic_df,palette='winter_d') #plot cabin distribution#
#plot cabin excludeing T class distribution#
cabin_df = cabin_df[cabin_df.Cabin != 'T']
sns.factorplot('Cabin',data=titanic_df,palette='summer')
#plot where the passanger come from#
sns.factorplot('Embarked',data=titanic_df,hue='Pclass')

