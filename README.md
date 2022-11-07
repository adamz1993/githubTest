def test(x,y):
    if x=='ODD':
        sum_all=0
        for i in range(1,y+1,2):
            sum_all+=i
        return sum_all
    elif x=='EVEN':
        sum_all=0
        for i in range(2,y+1,2):
            sum_all+=i
        return sum_all
    else:
        return y**0.5

dic={}
count=0
for i in range(5):
    count+=1
    mahrozet=str(input('what is youre sentence?'))
    number=int(input('choose youre number'))
    dic[count]=[]
    dic[count].append(mahrozet)
    dic[count].append(number)
    dic[count].append(test(mahrozet,number))


#שאלה 2
customer=int(input('how much customer there is?'))
count=0
count1=0
count2=0
for x in range(customer):
    ans=input('what is youre credit card?')
    while ans!='American' and ans!='Visa' and ans!='Other':
        print('wrong card,please choose again')
        ans = input('what is youre credit card?')
    if ans=='American':
        count+=1
    elif ans=='Visa':
        count1+=1
    else:
        count2+=1
ce_American=count/customer*100
ce_Visa=count1/customer*100
print('American',ce_American,'%')
print('Visa',ce_Visa,'%')



#שאלה 3
import random
keylist=['A','B','C','D','E','F','G']
dic={}
for x in range(3):
 dickey=random.choice(keylist)
 keylist.remove(dickey)
 dic[dickey]=random.randrange(2,100,2)
for x in dic:
 print(x,":" ,dic[x], end=",")




#שאלה 4
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv('WorkOrders.csv',index_col='WO')
data['TotalCost']=data['PartsCost']+data['LbrHrs']*250
data.groupby('TotalCost').max().tail(5)
data.iloc[data['LbrHrs'].argmax(),1]
data.iloc[data['LbrHrs'].argmax(),4]
pd.pivot_table(data,
               index='OrderDay',
               columns='ServiceType',
               values='TotalCost',
               aggfunc='mean')
data2=data.groupby('ServiceType')['Worker'].count()
data2.plot(kind='bar',title='number of orders')
