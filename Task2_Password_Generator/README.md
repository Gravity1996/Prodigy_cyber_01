import random
import string

def generate_password(length, use_upper, use_lower, use_digits, use_special):
    characters = ''
    
    if use_upper:
        characters += string.ascii_uppercase
    if use_lower:
        characters += string.ascii_lowercase
    if use_digits:
        characters += string.digits
    if use_special:
        characters += string.punctuation

    if not characters:
        return "You must select at least one character set!"
    
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

def get_yes_or_no(prompt):
    response = input(prompt).lower()
    return response in ['y', 'yes']

# User input
try:
    length = int(input("Enter desired password length: "))
    use_upper = get_yes_or_no("Include uppercase letters? (y/yes/n/no): ")
    use_lower = get_yes_or_no("Include lowercase letters? (y/yes/n/no): ")
    use_digits = get_yes_or_no("Include numbers? (y/yes/n/no): ")
    use_special = get_yes_or_no("Include special characters? (y/yes/n/no): ")

    # Generate password
    password = generate_password(length, use_upper, use_lower, use_digits, use_special)
    print(f"Generated Password: {password}")

except ValueError:
    print("Please enter a valid number for password length!")
