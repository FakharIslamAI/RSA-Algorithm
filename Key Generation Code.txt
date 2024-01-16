#include <iostream>
#include <cmath>

// Function to check if two numbers are coprime (i.e., their GCD is 1)
bool isCoprime(int a, int b) {
	while (b != 0) {
		int temp = b;
		b = a % b;
		a = temp;
	}
	return a == 1;
}

// Function to calculate the modular inverse using Extended Euclidean Algorithm
int modInverse(int a, int m) {
	int m0 = m, t, q;
	int x0 = 0, x1 = 1;

	if (m == 1)
		return 0;

	while (a > 1) {
		// q is quotient
		q = a / m;
		t = m;

		// m is remainder now; process same as Euclid's algo
		m = a % m, a = t;

		t = x0;

		x0 = x1 - q * x0;

		x1 = t;
	}

	// Make x1 positive
	if (x1 < 0)
		x1 += m0;

	return x1;
}

int main() {
	// Given modulus 'n' for RSA cipher
	int n = 55;

	// Calculate pi(n) for n=55 (pi(n) is Euler's totient function for n)
	int pi_n = 0;
	for (int i = 1; i < n; i++) {
		if (isCoprime(i, n)) {
			pi_n++;
		}
	}

	// Find public key 'e' such that it is the smallest coprime to pi(n)'
	int e = 0;
	for (int i = 2; i < pi_n; i++) {
		if (isCoprime(i, pi_n)) {
			e = i;
			break;
		}
	}

	// Assuming sender and receiver have the same public and private keys
	int d = modInverse(e, pi_n);

	// Display the results
	std::cout << "Public key (e, n): (" << e << ", " << n << ")" << std::endl;
	std::cout << "Private key (d): " << d << std::endl;

	return 0;
}
