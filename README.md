

OpenBooks App Documentation

Introduction

OpenBooks is a peer-to-peer book sharing network that allows users to rent books from each other using a secure escrow mechanism. This documentation covers the deployment and usage of the escrow smart contract developed in Rust and the API built with NestJS.

Smart Contract

Requirements

Rust: Ensure Rust is installed on your system. You can install Rust from the [official website](https://www.rust-lang.org/tools/install).
Truffle Suite: For compiling and deploying the smart contract, [Truffle Suite](https://www.trufflesuite.com/) is recommended.

Smart Contract Deployment

Compilation
1. Navigate to your project directory.
2. Compile the smart contract using Truffle:
   ```bash
   truffle compile
   ```

Deployment
1. Configure the `truffle-config.js` to include your Ethereum network details and private keys.
2. Deploy the contract to Ethereum network:
   ```bash
   truffle migrate --network rinkeby
   ```

    Function Details

- add_book
  - Purpose: Registers a new book with its daily rental rate.
  - Parameters:
    - `id` (String): A unique identifier for the book.
    - `daily_rate` (u64): The daily rental price in wei.
  -   Returns: None.

-  rent_book
  -  Purpose: Initiates a rental transaction.
  -  Parameters:
    - `id` (String): The unique identifier of the book to rent.
    - `days` (u32): Number of days the book is rented for.
  - Returns: `bool`: True if transaction is successful.

- complete_rental
  - Purpose: Completes a rental transaction and releases funds from escrow.
  - Parameters:
    - `id` (String): The unique identifier of the book.
  - Returns: `bool`: True if transaction is successful.

   API

    Setup

1.  Installation
   - Clone the repository and navigate into the directory:
     ```bash
     git clone <repository-url>
     cd <repository-name>
     ```
   - Install dependencies:
     ```bash
     npm install
     ```

2.   Running the Server
   - Start the development server:
     ```bash
     npm run start:dev
     ```

     API Endpoints

-   POST /api/books/add
  -   Description: Adds a new book to the blockchain.
  -   Request Body:
    ```json
    {
      "id": "book123",
      "daily_rate": 1000
    }
    ```
  -   Response:
    ```json
    {
      "success": true,
      "message": "Book added successfully."
    }
    ```

-   POST /api/books/rent
  -   Description: Initiates a book rental.
  -   Request Body:
    ```json
    {
      "id": "book123",
      "days": 5
    }
    ```
  -   Response:
    ```json
    {
      "success": true,
      "message": "Rental initiated successfully."
    }
    ```

-   POST /api/books/complete
  -   Description: Completes the book rental.
  -   Request Body:
    ```json
    {
      "id": "book123"
    }
    ```
  -   Response:
    ```json
    {
      "success": true,
      "message": "Rental completed successfully."
    }
    ```

   Testing

-   Unit Tests for Smart Contract
  - Use `pwasm-test` for testing the functions of the smart contract.
  - Tests should cover all possible input scenarios and validate output and state changes.

-   Integration Tests for API
  - Use Jest with Supertest to simulate API requests and responses.
  - Ensure that the API interacts correctly with the smart contract, handling errors gracefully.

   Security

-   Smart Contract: Analyze with tools like MythX to detect vulnerabilities.
-   API: Implement standard security measures including validation, authentication, and HTTPS encryption.

This comprehensive documentation should guide developers through setting up, deploying, and using the OpenBooks smart contract and APIs effectively.
