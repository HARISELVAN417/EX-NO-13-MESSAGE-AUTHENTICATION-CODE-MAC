# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC
## NAME : HARISELVAN S
## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:
```
#include <stdio.h>
#include <string.h>
int main() {
    char key[50], msg[50], mac[50];
    printf("Enter key: ");
    scanf("%s", key);
    printf("Enter message: ");
    scanf("%s", msg);
    int klen = strlen(key);
    int mlen = strlen(msg);
    for (int i = 0; i < mlen; i++) {
        mac[i] = msg[i] ^ key[i % klen];
    }
    mac[mlen] = '\0';
    printf("MAC: ");
    for (int i = 0; i < mlen; i++) {
        printf("%02x", (unsigned char)mac[i]);
    }
    return 0;
}
```
## Output:
<img width="1913" height="949" alt="image" src="https://github.com/user-attachments/assets/4f67add9-a2d9-41ea-9467-61df9b9495c9" />


## Result:
The program is executed successfully.
