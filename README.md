# RSA Algorithm Implementation

This repository contains a C++ implementation of the RSA algorithm. The RSA algorithm is a widely-used public-key cryptosystem for secure data transmission and digital signatures.

## Table of Contents

- [Features](#features)
- [How to Use](#how-to-use)
- [Key Generation](#key-generation)
- [Encryption](#encryption)
- [Decryption](#decryption)
- [Contributing](#contributing)
- [License](#license)

## Features

- Key generation for RSA algorithm.
- Encryption of plaintext messages.
- Decryption of ciphertext messages.
- Digital signature using the RSA algorithm.

## How to Use

1. **Clone the Repository:**

    ```bash
    git clone https://github.com/FakharIslamAI/RSA-Algorithm.git
    ```

2. **Navigate to the Project:**

    ```bash
    cd RSA-Algorithm
    ```

3. **Compile the Code:**

    ```bash
    g++ -o rsa_algorithm main.cpp
    ```

4. **Run the Program:**

    ```bash
    ./rsa_algorithm
    ```

## Key Generation

The RSA key pair (public key and private key) is generated automatically during the execution of the program. The public key is used for encryption, while the private key is used for decryption.

## Encryption

To encrypt a plaintext message, the program uses the public key to generate the ciphertext.

## Decryption

To decrypt a ciphertext message, the program uses the private key to recover the original plaintext.

## Contributing

If you would like to contribute to this project, feel free to open issues or submit pull requests. Your contributions are welcome!

## License

This project is licensed under the [MIT License](LICENSE).
