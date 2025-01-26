# Setting up a dev container for Go

* Primary author: [Dhyey Shah](https://github.com/dhyeyvshah)
* Reviewer: [Alexander Shang](https://github.com/alexander-shang)

---
## Prerequisites
Before starting this tutorial, ensure the following:

1. Create a [GitHub](https://github.com/) account.
2. Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).
3. Install [Visual Studio Code (VS Code)](https://code.visualstudio.com/download).
4. Install [Docker](https://www.docker.com/get-started/).

---
## Step 1: Create a Local Directory and Initialize Git

1. Open your terminal or command prompt.

2. Create a new directory for your project:

        mkdir go-hello-comp423
        cd go-hello-comp423

3. Initialize a new Git repository:

        git init

4. Add a README if you would like:

        echo "<your-readme.md-text>" > README.md
        git add README.md
        git commit -m "Initial commit with README"
Replace ```<your-readme.md-text>``` with your README markdown text.

## Step 2: Create a Remote Repository on GitHub
1. Log in to your GitHub account and navigate to the [Create a New Repository](https://github.com/new) page.

2. Add the GitHub repository as a remote:

        git remote add origin https://github.com/<your-username>/go-hello-comp423.git
Replace ```<your-username>``` with your GitHub username.

## Step 3: Set up a Development Container
1. Inside the project directory, create a ```.devcontainer``` folder and add a ```devcontainer.json``` file:

        mkdir .devcontainer
        touch .devcontainer/devcontainer.json

2. In VS Code, open the go-hello-comp423 directory. You can do this via: File > Open Folder.
3. Install the Dev Containers extension for VS Code.
4. Add the following configuration to your ```devcontainers.json``` file:

        {
            "name": "Go Dev Container",
            "image": "mcr.microsoft.com/devcontainers/go:latest",
            "features": {},
            "customizations": {
                "vscode": {
                    "extensions": ["golang.go"]
                }
            }
        }

    - ```name```: A descriptive name for your dev container.
    - ```image```: The base image from Microsoft with Go pre-installed.
    - ```customizations```: Adds useful configurations to VS Code, like installing the Go extension.

5. Reopen the project in the container by pressing ```Ctrl+Shift+P``` (or ```Cmd+Shift+P``` on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. 
6. Open the terminal in VS Code and run:

        go version
This verifies the Go version installed in the container.

## Step 4: Create a New Go Project
1. Run the following command to initialize the Go project:

        go mod init go-hello-comp423

2. Create a file named ```main.go```:

        touch main.go

3. Add the following content to ```main.go```:

        package main

        import "fmt"

        func main() {
            fmt.Printlin("Hello COMP423")
        }

## Step 5: Run the program
You have two options:

- Execute the program directly:

        go run main.go

- Compile the program into a binary:

        go build -o hello
        ./hello

!!! Note
    The ```go run``` command executes the source code directly, while the ```go build``` command
    compiles the code into an executable binary, which can be run without requiring Go at runtime
    (similar to gcc in that they both compile code into an executable).

---

Congratulations! You have successfully set up a dev container for Go!