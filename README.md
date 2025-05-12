# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>

// Improved power function for modular exponentiation
long long int power(long long int a, long long int b, long long int P) {
    long long int res = 1;
    a = a % P;
    while (b > 0) {
        if (b & 1)
            res = (res * a) % P;
        a = (a * a) % P;
        b = b >> 1;
    }
    return res;
}

// Driver program
int main() {
    long long int P, G, x, a, y, b, ka, kb;

    // Both persons will agree upon the public keys G and P
    printf("\n***** Diffie-Hellman Key Exchange Algorithm *****\n\n");

    printf("Enter the value of P: ");
    scanf("%lld", &P); // A prime number P is taken
    printf("The value of P: %lld\n", P);

    printf("Enter the value of G (Primitive root of P): ");
    scanf("%lld", &G); // A primitive root for P, G is taken
    printf("The value of G: %lld\n\n", G);

    // Alice will choose the private key a
    a = 4; // a is the chosen private key
    printf("The private key a for Alice: %lld\n", a);
    x = power(G, a, P); // gets the generated key

    // Bob will choose the private key b
    b = 3; // b is the chosen private key
    printf("The private key b for Bob: %lld\n\n", b);
    y = power(G, b, P); // gets the generated key

    // Generating the secret key after the exchange of keys
    ka = power(y, a, P); // Secret key for Alice
    kb = power(x, b, P); // Secret key for Bob

    printf("Secret key for Alice is: %lld\n", ka);
    printf("Secret Key for Bob is: %lld\n", kb);

    return 0;
}
```


## Output:

![image](https://github.com/user-attachments/assets/57cf7c13-d725-4c9d-98bd-48be59705685)


## Result:
  The program is executed successfully

