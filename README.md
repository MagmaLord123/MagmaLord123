#Lukasz Drzezla
#Programming Assessment
#27/05/2021

#define functions
def ProductAndPrice (productArrey, PriceArrey):
    #get products and prices for user 
    for i in range(5):
        product =  input("What is your product ? >> ")
        productArrey.append(product)
        try:
            productPrice =  float(input("What is the price of Product ?  >> "))
            PriceArrey.append(float(productPrice))
        except:
            productPrice = float(input ("invalid price. Pls try again  >> "))
            #if product price is valid append the price array
            PriceArrey.append(float(productPrice))
        
def InOrderP (ProductArray, PriceArray):
    #temperary variablas
    sortedA = False
    b = 0
    a = 0

    sortedPriceArray = []
    sortedProductArray = []

    while sortedA != True:
        if b!=5:
            minA = max(PriceArray)#get the minimum price in array 
            minB = int(minA) #cast the minA to a int as it comes out float from array and int is needed for next function index
            index = PriceArray.index(minB)# find the index on the minimum number and store it in index variable
            #append temperary arrays with the index that u found above
            sortedPriceArray.append(PriceArray[index])
            sortedProductArray.append(ProductArray[index])
            #delete product and price from orginal array
            del PriceArray[index]
            del ProductArray[index]
            b += 1
        a += 1
        rev = sorted(sortedPriceArray)
        rev.reverse()
        if rev == sortedPriceArray and a >= 6:#if array is sorted stop the while loop
            sortedA = True
    #reappend orginal arrays with the sorted temperary arrays
    if sortedA == True:
        PriceArray.append(sortedPriceArray)
        ProductArray.append(sortedProductArray)

def TotalandDiscount(ProductArray, PriceArray):
    #temperary variables
    SemiTotal = 0
    b = 0
    for i in PriceArray:#Add all of the numbers in the PriceArray
        SemiTotal += sum(i)
    print("Your Total befor Discount is " , SemiTotal , "£")
    minA = min(PriceArray[0])
    Discount = minA#Set discount to the lowest number in array
    print("Your discount is " , Discount , "£")
    Total = SemiTotal - Discount#Calculate the total after discount
    print("Your Total After Discount is " , Total , "£")
    


#variables
products =  []
prices = []

#call functions
ProductAndPrice(products, prices)
InOrderP(products,prices)
TotalandDiscount(products,prices)

for i in range(len(prices)):#loop for the length of the array
    print(products[i], "cost", prices[i])#print product and prices
