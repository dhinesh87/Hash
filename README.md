### Date:
# Ex-14:Hash
## AIM:
To implement a simple hash generation and verification process using a custom hash function based on XOR and addition.

## ALGORITHM:

### STEP 1:
Input a message from the user.

### STEP 2:
Use a basic custom hash function that applies XOR and addition on each character of the message.

### STEP 3:
Convert the resulting hash into a hexadecimal format.

### STEP 5:
Verify the hash by comparing it with a received hash entered by the user.
## Program:
```
#include <stdio.h>
#include <string.h>

// Function to compute a simple hash using XOR and addition
unsigned char compute_simple_hash(const char *message) {
    int temp = 0;

    // Simple hash computation: XOR and addition
    for (int i = 0; i < strlen(message); i++) {
        temp = temp ^ message[i];  // XOR each character
        temp += message[i];        // Add each character's value
    }

    // Return the result as a 1-byte hash
    return temp & 0xFF;  // Ensure the hash is within a byte (0-255)
}

int main() {
    char message[256];
    char received_hash_hex[3];  // Store the 2-digit hex hash
    unsigned char hash_value, received_hash_value;

    // Step 1: Input the message
    printf("Enter the message: ");
    fgets(message, sizeof(message), stdin);
    message[strcspn(message, "\n")] = 0;  // Remove trailing newline

    // Step 2: Compute the simple hash
    hash_value = compute_simple_hash(message);

    // Step 3: Display the computed hash in hexadecimal format
    printf("Computed Hash (in hex): %02x\n", hash_value);

    // Step 5: Verify the hash
    printf("Enter the received hash (in hex): ");
    fgets(received_hash_hex, sizeof(received_hash_hex), stdin);
    received_hash_hex[strcspn(received_hash_hex, "\n")] = 0;  // Remove trailing newline

    // Convert received hash from hex string to an integer
    sscanf(received_hash_hex, "%2hhx", &received_hash_value);

    // Compare the computed hash with the received hash
    if (hash_value == received_hash_value) {
        printf("Hash verification successful. Message is unchanged.\n");
    } else {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0;
}

```
## Output:

![Screenshot 2024-10-19 103541](https://github.com/user-attachments/assets/ea70bc35-2792-45d7-bb4d-05176dd39d37)


## Result:
The program for generating and verifying a simple hash using a custom hash function was successfully implemented and executed. The computed hash ensures basic message integrity and was successfully verified against the received hash.
