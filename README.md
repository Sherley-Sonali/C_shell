# Custom Shell Implementation

A feature-rich shell implementation in C that provides various Unix-like shell functionalities including process management, I/O redirection, and custom commands.

## Features

### Basic Shell Operations
- Custom shell prompt showing username, system name, and current directory
- Support for multiple commands using ';' separator
- Background process execution using '&'
- Error handling for invalid commands

### Built-in Commands

#### Directory Navigation
- `hop` - Change directory with support for:
  - Relative and absolute paths
  - Special symbols (., .., ~, -)
  - Multiple directory arguments
  - Displays full path after changing directory

#### File Operations
- `reveal` - List files and directories with:
  - Color coding (green for executables, white for files, blue for directories)
  - Support for -a (show hidden files) and -l (detailed listing) flags
  - Path symbols support (., .., ~, -)

#### Command History
- `log` - Command history management:
  - Stores up to 15 most recent commands
  - Persists across sessions
  - `log purge` - Clear history
  - `log execute <index>` - Execute command from history

#### Process Information
- `proclore` - Display process information:
  - PID
  - Process Status (R/R+/S/S+/Z)
  - Process Group
  - Virtual Memory
  - Executable Path

#### File Search
- `seek` - Search for files and directories:
  - `-d` flag for directories only
  - `-f` flag for files only
  - `-e` flag for direct interaction with single match
  - Support for target directory specification

### Advanced Features

#### Process Management
- Background process execution with PID display
- Process completion notification
- Time taken display for foreground processes (>2s)
- `activities` - List all running processes
- `ping` - Send signals to processes
- `fg`/`bg` - Foreground/Background process control

#### I/O Redirection and Pipes
- Support for input (`<`) and output (`>`, `>>`) redirection
- Multiple pipe (`|`) support
- Combined pipes and redirection

#### Signal Handling
- Ctrl+C (SIGINT) - Interrupt foreground process
- Ctrl+Z - Stop foreground process
- Ctrl+D - Shell exit

#### Configuration
- `.myshrc` support for aliases and custom functions
- Customizable shell environment

#### Networking
- `iMan` - Fetch man pages from the internet using sockets

## Installation

```bash
# Clone the repository
git clone <repository-url>

# Navigate to the project directory
# Run the makefile
make
```

## Usage Examples

```bash
# Change directory
<username@system:~> hop documents

# List files with details
<username@system:~/documents> reveal -l

# Search for files
<username@system:~> seek -f document ~/

# View command history
<username@system:~> log

# Check process information
<username@system:~> proclore 1234

# Redirect output
<username@system:~> echo "Hello" > output.txt

# Use pipes
<username@system:~> cat file.txt | grep "pattern"

# Fetch man pages
<username@system:~> iMan ls
```

## Error Handling
- Invalid command detection and reporting
- File/directory access permission checks
- Process management error handling
- I/O redirection error handling

## Technical Details
- Written in C
- Uses system calls for process management
- Socket programming for network features
- Signal handling implementation
- File descriptor management for I/O operations

## Limitations
- Aliases limited to single-word mappings
- Maximum command history of 15 entries

## Contributing
Feel free to submit issues and enhancement requests.
