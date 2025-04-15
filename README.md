# Solana-Setup-Hello-World-Deployment
## by Tamyzgazina Ulzhan(SE-2325) & Bassanova Nurgul(SE-2323)

This assignment demonstrates:
1. Successful installation of Solana toolchain
2. Development and deployment of a Rust program on Solana

## Documentation Followed
- Installation: [https://solana.com/docs/intro/installation](https://solana.com/docs/intro/installation)
- Rust Program Development: [https://solana.com/ru/docs/programs/rust#update-the-program](https://solana.com/ru/docs/programs/rust#update-the-program)


## Part 1: Solana Installation
### Quick Installation
Run this single command to install all dependencies (due to the that we have used Ubuntu terminal):
```bash
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```
![Installation Step 1](screens/1.png) 

### Install Rust 
Install Rust with rustup. Run the following command to install Rust:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
```
![Installation Step 2](screens/2.png) 
![Installation Step 3](screens/3.png) 

### Install Anchor CLI
Anchor is a framework for developing Solana programs. The Anchor framework leverages Rust macros to simplify the process of writing Solana programs.
Install AVM with the following command:
```bash
cargo install --git https://github.com/coral-xyz/anchor avm --force
```
![Installation Step 4](screens/4.png) 

### Solana CLI Basics
### Solana Config & Create Wallet
To send transactions using the Solana CLI, you need a Solana wallet funded with SOL.
To generate a keypair at the default Keypair Path, run the following command:
```bash
solana-keygen new
```
To view our wallet's address (public key), run:
```bash
solana address
```
![Installation Step 5](screens/5.png) 

### Anchor CLI Basics
### Initialize Project
![Installation Step 7](screens/7.png) 
### Build program
![Installation Step 8](screens/8.png) 
### Deploy program
![Installation Step 9](screens/9.png) 

## Part 2: Developing Programs in Rust
### Create a new Program
![Installation Step 10](screens/10.png) 
Cargo.toml file should look like the following:
![Installation Step 11](screens/11.png) 
Replaced the contents of src/lib.rs with the following code. 
![Installation Step 12](screens/12.png) 

### Build the Program
![Installation Step 13](screens/13.png) 

To view the program ID, run the following command in your terminal. This command prints the public key of the keypair at the specified file path:
![Installation Step 14](screens/14.png) 

### Test the Program
![Installation Step 15](screens/15.png) 

Add the following test to src/lib.rs, below the program code. This is a test module that invokes the hello world program.
![Installation Step 16](screens/16.png)

 ### Deploy the Program
 First, configure the Solana CLI to use the local Solana cluster.
```bash
solana config set -ul
```
![Installation Step 18](screens/18.png)

Open a new terminal and run the solana-test-validators command to start the local validator.
```bash
solana-test-validator
```
While the test validator is running, run the solana program deploy command in a separate terminal to deploy the program to the local validator.
```bash
solana program deploy ./target/deploy/hello_world.so
```
![Installation Step 19](screens/19.png)

### Invoke the Program
First create an examples directory and a client.rs file.
![Installation Step 21](screens/21.png)

Add the following to Cargo.toml.
![Installation Step 20](screens/20.png)

Add the following code to examples/client.rs. This is a Rust client script that funds a new keypair to pay for transaction fees and then invokes the hello world program.
![Installation Step 22](screens/22.png)

Add the solana-client dependency.
![Installation Step 23](screens/23.png)

Run the client script with the following command.
```bash
cargo run --example client
```
![Installation Step 24](screens/24.png)

Test the updated program by running the cargo test-sbf command.
```bash
cargo test-sbf
```
![Installation Step 17](screens/17.png)

To close a program, use run the following command.
```bash
solana program close DaoRsAj2MJ4ehQukECn5g4NTDV3wbFoYZX8hErdMUBY7
--bypass-warning
```
![Installation Step 17](screens/25.png)

