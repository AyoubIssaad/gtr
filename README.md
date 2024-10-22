# gtr (Go To Root)

`gtr` is a command-line tool that helps you quickly navigate to your project's root directory by detecting common project files and structures.

## Features

- 🚀 One-command installation
- 🔍 Smart project root detection
- 🛠️ Interactive setup process
- 🔄 Safe updates (no duplicate wrappers)
- 💻 Support for bash, zsh, and fish shells
- 📁 Extensive project type support

## Installation

```bash
go install github.com/yourusername/gtr@latest
```

After installation, simply run `gtr` once, and it will guide you through the setup process:

1. Automatically detects your shell (bash, zsh, or fish)
2. Offers to install the necessary shell wrapper
3. Sets everything up with your confirmation

## Usage

Navigate to any project's root directory from any subdirectory:

```bash
$ pwd
/home/user/projects/myapp/src/components/utils
$ gtr
$ pwd
/home/user/projects/myapp
```

### Options

- `--path-only`: Only output the project root path without changing directory
- `--version`: Show version information

## Project Detection

gtr identifies project roots using various indicators:

### Common Files

- Version Control: `.git`, `.svn`, `.hg`
- Documentation: `README.md`, `LICENSE`
- Package Managers: `package.json`, `go.mod`, `Cargo.toml`
- Configuration: `.env`, `docker-compose.yml`, `Makefile`
- And many more...

### Common Directories

- Source Code: `src`, `lib`, `pkg`
- Documentation: `docs`, `wiki`
- Testing: `tests`, `spec`
- And others...

## Manual Setup

If you prefer manual setup, add the following to your shell configuration:

### Bash/Zsh

Add to `~/.bashrc` or `~/.zshrc`:

```bash
gtr() {
    local dir="$(command gtr --path-only)"
    [[ $? -eq 0 ]] && cd "$dir"
}
```

### Fish

Add to `~/.config/fish/config.fish`:

```fish
function gtr
    set -l dir (command gtr --path-only)
    if test $status -eq 0
        cd "$dir"
    end
end
```

## Development

### Testing Locally

```bash
# Clone the repository
git clone https://github.com/yourusername/gtr.git
cd gtr

# Build and install locally
go install .

# Test the command
gtr
```

## Contributing

Contributions are welcome! Feel free to:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.
