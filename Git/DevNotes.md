# Development Notes

## Git Bash Default Directory Setup Memo

### Objective
This memo outlines how to set `D:/DATA/10.CLD/GitHub` as the default directory in Git Bash, ensuring that each session starts in this specified directory.

### Steps to Configure Git Bash

1. **Open Git Bash**:
   - Launch Git Bash from your Start menu or desktop shortcut.

2. **Edit `.bashrc`**:
   - Open the `.bashrc` file located in your user directory (`~`). If the file does not exist, you can create it:
     ```bash
     nano ~/.bashrc
     ```
   - Add the following line to set the default directory:
     ```bash
     cd /d/DATA/10.CLD/GitHub
     ```
   - Save the changes and exit nano (Ctrl+O, Enter to save and Ctrl+X to exit).

3. **Edit `.bash_profile`**:
   - Ensure `.bashrc` is sourced at login and set the default directory by opening or creating `.bash_profile`:
     ```bash
     nano ~/.bash_profile
     ```
   - Add these lines to ensure both profile and rc files are loaded, and the directory change persists:
     ```bash
     test -f ~/.profile && . ~/.profile
     test -f ~/.bashrc && . ~/.bashrc
     ```
   - Save and exit using Ctrl+O, Enter and Ctrl+X.

4. **Reload the Profile**:
   - To apply the changes immediately, especially if you are in an active session:
     ```bash
     source ~/.bash_profile
     ```

### Conclusion

Following these steps configures Git Bash to start in `D:/DATA/10.CLD/GitHub` automatically, streamlining your workflow by avoiding the need to manually navigate to this directory each time you open Git Bash.
