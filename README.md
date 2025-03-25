from cryptography.fernet import Fernet
# key generation
key = Fernet.generate_key()
print("file encryption decryption using python")
print("\n")
# string the key in a file
with open('filekey.key', 'wb') as filekey:
   filekey.write(key)
# opening the key
with open('filekey.key', 'rb') as filekey:
    key = filekey.read()
 
# using the generated key
fernet = Fernet(key)
 
# opening the original file to encrypt
with open('sayali.txt', 'rb') as file:
    original = file.read()
print("encrypting file data")

# encrypting the file
encrypted = fernet.encrypt(original)
print(encrypted)
print("\n")
# opening the file in write mode and
# writing the encrypted data
with open('encrypt.txt', 'wb') as encrypted_file:
    encrypted_file.write(encrypted)
# using the key
fernet = Fernet(key)
print("decrypting file data") 
# opening the encrypted file
with open('encrypt.txt', 'rb') as enc_file:
    encrypted = enc_file.read()
 
# decrypting the file
decrypted = fernet.decrypt(encrypted)
print(decrypted) 
# opening the file in write mode and
# writing the decrypted data
with open('decrypt.txt', 'wb') as dec_file:
    dec_file.write(decrypted)
