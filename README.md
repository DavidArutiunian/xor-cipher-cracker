# xor-cipher-cracker
An attack on the repeating key XOR Cipher. The script attempts to decipher a piece of ciphertext encrypted using the XOR Cipher with a repeating key.

## Example Usage
example.py shows an example of using the XorCipherCracker class to decrypt the hex contained within cipher-text.txt.

### Running example.py

`python example.py cipher-text.txt`

## Methodology
The program works by running through a range of key lengths, slicing out sequential sections of the ciphertext equal in length to each one. The Hamming Distance of each two section grouping of the text is then computed. The average Hamming distance for all sections of the ciphertext for each key length are found, and normalised by division by the key length. The smaller the resulting average hamming distance, the more likely a key length is to be correct.

The key space for keys of length n, where n is the most likely key length, is then generated. Each possible key is then XORed with each n-length block of ciphertext, before checking the resulting ASCII value matches one of a list of ‘legal’ characters (`’abcdefghijklmnopqrstuvwxyz .,-\’?_()!’`). The list of keys that produce only legal characters as the plaintext are then used to fully decrypt the ciphertext, which the program then returns with the corresponding keys.
