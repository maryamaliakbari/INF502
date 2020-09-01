```python
def pythagoreanTheorem(length_a, length_b):  # define pythagoreanTheorem function with two variables of length_a and length_b
    length_c =(length_a **2 + length_b ** 2) ** (1/2) # pythagoreanTheorem formula, calculate hypotenuse
    return length_c  #return the length_c
pythagoreanTheorem(10, 5)
pythagoreanTheorem(7, 9)
pythagoreanTheorem(3, 8)

outputs:
11.180339887498949
11.40175425099138
8.54400374531753




def list_mangler(list_in):       
    list_new = [] #create new list
    for i in list_in:  #check every value in list_in
        if i % 2 == 0:  #check if the value is even
            list_new.append(i * 2) # if the value is even then double it and add it to the new list
        else:  
            list_new.append(i * 3) # if the value is not even(is odd) then tripple it and add it to the new list
    return list_new 
list_mangler([3, 4, 9, 10])    
list_mangler([1, 4, 8, 10, 13, 18, 21, 30])  
list_mangler([0, 2, 7, 12, 15, 30])

outputs:    
[9, 8, 27, 20]
[3, 8, 16, 20, 39, 36, 63, 60]
[0, 4, 21, 24, 45, 60]




import statistics
def grade_calc(grades_in, to_drop):
    grades_in.sort() #sort grades in list in ascending order
    del grades_in[:to_drop]  #delete first to to_drop elements of the grades in list
    average = statistics.mean(grades_in) # take average of the list
    if average >= 90: 
        new_grade = "A"
    elif average >= 80: 
        new_grade = "B"    
    elif average >= 70: 
        new_grade = "C"
    elif average >= 60: 
        new_grade = "D"
    else:
        new_grade = "F"
    return new_grade  #return new letter grade
grade_calc([65, 85, 90, 100], 2)    
grade_calc([40, 30, 60, 75, 83, 90, 20], 1)
grade_calc([72, 98, 10, 46, 100, 54, 92, 0], 3)

outputs:
'A'
'D'
'B'
    



def odd_even_filter(numbers): 
    even_list= [] # create list of even numbers
    odd_list = [] # create list of odd numbers
    for i in numbers: # for each value in numbers list 
        if (i % 2 == 0): #check if the value is even
            even_list.append(i) # add the value to even list
        else: 
            odd_list.append(i) # if value is not even(is odd) add it to odd list
    new_list = [even_list, odd_list] # create the new list with seperate even list and odd list
    return new_list
odd_even_filter([1, 2, 3, 4, 5])
odd_even_filter([3, 4, 8, 11, 14, 17, 24, 39])
odd_even_filter([1, 4, 5, 12, 19, 37, 44, 59, 82, 93])

outputs:             
[[2, 4], [1, 3, 5]] 
[[4, 8, 14, 24], [3, 11, 17, 39]]
[[4, 12, 44, 82], [1, 5, 19, 37, 59, 93]]
    
