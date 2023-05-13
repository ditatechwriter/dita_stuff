# Installing the Vale linter

1. Install Vale.

    === Mac

    ```console
    # If you have Homebrew installed:
    
    brew install vale
    ```

    === Linux

    ```console
    # If you use apt-get:

    sudo apt-get install vale
    ```

    === Windows

    ```console
    # If you have Chocolatey installed:

    choco install vale
    ```

2. Clone this repository.

    ```console
    git clone git@github.com:Venafi/venafi-vale.git
    ```

3. Add the `.vale.ini` file to the root of the folder of the repository you whose content you want to lint.
4. Add the `styles` folder to the `.github` folder of the repository.
5. Update `.gitignore`:

    ```text
    # Vale
    .github/styles  # required if the repo uses GitHub Actions
    .vale.ini       # optional
    ```

6. Install the Vale VS Code extension.
7. Update the Vale VS Code extension settings to point to the Vale executable.
