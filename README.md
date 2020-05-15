# Buoy-PDE-Sim
2D PDE simulator with boundary conditions

# importing "math" for mathematical operations 
import math 
#for dealing with 2d array
import numpy as np

print('This is a bouy PDE simulator')

# Flexible 2d array
n=int(input('How many rows? '))
m=int(input('How many columns? '))
print('\r') #newline
rows, cols = (n, m) 

#mass assign value
p=round(0.00,2)
arr = np.array([[p for i in range(cols)] for j in range(rows)])

print('Table Initialized to 0')

#change first column to function working
print('First column set to function')
for l in range (n): 
  arr[l][0]=round(math.sin(l/(n-1)*2*math.pi), 2)

#change last column to function working
print('Last column set to function')
for l in range (n): 
  arr[l][m-1]=round(math.sin(l/(n-1)*2*math.pi), 3)

#change first row function working
print('First row set to function')
for k in range (m): 
  arr[0][k]=round(math.sin(k/(m-1)*2*math.pi), 3)

print('\r') #newline

#print by row up
for i in range (n):
  print (arr[n-1-i,:])
print('\r') #newline

#Attempt to fill in the rest of the table
#Take input for delta x and t and display it
deltax=float(input ('delta x = ')) 
deltat=float(input('delta t = '))


for i in range (1,n):
  for j in range (1,m-1):
    arr[i][j]=round(arr[i-1][j]+((arr[i-1][j]-arr[i-1][j-1])/deltax), 3)

#print by row up
for i in range (n):
  print (arr[n-1-i,:])


a = 0
b = arr[0][m-1]
if b == a:
  print("-0 = 0")
