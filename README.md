# PRODIGY_CS_01
Python program that can encrypt and decrypt text using the Caesar Cipher algorithm and Allow users to input a message and a shift value to perform encryption and decryption.

# Define a function called caesar_cipher which takes a text and shift value as input
def caesar_cipher(text, shift):
    # Initialize an empty string to store the encrypted/decrypted text
    encrypted_text = ""
    
    # Iterate through each character in the input text
    for char in text:
        # Check if the character is an alphabet
        if char.isalpha():
            # Calculate the shifted ASCII value of the character
            shifted = ord(char) + shift
            
            # Check if the character is lowercase
            if char.islower():
                # Wrap around if the shifted value exceeds the ASCII range of lowercase letters
                if shifted > ord('z'):
                    shifted -= 26
                elif shifted < ord('a'):
                    shifted += 26
            
            # Check if the character is uppercase
            elif char.isupper():
                # Wrap around if the shifted value exceeds the ASCII range of uppercase letters
                if shifted > ord('Z'):
                    shifted -= 26
                elif shifted < ord('A'):
                    shifted += 26
            
            # Append the shifted character to the encrypted/decrypted text
            encrypted_text += chr(shifted)
        
        # If the character is not an alphabet, append it directly to the text
        else:
            encrypted_text += char
    
    # Return the encrypted/decrypted text
    return encrypted_text

# Define the main function
def main():
    # Prompt the user to choose encryption or decryption
    choice = input("Enter 'E' for encryption or 'D' for decryption: ")
    
    # If the user chooses encryption
    if choice == 'E':
        # Prompt the user to enter the message to encrypt
        message = input("Enter the message to encrypt: ")
        
        # Prompt the user to enter the shift value
        shift = int(input("Enter the shift value: "))
        
        # Call the caesar_cipher function with the message and shift value
        encrypted_message = caesar_cipher(message, shift)
        
        # Print the encrypted message
        print("Encrypted message:", encrypted_message)
    
    # If the user chooses decryption
    elif choice == 'D':
        # Prompt the user to enter the message to decrypt
        message = input("Enter the message to decrypt: ")
        
        # Prompt the user to enter the shift value
        shift = int(input("Enter the shift value: "))
        
        # Call the caesar_cipher function with the message and the negative of the shift value (to decrypt)
        decrypted_message = caesar_cipher(message, -shift)
        
        # Print the decrypted message
        print("Decrypted message:", decrypted_message)
    
    # If the user enters an invalid choice
    else:
        # Print an error message
        print("Invalid choice!")

# Execute the main function if this script is run directly
if __name__ == "__main__":
    main()

