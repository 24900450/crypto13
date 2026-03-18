# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

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
```c
#include <stdio.h>
#include <string.h>

int main()
{
    char msg[100], key[100];
    int i, mac = 0;

    printf("Enter message: ");
    scanf("%s", msg);

    printf("Enter key: ");
    scanf("%s", key);

    // Generate MAC
    for(i = 0; i < strlen(msg); i++)
    {
        mac = mac ^ msg[i] ^ key[i % strlen(key)];
    }

    printf("Generated MAC: %d\n", mac);

    // Verification
    int verify = 0;
    for(i = 0; i < strlen(msg); i++)
    {
        verify = verify ^ msg[i] ^ key[i % strlen(key)];
    }

    if(mac == verify)
        printf("Message is Authentic\n");
    else
        printf("Message is Tampered\n");

    return 0;
}
```
## Output:
<img width="666" height="292" alt="image" src="https://github.com/user-attachments/assets/4187f9d1-8cfc-4e7c-8cdc-fc0c563ba351" /><br>
## Result:
The program is executed successfully.
