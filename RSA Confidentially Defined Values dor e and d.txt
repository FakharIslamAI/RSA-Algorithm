#include <iostream>
#include <cmath>

// Function to calculate the modular exponentiation (a^b % m) efficiently
int powerMod(int a, int b, int m) {
	int result = 1;
	a = a % m;

	while (b > 0) {
		if (b & 1)
			result = (result * a) % m;

		b = b >> 1;
		a = (a * a) % m;
	}

	return result;
}

int main() {
	char alphabet[26] = { 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm',
						 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z' };

	// Given public and private keys for RSA
	int e = 3; // Public key (e, n)
	int d = 27; // Private key (d)
	int n = 55; // Modulus (n)

	// Input the plaintext letter (single letter)
	char plaintext;
	std::cout << "Enter a single letter as plaintext: ";
	std::cin >> plaintext;

	// Find the value of the plaintext letter using the alphabet array
	int plaintextValue = -1;
	for (int i = 0; i < 26; i++) {
		if (alphabet[i] == plaintext) {
			plaintextValue = i;
			break;
		}
	}

	if (plaintextValue == -1) {
		std::cout << "Invalid input. Please enter a valid letter." << std::endl;
		return 1;
	}

	// Encryption: C = P^e (mod n)
	int ciphertext = powerMod(plaintextValue, e, n);

	// Decryption: P = C^d (mod n)
	int decryptedValue = powerMod(ciphertext, d, n);

	// Check if the decryption is valid
	if (decryptedValue >= 0 && decryptedValue < 26) {
		char decryptedLetter = alphabet[decryptedValue];
		std::cout << "Encrypted ciphertext (C): " << ciphertext << std::endl;
		std::cout << "Decrypted plaintext (P): " << decryptedLetter << std::endl;
	}
	else {
		std::cout << "Decryption failed. Please check the keys and input." << std::endl;
	}

	return 0;
}
