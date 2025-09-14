# Install-go-language-in-kali
To install the Go programming language on Kali Linux, follow these steps:

1. **Update the System**:
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Download the Go Binary**:
   Visit the official Go website (https://go.dev/dl/) to find the latest version. For example, to download Go 1.21.5 (replace with the latest version if needed):
   ```bash
   wget https://go.dev/dl/go1.21.5.linux-amd64.tar.gz
   ```

3. **Extract the Archive**:
   Extract the downloaded tarball to `/usr/local`:
   ```bash
   sudo tar -C /usr/local -xzf go1.21.5.linux-amd64.tar.gz
   ```

4. **Set Up Environment Variables**:
   Edit your shell configuration file (e.g., `~/.bashrc` or `~/.zshrc` if using Zsh) to add Go to your PATH:
   ```bash
   nano ~/.bashrc
   ```
   Add the following lines at the end of the file:
   ```bash
   export PATH=$PATH:/usr/local/go/bin
   export GOPATH=$HOME/go
   export PATH=$PATH:$GOPATH/bin
   ```
   Save and exit, then apply the changes:
   ```bash
   source ~/.bashrc
   ```

5. **Verify Installation**:
   Check the Go version to confirm installation:
   ```bash
   go version
   ```
   You should see output like `go version go1.21.5 linux/amd64`.

6. **Create Go Workspace** (optional):
   Create a directory for your Go projects:
   ```bash
   mkdir -p $HOME/go/{bin,src,pkg}
   ```

7. **Test Go**:
   Create a simple Go program to test:
   ```bash
   nano $HOME/go/src/hello.go
   ```
   Add the following code:
   ```go
   package main
   import "fmt"
   func main() {
       fmt.Println("Hello, Kali!")
   }
 
### Why it happens

* `~/.bashrc` is written for **Bash**.
* If your current shell is **not Bash**, commands like `shopt` won’t exist.

---

### ✅ How to fix

1. **Check your current shell:**

   ```bash
   echo $SHELL
   ```

   If it prints `/bin/sh` or `/bin/dash`, that explains the error.

2. **Switch to Bash temporarily:**

   ```bash
   bash
   ```

   Then run:

   ```bash
   source ~/.bashrc
   ```

3. **Make Bash your default shell (if you want):**

   ```bash
   chsh -s /bin/bash
   ```

   (Log out and back in after this.)

---

### Extra

If you’re actually using **Zsh** (common in Kali and modern distros), you should put your configs in `~/.zshrc` instead of `~/.bashrc`.

---

👉 Do you want me to show you how to **move your `.bashrc` settings into `.zshrc`** so they work without switching shells?

   Run the program:
   ```bash
   go run $HOME/go/src/hello.go
   ```
   You should see `Hello, Kali!` as output.


