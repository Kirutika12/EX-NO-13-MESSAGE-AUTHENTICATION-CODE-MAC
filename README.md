# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC
### NAME: KIRUTIKA K R
### REG NO: 212224230128

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
  
unsigned long simpleHash(char *str) 
{ 
    unsigned long hash = 5381; 
    int c; 
  
    while ((c = *str++)) 
        hash = ((hash << 5) + hash) + c; 
  
    return hash; 
} 
  
int main() 
{ 
    char key[100], message[500]; 
    char input[600]; 
    unsigned long mac, receivedMAC; 
  
    printf("Enter Secret Key: "); 
    scanf("%s", key); 
  
    getchar(); 
  
    printf("Enter Message: "); 
    fgets(message, sizeof(message), stdin); 
    message[strcspn(message, "\n")] = '\0'; 
    strcpy(input, key); 
    strcat(input, message); 
    mac = simpleHash(input); 
  
    printf("\nGenerated MAC: %lu\n", mac); 
    printf("\nEnter MAC for verification: "); 
    scanf("%lu", &receivedMAC); 
  
    if (mac == receivedMAC) 
    { 
        printf("\nMAC Verification Successful!\n"); 
        printf("Message is authentic and unchanged.\n"); 
    } 
    else 
    { 
        printf("\nMAC Verification Failed!\n"); 
        printf("Message is not authentic or has been modified.\n"); 
    } 
  
    return 0; 
}
```


## Output:
<img width="538" height="408" alt="image" src="https://github.com/user-attachments/assets/2712fa94-db7a-4576-b61b-65794e8bde5d" />


## Result:
The program is executed successfully.
