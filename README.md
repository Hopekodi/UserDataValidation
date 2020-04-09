import random
def generatePsw(firstname,lastname):
    first = firstname[0:2]
    last = lastname[0:2]
    rand = random.randint(10000,99999)
    key = first+last+str(rand)
    shuffledkey = ''.join(random.sample(key,len(key)))
    return key

def createUserID(firstname,lastname):
    first = firstname[0:2]
    last = lastname[0:2]
    rand = random.randint(100,999)
    key = first+last+str(rand)
    shuffledkey = ''.join(random.sample(key,len(key)))
    return shuffledkey


def getUserPassword():
    while True:
        psw = input("Please Enter Your Password\nNote: Password must be more than 7 characters\n>>")
        if (len(psw) > 7):
            password = psw
            break
        else:
            print("Error: Password Length must be more than 7...Try Again!!!\n")

            continue
    return password



def createDetails(firstname,lastname,email,password):
    details={
        'firstname':firstname,
        'lastname': lastname,
        'email': email,
        'password': password
    }
    return details

print('-'*40)
print('HNG Tech- NEW EMPLOYEE REGISTRATION')
print('-'*40)
print('\nPlease Fill in Your details\n')
employees={}
userID = 1
while True:
    first = input("Enter Your First Name: ")
    last = input("Enter Your Last Name: ")
    email = input("Enter Your Email: ")

    # userID = createUserID(first,last)


    generated = generatePsw(first,last)
    print("\nSuggested Password: "+ generated)


    while True:
        ans = input("Are You Ok with the Password?\nEnter '1' for Yes\nEnter '2' for No\nResponse>> ")
        if(ans=="1"):
            password = generated
            employees[userID] = createDetails(first, last, email, password)
            print(employees)
            userID += 1
            break
        elif(ans=="2"):
            password=getUserPassword()
            employees[userID] = createDetails(first, last, email, password)
            print(employees)
            userID += 1
            break
        else:
            continue

    Options = input("1-Enter another record\n2-Stop entering Records\nResponse>>")
    if(Options=="1"):

        continue
    elif(Options=="2"):
        break
    else:
        break

print("-"*40)
print("List of Users")

for x, y in employees.items():
    print("Employee "+str(x) + " Details:\n" + "First Name: "+y["firstname"] + "\nLast Name: " + y["lastname"]+ "\nEmail: " + y["email"]+ "\nPassword: " + y["password"]+"\n")


