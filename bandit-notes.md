# OverTheWire Bandit - Study Notes

Notes from the [OverTheWire Bandit](https://overthewire.org/wargames/bandit/) wargame, a beginner-friendly way to learn Linux and security fundamentals.

> Following the OverTheWire rules, this file contains **no passwords and no step-by-step solutions**. It only records the concepts I learned.

## Setup
- Environment: Windows 11 + WSL 2 (Ubuntu)
- Connection: SSH to the game server on port 2220
- Workflow: each level's password unlocks the next level

## Level 0 - Connecting with SSH
- `ssh user@host -p PORT` opens a remote shell on another machine.
- The password prompt does not echo characters, so typing errors are easy to miss.
- A remote server can refuse connections coming from itself. You have to `exit` first and connect from your own machine.
- `cat file` prints a file's content.

## Level 1 - Files with special names
- Some programs treat `-` as "read from keyboard" instead of a filename.
- Giving an explicit path (`./name`) makes the shell treat it as a real file.
- Lesson: when a command behaves strangely, check how it interprets its arguments.

## Level 2 - Spaces in filenames
- The shell splits arguments on spaces, so a name with spaces becomes several arguments.
- Quoting the name (or escaping spaces) keeps it as a single argument.
- Pressing `Tab` autocompletes names and avoids typing mistakes.

## Level 3 - Hidden files
- Files starting with `.` are hidden from a plain `ls`.
- `ls -a` lists all files, including hidden ones.
- Configuration and credential files are often hidden, so knowing how to find them matters in security work.

## Commands practiced so far
| Command | Purpose |
|---------|---------|
| `ssh` | Connect to a remote machine |
| `ls`, `ls -a` | List files (and hidden files) |
| `cd`, `pwd` | Move around and show the current directory |
| `cat` | Read a file |
| `exit` | Leave the current session |

## Cheat sheet
- [cat-cheatsheet.md](cat-cheatsheet.md): every way to write `cat` for different filenames.

## Habits I am building
- Try first, look things up after.
- Read the error message before changing anything.
- Never share passwords or tokens in notes, screenshots or repositories.

## Progress
- [x] Level 0
- [x] Level 1
- [x] Level 2
- [x] Level 3
- [ ] Level 4
