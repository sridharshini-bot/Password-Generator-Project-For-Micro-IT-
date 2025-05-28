import random
import string

def generate_password(length=12, use_uppercase=True, use_lowercase=True, use_numbers=True, use_special=True):
    character_pool = ""
    
    if use_uppercase:
        character_pool += string.ascii_uppercase
    if use_lowercase:
        character_pool += string.ascii_lowercase
    if use_numbers:
        character_pool += string.digits
    if use_special:
        character_pool += string.punctuation
    
    if not character_pool:
        raise ValueError("At least one character type must be selected!")
    
    password = "".join(random.choice(character_pool) for _ in range(length))
    return password


while True:
    try:
      
        length = int(input("Enter password: "))
        if length <= 0:
            print("Password length must be a positive number.")
            continue
        break
    except ValueError:
        print("Invalid input! Please enter a numeric value.")

use_uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
use_lowercase = input("Include lowercase letters? (y/n): ").lower() == 'y'
use_numbers = input("Include numbers? (y/n): ").lower() == 'y'
use_special = input("Include special characters? (y/n): ").lower() == 'y'

try:
    password = generate_password(length, use_uppercase, use_lowercase, use_numbers, use_special)
    print(f"Generated Password: {password}")
except ValueError as e:
    print(e)
