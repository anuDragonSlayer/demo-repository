#gowrylakshmi santhosh kumar 201605629 January 2022 CA-07.py
#Display the theatre dashboard when it is part filled or fully and calculate the production costs 
# and how many days the movie can be run in the theatre with the given production cost

import random      #importing random function for random picking of tickets that are sold
#creating both the lists
list_A = [[1,2,3,4,5],[6,7,8,9,10]]
list_B = [[11,12,13,14,15],[16,17,18,19,20]]
#intialising row and column for incrementating later

print("Enter the production cost to management")
production_cost = int(input())                          #inputing production cost
print("Enter the cost of one seat in band A(Band A is the first 2 rows)")
price_of_A = int(input())                             #inputing cost of seats in band A
#calculating the price of seats in band B as we know the price in band A
price_of_B = int(price_of_A/2)    
print("The price of ticket in band B is " + str(price_of_B))                          
total_tickets_cost = (price_of_A + price_of_B)*10
print("\tAll these tickets are sold and it is house full")
row = 2
col = 5   
theatrelist =[ list_A , list_B ]
for row in theatrelist:                                 #This loop is for showing the list in multiple rows
    for col in row:
        print(col,end="")
        print()
print()

#Displaying the details for fully filled house
print("Case 1: When all the seats are sold")
print("Full house costs: \t\t $")
print("Production cost \t\t " + str(production_cost))
print()
print("Full house revenue")
print("Band-A 10 seats at " + str(price_of_A) + " per seat = " + str(price_of_A*10))
print("Band-B 10 seats at " + str(price_of_B) + " per seat = " + str(price_of_B*10))
print("Revenue total for one full house = " + str(total_tickets_cost))
print()
num_of_days = int(production_cost/total_tickets_cost)           #calculating how many days the movie can be played in the theatre
print("Number of shows to break even = " + str(num_of_days))
print()

rows = 2
cols = 5
sold_count_for_A = 0                                            #Intialising sold counts for A and B to increment it later
sold_count_for_B = 0
for r in range(rows):                                           #This loop is for generating random seats that are sold and not sold in band A
    for c in range(cols):
        list_A[r][c] = random.randint(0,1)
        if(list_A[r][c]==0):
            list_A[r][c]="not sold"
        else:
            list_A[r][c]="sold"
            sold_count_for_A = sold_count_for_A+1              #counting the number of seats sold in band A

for r in range(rows):                                            #This loop is for generating random seats that are sold and not sold in band A
    for c in range(cols):
        list_B[r][c] = random.randint(0,1)
        if(list_B[r][c]==0):
            list_B[r][c]="not sold"
        else:
            list_B[r][c]="sold"
            sold_count_for_B = sold_count_for_B+1               #counting the number of seats sold in band B

row = 2 
col = 5
combined_list =[ list_A , list_B ]
for row in combined_list:                                       #This loop is for showing the lists in multiple rows
    for col in row:
        print(col,end="")
        print()
print()
total_for_A = price_of_A*sold_count_for_A
total_for_B = price_of_B*sold_count_for_B
total_tickets_cost_for_part_filled = total_for_A + total_for_B            #calculating the total tickets cost

#calculating the number of days the movie can be played in the theatre
num_of_days_for_part_filled = int(production_cost/total_tickets_cost_for_part_filled)      

#Displaying the details for part filled house
print("Case 2: When only some seats are sold")
print("Part-house costs: \t\t $")
print("Production cost \t\t "+ str(production_cost))
print()
print("Part-house revenue: ")
print("Band-A "+ str(sold_count_for_A) + " seats at " + str(price_of_A) + " per seat = " + str(total_for_A))
print("Band-B "+ str(sold_count_for_B) + " seats at " + str(price_of_B) + " per seat = " + str(total_for_B))
print("Revenue total for one part house " + str(total_tickets_cost_for_part_filled))
print("Number of shows to break-even " + str(num_of_days_for_part_filled))
