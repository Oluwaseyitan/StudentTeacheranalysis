# StudentTeacheranalysis
In [1]:
# import numpy as np
import pandas as pd
In [10]:
data = pd.read_csv('Desktop/Research Questionnaire .csv')
print (data)

                                           
In [12]:
# encoding one categorical column and displaying encoder classes
from sklearn.preprocessing import LabelEncoder
encoder = LabelEncoder()
data["Age"]=encoder.fit_transform(data["Age"])
print(encoder.classes_)


['20 - 25' 'Above 25' 'Below 20']

In [16]:

from sklearn.preprocessing import LabelEncoder
encoder = LabelEncoder()
i=0
for col in data:
    x_enc=encoder.fit_transform(data[col])
    df_enc=pd.DataFrame(x_enc, columns=[col])
    if i>0:
        df_cat=df_cat.join(df_enc)
    else:
        df_cat=df_enc
    i=i+1
    #print(col, " ", encoder.classes_)
df_cat.head()

In [18]:

#Save file
df_cat.to_csv('Desktop/Research Questionnaire .csv')
