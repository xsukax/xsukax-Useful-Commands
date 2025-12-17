# xsukax Useful Linux Commands

This command lists all subdirectories in the current directory in a clean, readable, and numbered format, making it easier to quickly see and reference folder names. It works by scanning only the current directory level (without going into subfolders), selecting directories only, and excluding the special entry that represents the current directory itself. The output is then cleaned to remove the technical path prefix so that only the folder names remain, and finally each directory is automatically numbered in order with consistent formatting. Overall, the command is useful for organizing, reviewing, or documenting directory structures in a simple and beginner-friendly way while keeping the output neat and human-readable.

`find . -maxdepth 1 -type d ! -name '.' | sed 's|^\./||' | nl -w2 -s'. '`

---
