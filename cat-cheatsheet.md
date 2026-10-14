# `cat` Cheat Sheet

Every way I need to write `cat`, depending on the filename. Examples use made-up filenames.

## 1. The basic rule
```
cat FILE
```
`cat` needs a **target**. Without one, it waits for keyboard input and looks frozen.
If that happens, press **Ctrl + C** to cancel.

## 2. Quick reference by filename type

| Filename looks like | How to write it | Why |
|---------------------|-----------------|-----|
| `notes.txt` (normal) | `cat notes.txt` | Nothing special |
| `-notes` (starts with `-`) | `cat ./-notes` | `-` at the start looks like an option; `./` marks it as a file |
| `-` (only a hyphen) | `cat ./-` | A lone `-` means "read the keyboard" |
| `my notes.txt` (has spaces) | `cat "my notes.txt"` | Quotes keep it as one argument |
| `my notes.txt` (has spaces) | `cat my\ notes.txt` | The backslash escapes each space |
| `--my notes--` (hyphens + spaces) | `cat "./--my notes--"` | Needs both: `./` and quotes |
| `.hidden` (starts with `.`) | `cat .hidden` | Works like any file, but `ls` hides it. Use `ls -a` to see it |
| `...weird` (many dots) | `cat ./...weird` | Same as hidden files; `./` is optional but safe |
| File in another folder | `cat folder/notes.txt` | Give the path |
| File with absolute path | `cat /home/user/notes.txt` | Full path from the root `/` |
| File in parent folder | `cat ../notes.txt` | `..` means one folder up |

## 3. Safe habits
- Start the path with `./` when the name looks strange. It almost never hurts.
- Press `Tab` after `cat ./` to autocomplete the real name. Press `Tab` twice to list the options.
- Run `ls -a` first to see the exact name, including hidden files.
- Copy the name from `ls` instead of retyping it.

## 4. Another way to stop `-` from being an option
```
cat -- -notes
```
`--` means "everything after this is a filename, not an option".

## 5. Reading several files
```
cat a.txt b.txt          # shows both, one after the other
cat ./*                  # every file in the current folder (careful with binary files)
```

## 6. Useful options
| Command | What it does |
|---------|--------------|
| `cat -n notes.txt` | Show line numbers |
| `cat -A notes.txt` | Show hidden characters (tabs, line endings) |
| `head notes.txt` | First 10 lines only |
| `tail notes.txt` | Last 10 lines only |
| `less notes.txt` | Scroll through a long file (`q` to quit) |

## 7. Before using `cat`: check the file type
```
file ./*
```
Shows what each file really is (`ASCII text`, `data`, `ELF executable`, ...).
Use `cat` only on files reported as text.

## 8. Troubleshooting

| What I see | What it means | Fix |
|------------|---------------|-----|
| Terminal looks frozen | `cat` has no filename and is waiting for input | `Ctrl + C`, then add the filename |
| `invalid option -- 'x'` | The name starts with `-` and was read as an option | Use `./` before the name |
| `No such file or directory` | Wrong name, wrong folder or typo | Check with `ls -a` and `pwd` |
| `cat: a: No such file` + `cat: b: No such file` | Spaces split the name into two arguments | Use quotes around the whole name |
| `Is a directory` | I tried to `cat` a folder | Use `ls folder` instead |
| Screen full of strange symbols | I opened a binary file | Type `reset` and press Enter |
| `Permission denied` | I am not allowed to read this file | Check permissions with `ls -l` |

## 9. Same logic for other commands
The same tricks (`./`, quotes, `--`) work for `cp`, `mv`, `rm`, `ls`, `file` and more.
