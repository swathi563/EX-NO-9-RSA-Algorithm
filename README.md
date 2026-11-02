# EX-NO-9-RSA-Algorithm

## AIM:
To Implement RSA Encryption Algorithm in Cryptography

## Algorithm:


Step 1: Design of RSA Algorithm  
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

Step 2: Implementation in Python or C 
This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

Step 3: Algorithm Description  
1. Key Generation:
   - Select two large prime numbers \( p \) and \( q \).
   - Calculate \( n = p \times q \), which will be used as the modulus.
   - Compute the totient \( \phi(n) = (p - 1)(q - 1) \).
   - Choose a public exponent \( e \) such that \( e \) is coprime with \( \phi(n) \).
   - Compute the private key \( d \), which is the modular inverse of \( e \) mod \( \phi(n) \).

2. Encryption:
   - Convert the plaintext message \( M \) into a numerical form \( m \) (such that \( 0 \le m < n \)).
   - Compute the ciphertext \( c \) using the formula: \( c = m^e \mod n \).

3. Decryption:
   - Use the private key \( d \) to recover \( m \) from \( c \) using: \( m = c^d \mod n \).
   - Convert \( m \) back into the original message \( M \).

Step 4: Mathematical Representation  
- Encryption: \( E(m) = m^e \mod n \)
- Decryption: \( D(c) = c^d \mod n \)

Step 5: **Security Foundation  
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for \( p \) and \( q \) is crucial for security.

## Program:
```
#include <stdio.h>

// Function to calculate modular exponentiation
long long modPower(long long base, long long exp, long long mod)
{
    long long result = 1;

    while (exp > 0)
    {
        if (exp % 2 == 1)
            result = (result * base) % mod;

        base = (base * base) % mod;
        exp = exp / 2;
    }

    return result;
}

int main()
{
    long long p = 61, q = 53;
    long long n, phi;
    long long e = 17, d = 2753;
    long long message, cipher, decrypted;

    // Key Generation
    n = p * q;
    phi = (p - 1) * (q - 1);

    printf("Public Key: (%lld, %lld)\n", e, n);
    printf("Private Key: (%lld, %lld)\n", d, n);

    // Encryption
    printf("Enter message (number less than %lld): ", n);
    scanf("%lld", &message);

    if (message < 0 || message >= n)
    {
        printf("Invalid message!\n");
        return 1;
    }

    cipher = modPower(message, e, n);

    printf("Original Message: %lld\n", message);
    printf("Encrypted Message: %lld\n", cipher);

    // Decryption
    decrypted = modPower(cipher, d, n);

    printf("Decrypted Message: %lld\n", decrypted);

    return 0;
}
```
## Output:

Public Key: (17, 3233)
Private Key: (2753, 3233)
Enter message (number less than 3233): 1234
Original Message: 1234
Encrypted Message: 2183
Decrypted Message: 1234

<img width="672" height="240" alt="image" src="https://github.com/user-attachments/assets/82ecb074-1daa-413e-9453-4cbe28814e1c" />

## Result:
The program is executed successfully.


## Result:
 The program is executed successfully.
