

#Datasset Price=X1, Income=X2 and Demand=Y (Class Label)

Demand_Y=[100 , 75 , 80 ,70 , 50, 65, 90, 100, 110,60]
Price_X1=[5 , 7 , 6 ,6 , 8, 7, 5, 4, 3,9]
Income_X2=[1000, 600, 1200, 500 ,300 ,400 ,1300 ,1100, 1300, 300]

y=[]
x1=[]
x2=[]

Square_y=[]
Square_x1=[]
Square_x2=[]

yx1=[]
yx2=[]
x1x2=[]

b0=0
b1=0
b2=0

#Calculating Average
Mean_X1 = sum(Price_X1)/len(Demand_Y)
Mean_X2 = sum(Income_X2)/len(Demand_Y)
Mean_Y = sum(Demand_Y)/len(Demand_Y)

for i in range(len(Demand_Y)):

    y.append(Demand_Y[i]-Mean_Y)
    x1.append(Price_X1[i]-Mean_X1)
    x2.append(Income_X2[i]-Mean_X2)
    Square_y.append(y[i]**2)
    Square_x1.append(x1[i]**2)
    Square_x2.append(x2[i]**2)
    yx1.append(y[i]*x1[i])
    yx2.append(y[i] * x2[i])
    x1x2.append(x1[i] * x2[i])

#Calculating b1
temp1=((sum(Square_x2))*(sum(yx1)))-((sum(x1x2))*(sum(yx2)))
temp2=(((sum(Square_x1))*(sum(Square_x2)))-(sum(x1x2)**2))
b1=temp1/temp2
b1=round(b1,3)

#Calculating b2
temp1=((sum(Square_x1))*(sum(yx2)))-((sum(x1x2))*(sum(yx1)))
temp2=(((sum(Square_x1))*(sum(Square_x2)))-(sum(x1x2)**2))
b2=temp1/temp2
b2=round(b2,3)

#Calculating b0
b0=Mean_Y-(b1*Mean_X1)-(b2*Mean_X2)
b0=round(b0,3)

#Prediction
print("")
print("Final Coefficients")
print("B0 : ",b0)
print("B1 : ",b1)
print("B2 : ",b2)

print("")
print("Final Equation")
print(b0 ," + ", b1,"(Price) + ",b2 )

print("")

while True:
    print("")
    print("Time to Predict")
    Price=float(input("Enter Price : "))
    Income=float(input("Enter Income : "))
    print("")
    PredictedValue=b0+(b1*Price)+(b2*Income)
    PredictedValue=round(PredictedValue,2)
    print("Predicted Value is : ",PredictedValue)
    print("")
    exit=input("DO YOU WANT TO EXIT Y/N ?")
    if(exit=="y" or exit=="Y"):
        break
