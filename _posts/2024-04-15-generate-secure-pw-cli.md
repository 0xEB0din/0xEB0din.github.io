## Generate Secure Passwords from the CLI with `pwgen`

Securing your online presence with strong, unique passwords is essential. If you spend a lot of time in the terminal, `pwgen` is a great tool for generating secure passwords directly from the command line. Here’s a quick guide for macOS and Linux users, along with a handy CLI shortcut.

### Installing `pwgen`

#### macOS

Install `pwgen` using Homebrew:

```bash
brew install pwgen
```

#### Linux

Install `pwgen` using your package manager:

**Debian/Ubuntu:**
```bash
sudo apt-get install pwgen
```

**Fedora:**
```bash
sudo dnf install pwgen
```

### Basic Usage

Generate a secure password:

```bash
pwgen -s 16 1
```

- `-s`: Secure passwords.
- `16`: Password length.
- `1`: Number of passwords.

### Enhanced Security

Include special characters and avoid ambiguous ones:

```bash
pwgen -s -y -B 16 1
```

- `-y`: Include special characters.
- `-B`: Avoid ambiguous characters.

### Creating a CLI Shortcut

To make password generation even easier, create a function that generates a password, copies it to the clipboard, and displays a message.

#### macOS

Add this to your shell configuration file (e.g., `.bashrc`, `.zshrc`):

```bash
genpasswd() {
  pwgen -s -y -B ${1:-16} 1 | tee >(pbcopy) | sed 's/.*/Mission success. Password locked and loaded!/'
}
```

#### Linux

Install `xclip`:

```bash
sudo apt-get install xclip
```

Add this to your shell configuration file:

```bash
genpasswd() {
  pwgen -s -y -B ${1:-16} 1 | tee >(xclip -selection clipboard) | sed 's/.*/Mission success. Password locked and loaded!/'
}
```

### Usage

Reload your shell configuration:

```bash
source ~/.bashrc  # or source ~/.zshrc
```

Generate and copy a password:

```bash
genpasswd 20  # Generates a 20-character password
genpasswd     # Generates a default 16-character password
```

Output:

```plaintext
Mission success. Password locked and loaded!
```

### Conclusion

Using `pwgen` and a simple CLI shortcut, you can quickly generate and copy secure passwords. This setup ensures strong passwords are always just a command away. Stay secure!

Happy password generating! 💻🔐