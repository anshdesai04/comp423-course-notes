# Setting up a dev container for Rust

* Primary author: [Ansh Desai](https://github.com/anshdesai04)
* Reviewer: [Sujay Patel](https://github.com/SUJP123)

## **Intro**
This is a guide for setting up a Rust project with a Git repository and a dev container, and produce a "Hello COMP423!" program.

## **Prerequisites**
Before starting, ensure you have the following installed:

- [Visual Studio Code](https://code.visualstudio.com/) as well as the **Remote – Containers** extension
- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)

## **Step-by-step instructions for creating a new Dev Container project for Rust**

---

### **Step 1**
Open your terminal and create a directory for your Rust project:
```bash
mkdir rust-hello-world
cd rust-hello-world
```
### **Step 2**
Initialize a new Git repository:
```bash
git init
```
### **Step 3**
Create a new public repository on GitHub and copy its URL. Then, link it to your local project:
```bash
git remote add origin https://github.com/<your-username>/rust-hello-world.git
```

Replace `<your-username>` with your GitHub username.

### **Step 4**
Set up a Dev Container configuration for your project:

1. Create a `.devcontainer` folder and a `devcontainer.json` file:
   ```bash
   mkdir .devcontainer
   touch .devcontainer/devcontainer.json
   ```

2. Open the `devcontainer.json` file in your editor and add the following configuration:
   ```json
   {
     "name": "Rust Dev Container",
     "image": "mcr.microsoft.com/vscode/devcontainers/base:ubuntu",
     "features": {
       "ghcr.io/devcontainers/features/rust": {}
     },
     "customizations": {
       "vscode": {
         "extensions": ["rust-lang.rust-analyzer"]
       }
     }
   }
   ```

3. Save the file and reopen the project in the container by pressing `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac), typing "Dev Containers: Reopen in Container," and selecting the option.

### **Step 5**
Verify that Rust is installed and working inside the Dev Container:

1. Open a terminal in VS Code (inside the container) and run:
   ```bash
   rustc --version
   ```

2. You should see output similar to the following:
   ```
   rustc 1.x.x (some-hash YYYY-MM-DD)
   ```

This confirms that Rust is installed and ready to use in your Dev Container.

Here’s how we can start with **Step 1** under your new section:

## **Steps to create a new project, write a basic "Hello COMP423" program, compile, and run**

### **Step 1**
Create a new Rust project using Cargo:

1. Run the following command to initialize a new Cargo project:
   ```bash
   cargo new hello-comp423 --vcs none
   ```

   This creates a new folder called `hello-comp423` with the default structure for a Rust project.

2. Navigate into the project directory:
   ```bash
   cd hello-comp423
   ```

3. Verify the folder structure. You should see:
   ```
   hello-comp423/
   ├── Cargo.toml
   └── src/
       └── main.rs
   ```

The `Cargo.toml` file contains metadata about the project, and `src/main.rs` is where you’ll write your program.

### **Step 2**
Write the "Hello, COMP423!" program:

1. Open the `src/main.rs` file in your project directory. Replace its contents with the following code:
   ```
   fn main() {
       println!("Hello COMP423!");
   }
   ```

2. Save the file.

This is your basic Rust program, which prints "Hello, COMP423!" to the console when executed.

### **Step 3**
Compile and run the program:

1. To compile the program, run:
   ```bash
   cargo build
   ```

2. To execute the compiled program, run:
   ```bash
   ./target/debug/hello-comp423
   ```

   You should see the output:
   ```text
   Hello COMP423!
   ```

Alternatively, you can compile and run the program in one step using:
   ```bash
   cargo run
   ```

   This will both build the program and immediately execute it, showing the output:
   ```text
   Hello COMP423!
   ```

!!! note
    - **`cargo build`**: This command compiles the program and generates an executable file in the `target/debug` directory. It’s useful when you want to inspect or reuse the binary later without immediately running the program.
    - **`cargo run`**: This command combines building and executing the program in a single step, which is convenient for quick testing during development.


### **Step 4**

1. Stage files, and add a README:
   ```bash
   echo "https://anshdesai04.github.io/comp423-course-notes/tutorials/rust-setup/" > README.md
   git add .
   ```

2. Add configs and commit:
   ```bash
   git config user.name --global "your-username-here"
   git config user.email --global "your-email-here"
   git commit -m "your-message-here"
   ```

3. Push to remote:
   ```bash
   git branch -M main
   git push --set-upstream origin main
   ```

## **Congrats you have finished!** :smile: