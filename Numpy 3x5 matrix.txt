import numpy as np

print("\nTask 1]")
arr1 = np.arange(10,49)
print("1D Array : ",arr1)

print("\nTask 2]")
arr2=arr1[:15].reshape((3,5))
print("3x5 Matrix : ",arr2)

print("\nTask 3]")
new_arr=arr1[arr1%3==0]
print("Numbers Divisible by 3 : ",new_arr)

print("\nTask 4]")
a1 = np.random.randint(1,50,(3,3))
a2=np.random.randint(1,50,(3,3))
print("Array 1 : ",a1)
print("Array 2 : ",a2)

add = a1+a2
print("\nAddition of Array 1 & Array 2 : ")
print(add)

sub = a1-a2
print("\nSubtraction of Array 1 & Array 2 : ")
print(sub)

mul = a1*a2
print("\nMultiplication of Array 1 & Array 2 : ")
print(mul)

div = a1/a2
print("\nDivision of Array 1 & Array 2 : ")
print(div)