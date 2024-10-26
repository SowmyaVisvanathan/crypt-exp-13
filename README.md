#### Name : Sowmya V
#### Reg no : 212222110045
#### Date : 

## EX - 13 : Implement Message Authentication Code (MAC)

### Aim:
To implement the Message Authentication Code (MAC) algorithm in C.

### Algorithm:

Step 1:
Select a secret key K for the MAC algorithm.

Step 2:
Take the input message M from the user.

Step 3:
Combine the message M with the secret key K.

Step 4:
Generate a MAC by hashing the combined data (using a simple hash function like XOR or a more secure function like SHA).

Step 5:
Verify the MAC by recomputing it using the same method and comparing it with the transmitted MAC.

### Program:
```
#include <stdio.h>
#include <string.h>

unsigned int simpleHash(char *data, int length)
{
    unsigned int hash = 0;
    for (int i = 0; i < length; i++)
    {
        hash ^= data[i];  
    }
    return hash;
}

unsigned int generateMAC(char *message, char *key)
{
    char combined[256];  
    strcpy(combined, key);  
    strcat(combined, message);  
    return simpleHash(combined, strlen(combined));
}

int main()
{
    char message[128];
    char key[128];
    
    printf("Enter the secret key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = 0;  
    
    printf("Enter the message: ");
    fgets(message, sizeof(message), stdin);
    message[strcspn(message, "\n")] = 0; 

    unsigned int mac = generateMAC(message, key);
    printf("Generated MAC: %u\n", mac);
    char verify_message[128];
    char verify_key[128];
    
    printf("\n--- Verification ---\n");
    printf("Enter the message for verification: ");
    fgets(verify_message, sizeof(verify_message), stdin);
    verify_message[strcspn(verify_message, "\n")] = 0;  
    
    printf("Enter the secret key for verification: ");
    fgets(verify_key, sizeof(verify_key), stdin);
    verify_key[strcspn(verify_key, "\n")] = 0;  
    unsigned int verify_mac = generateMAC(verify_message, verify_key);
    if (mac == verify_mac)
    {
        printf("Verification successful! MACs match.\n");
    }
    else
    {
        printf("Verification failed! MACs do not match.\n");
    }
    
    return 0;
}
```
### Output

![image](https://github.com/user-attachments/assets/04a5e199-de0d-4d27-afa2-9780b89bceb1)

### Result
The Message Authentication Code (MAC) algorithm has been successfully implemented in C.
