# VIGENERE-CIPHER
## EX. NO: 4
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
```
# Function to encrypt using Vigenère Cipher
def encrypt(plaintext, key):
    ciphertext = ""
    key_len = len(key)
    j = 0  # key index

    for ch in plaintext:
        if ch.isalpha():
            base = 'A' if ch.isupper() else 'a'
            k = ord(key[j % key_len].lower()) - ord('a')
            cipher_char = chr((ord(ch) - ord(base) + k) % 26 + ord(base))
            ciphertext += cipher_char
            j += 1
        else:
            ciphertext += ch  # keep symbols and spaces same

    return ciphertext


# Function to decrypt using Vigenère Cipher
def decrypt(ciphertext, key):
    plaintext = ""
    key_len = len(key)
    j = 0  # key index

    for ch in ciphertext:
        if ch.isalpha():
            base = 'A' if ch.isupper() else 'a'
            k = ord(key[j % key_len].lower()) - ord('a')
            plain_char = chr((ord(ch) - ord(base) - k + 26) % 26 + ord(base))
            plaintext += plain_char
            j += 1
        else:
            plaintext += ch

    return plaintext


# ✅ Main
plaintext = input("Enter plaintext: ")
key = input("Enter key (alphabetic only): ")

encrypted = encrypt(plaintext, key)
print("Encrypted text:", encrypted)

decrypted = decrypt(encrypted, key)
print("Decrypted text:", decrypted)
```
## OUTPUT

<img width="443" height="227" alt="image" src="https://github.com/user-attachments/assets/e9d8818b-00ee-4b3a-9076-54d404a803f7" />

## RESULT

The implement of Vigenere Cipher substitution technique using C program is successful.
