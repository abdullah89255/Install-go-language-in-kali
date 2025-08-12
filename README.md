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
   ```
   Run the program:
   ```bash
   go run $HOME/go/src/hello.go
   ```
   You should see `Hello, Kali!` as output.

**Notes**:
- Ensure you have `wget` installed (`sudo apt install wget`).
- If you prefer, you can install Go via `apt` using `sudo apt install golang`, but this may provide an older version.
- For the latest version, always download from the official site.
- If you encounter permission issues, ensure you have appropriate sudo privileges.

For further details, check the official Go documentation at https://go.dev/doc/install.
