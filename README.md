import string

print(f'{"-"*30:^60}')
print(f'{"Welcome to Vigenère Cipher":^60}')
print(f'{"-"*30:^60}')
print("Please select one of the following options:")
print("1 - Encrypt a message")
print("2 - Decrypt a message")
print("3 - Brute force")
print("4 - QUIT")

def encrypt():
    # asking user for the password, ensuring that the password is only characters if not will be giving an error
    valid = False
    while valid == False:
        password = input(f'\n{"Enter the password:":<30}').upper()
        spaces = password.find(" ", 0, len(password))
        check = password.isalpha()
        if spaces > 0 or check == False:
            print("\nInvalid! No numbers, special charcters or spaces allowed in messages")
            valid = False
        else:
            valid = True

    # asking the user for the key number, ensuring that the key number is between 1-26 and only contains numbers, if not will be giving an error
    valid = False
    while valid == False:
        try:
            key = int(input(f'{"Enter the key number (1-26):":<30}'))
            if key >= 1 and key <= 26:
                valid = True
            else:
                print("\nInvalid key! Please enter a number between 1-26.\n")
                valid = False
        except ValueError:
            print("\nInvalid key! Please enter an integer.\n")

    # asking user to enter the message, ensuring that the message doesn't contain spaces, numbers, special characters and is shorter in length than the password, if it is an error will be given
    valid = False
    while valid == False:
        message = input(f'{"Enter your message:":<30}').upper()
        valid = True
        spaces = message.find(" ", 0, len(message))
        check = message.isalpha()
        if spaces > 0 or check == False:
            print("\nInvalid! No numbers, special characters or spaces allowed in messages\n")
            valid = False
        elif len(message) < len(password):
            print("\nInvalid! the message can\'t contain less characters than the password\n")
            valid = False
        else:
            valid = True
    
    # setting the variables - encrypted and passwordindex so they start of at 0 then repeat in the loop
    passwordindex = 0
    alphabet = string.ascii_uppercase
    encrypted = ""
    for index in range(len(message)):
        # converting message to its ascii value - number
        asciivalue = ord(message[index])
        # finding the number at which the letters of the passowrd land on, eg. A -> 1
        passwordvalue = alphabet.find(password[passwordindex])
        # adding one to the password index ensures it will go to the next letter
        passwordindex += 1
        if passwordindex >= len(password):
            passwordindex = 0
        # finding the newascii value by adding the passwordvalue and subtacting the key, if the value goes over 90 or under 60 you will either add or subtract 26 to ensure it remains a letter when converting back to a letter
        newasciivalue = asciivalue + passwordvalue - key
        if newasciivalue > 90:
            newasciivalue = newasciivalue - 26
        if newasciivalue < 65:
            newasciivalue = newasciivalue + 26
        # ecrypting the number by converting it to its ascii value then printing the ecrypted message
        encrypted += chr(newasciivalue)
    print(f'{"Your encrypted message is:":<30s}{encrypted}')

def decrypt():
    # asking user for the password, ensuring that the password is only characters if not will be giving an error
    valid = False
    while valid == False:
        password = input(f'\n{"Enter the password:":<30}').upper()
        spaces = password.find(" ", 0, len(password))
        check = password.isalpha()
        if spaces > 0 or check == False:
            print("\nInvalid! No numbers, special charcters or spaces allowed in messages")
            valid = False
        else:
            valid = True

    # asking the user for the key number, ensuring that the key number is between 1-26 and only contains numbers, if not will be giving an error
    valid = False
    while valid == False:
        try:
            key = int(input(f'{"Enter the key number (1-26):":<30}'))
            if key >= 1 and key <= 26:
                valid = True
            else:
                print("\nInvalid key! Please enter a number between 1-26.\n")
                valid = False
        except ValueError:
            print("\nInvalid key! Please enter an integer.\n")

    # asking user to enter the message, ensuring that the message doesn't contain spaces, numbers, special characters and is shorter in length than the password, if it is an error will be given
    valid = False
    while valid == False:
        message = input(f'{"Enter your message:":<30}').upper()
        valid = True
        spaces = message.find(" ", 0, len(message))
        check = message.isalpha()
        if spaces > 0 or check == False:
            print("\nInvalid! No numbers, special characters or spaces allowed in messages\n")
            valid = False
        elif len(message) < len(password):
            print("\nInvalid! the message can\'t contain less characters than the password\n")
            valid = False
        else:
            valid = True

    # setting the variables - encrypted and passwordindex so they start of at 0 then repeat in the loop
    passwordindex = 0        
    alphabet = string.ascii_uppercase
    decrypted = ""
    for messageindex in range(len(message)):
        # converting message to its ascii value - number
        asciimessage = ord(message[messageindex])
        # finding the number at which the letters of the passowrd land on, eg. A -> 1
        passwordvalue = alphabet.find(password[passwordindex])
        # adding one to the password index ensures it will go to the next letter
        passwordindex += 1
        if passwordindex >= len(password):
            passwordindex = 0
        str(key)
        # finding encrypted message by doing the opposite of encryption: subtacting the passwordvalue and adding the key, if the value goes over 90 or under 60 you will either add or subtract 26 to ensure it remains a letter when converting back to a letter
        uncrypted = (asciimessage + key - passwordvalue)
        if uncrypted < 65:
            uncrypted = uncrypted + 26
        if uncrypted > 90:
            uncrypted = uncrypted - 26
        # decrypting the number by converting it to its ascii value then printing the decrypted message
        decrypted += chr(uncrypted).lower()
    print(f'{"Your decrypted message is:":<30s}{decrypted}')

def brute():
    # asking user for the password, ensuring that the password is only characters if not will be giving an error
    valid = False
    while valid == False:
        password = input(f'\n{"Enter the password:":<30}').upper()
        spaces = password.find(" ", 0, len(password))
        check = password.isalpha()
        if spaces > 0 or check == False:
            print("\nInvalid! No numbers, special charcters or spaces allowed in messages")
            valid = False
        else:
            valid = True

    # asking user to enter the message, ensuring that the message doesn't contain spaces, numbers, special characters and is shorter in length than the password, if it is an error will be given
    valid = False
    while valid == False:
        message = input(f'{"Enter your message:":<30}').upper()
        valid = True
        spaces = message.find(" ", 0, len(message))
        check = message.isalpha()
        if spaces > 0 or check == False:
            print("\nInvalid! No numbers, special characters or spaces allowed in messages\n")
            valid = False
        elif len(message) < len(password):
            print("\nInvalid! the message can\'t contain less characters than the password\n")
            valid = False
        else:
            valid = True
    
    print("\nYour decrypted message is:\n")

    # doing almost the same thing as decrypting except adding a key index in a for loop because the key can vary from 1-26, there will be 26 tries
    passwordindex = 0 
    alphabet = string.ascii_uppercase
    decrypted = ""
    for keyindex in range(1, 27):
        for messageindex in range(len(message)):
            asciimessage = ord(message[messageindex])
            passwordvalue = alphabet.find(password[passwordindex])
            passwordindex += 1
            if passwordindex >= len(password):
                passwordindex = 0
            str(keyindex)
            unencrypted = (asciimessage + keyindex - passwordvalue)
            if unencrypted < 65:
                unencrypted = unencrypted + 26
            if unencrypted > 90:
                unencrypted = unencrypted - 26
            decrypted += chr(unencrypted).lower()
        print(f'{keyindex:<5}{decrypted}')
        # setting the variables back to 0 once the decrypted message has been printed with one key value, also adds 1 to the keyindex to repeat the process
        keyindex += 1
        decrypted = ""
        messageindex = 0
        passwordindex = 0

def quit():
    if choice == 4:
        print("GoodBye")

# this process of either encrypting, decrypting or brute force should keep going until the user selects '4' - therefore made a while statement
option = True
while option == True:
    valid = False
    while valid == False:
        try:
            # asking the user for a choice and ensuring that they only put a number that is between 1-4
            choice = int(input(f'\n{"Enter your choice:":<30}'))
            if choice >= 1 and choice <= 4:
                valid = True
            else:
                print("\nInvalid choice! Please enter a number between 1-4.")
        except ValueError:
            print("\nInvalid choice! Please enter an integer.")

    if choice == 1:
        encrypt()
        option = True

    if choice == 2:
        decrypt()
        option = True

    if choice == 3:
        brute()
        option = True

    if choice == 4:
        quit()
        option = False
