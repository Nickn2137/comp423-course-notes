# **Setting up a dev container for Rust:**

* Primary author: [Nicholas Nguyen](https://github.com/Nickn2137)
* Reviewer: [Logan Gatza](https://github.com/lrgatza)

Welcome to this step-by-step guide for setting up a Rust project in a Dev Container! Hopefully by the end of this tutorial you'll have a fully functional Rust development environment and a simple Rust program!

## **Prerequisites**
---

!!! note "Required tools"
    Before we begin, make sure you have the following:
1. **Git installed:** [Install git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don't already have it.
- **Visual Studio Code(VS Code):** Download and install it from [here](https://code.visualstudio.com/).
- **Docker installed:** Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop). 
- **Command-line basics:** Basic knowledge of terminal commands and Git.

## **Set-Up Guide**
---

#### STEP 1. Create a Local Directory and Initialize Git

(A) Open your terminal or command prompt.

(B) Create a new directory for your project. (Note: Of course, if you'd like to organize this tutorial somewhere else on your machine, go ahead and change into that parent directory first. By default this will be in your user's home directory.):

``` bash
mkdir rust-hello
cd rust-hello
```
(C) Initialize a new Git repository:
``` bash
git init
```
#### STEP 2. Setting Up the Development Environment

(A) In VS Code, open the `rust-hello` directory. You can do this via: File > Open Folder.

(B) Install the **Dev Containers** extension for VS Code.

(C) Create a `.devcontainer` directory in the root of your project with the following file inside of this "hidden" configuration directory: `devcontainer/devcontainer.json`

* **`name`**: A descriptive name for your dev container.

* **`image`**: The Docker image to use. For this tutorial, we'll be using a base image of Rust from [Microsoft](https://hub.docker.com/r/microsoft/vscode-devcontainers).

* **`extensions`**: A list of Visual Studio Code extensions to install in the Dev Container. These extensions enhance your development experience. For Rust, we include the `rust-analyzer extension`, which provides powerful features like code completion, inline documentation, and real-time diagnostics.

* **`settings`**: VS Code-specific settings to customize your workspace. In this case, the `rust-analyzer.cargo.autoReload` setting is enabled, which ensures that the Rust Analyzer automatically reloads the Cargo workspace when files are added, removed, or updated.
``` json
{
  "name": "Rust Dev Container",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "extensions": [
    "rust-lang.rust-analyzer"
  ],
  "settings": {
    "rust-analyzer.cargo.autoReload": true
  }
}
```

!!! info "Why a Dev Container?" 
    Dev Containers provide a consistent, reproducible development environment, reducing setup time and dependency issues.

#### STEP 3. Build and Open the Dev Container

(A) Open the project in VS Code.

(B) Open the **Command Palette** (`Ctrl+Shift+P` or `Cmd+Shift+P`) and select `Dev Containers: Reopen in Container`.

(C) You can verify Rust is installed by running:
``` bash
rustc --version
```

!!! success "Expected Output"
    `plaintext rustc 1.x.x (or newer)`

## **Hello COMP423 Project**
---

#### STEP 4. Initialize a Rust Project

Use `cargo` to create a new binary project.

``` bash
cargo new hello-comp423 --vcs none
cd hello-comp423
```

!!! warning "Avoid Git Reinitialization"
    The `--vcs none` flag prevents `cargo` from creating a new Git repository since you already initialized one earlier."

#### STEP 5. Writing the Program
Edit the `src/main.rs` file to print "Hello COMP423" to the terminal:
``` rust
fn main() {
    println!("Hello COMP423");
}
```

#### STEP 6. Build and Run the Program
(A) Run the following command to compile the Rust program:
``` bash
cargo build
```
!!! note "Where's the binary?"
    The compiled binary is located in the `target/debug` directory. To run it manually, execute: `./target/debug/hello-comp423`

(B) Instead of building and running separately, we can use the `cargo run` command to run the program directly.

``` bash
cargo run
```
!!! info "What's the difference between build and run?"
    - cargo build: Compiles the project without running it.
    - cargo run: Builds the project (if necessary) and immediately runs the resulting binary.

## **Final Words**
---

Congratulations! 🎉 You've successfully set up a Rust development environment in a Dev Container and created a program that prints "Hello COMP423." You now have the foundation to build and explore more Rust projects.

!!! tip "Next Steps" 
    - Experiment with Rust features like modules, traits, and ownership. - Try using cargo test to write and run unit tests.

### Sources

- [423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/#understanding-your-cicd-workflow)
- [Rust Documentation](https://doc.rust-lang.org/rust-by-example/hello.html)
