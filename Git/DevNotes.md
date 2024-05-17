# Development Notes

## Git Bash Default Directory Setup Memo

### Steps to Set Default Directory in Git Bash

1. **Open Git Bash**.
2. **Open `~/.bash_profile` with nano** :
    ```bash
    nano ~/.bash_profile
    ```
3. **Add the following lines if not present** :
    ```bash
    test -f ~/.profile && . ~/.profile
    test -f ~/.bashrc && . ~/.bashrc
    ```
4. **Add the line to change the default directory** :
    ```bash
    cd /d/DATA/10.CLD/GitHub
    ```
5. **Save and exit nano** :
    - **Save** : Ctrl+O, Enter
    - **Exit** : Ctrl+X
6. **Reload the profile** to apply changes immediately :
    ```bash
    source ~/.bash_profile
    ```
