# Linting Markdown with Vale

## Install Vale


=== "Mac"

    ```console
    # If you have Homebrew installed:

    brew install vale
    ```

=== "Linux"

    ```console
    # If you use apt-get:

    sudo apt-get install vale
    ```

=== "Windows"

    ```console
    # If you have Chocolatey installed:

    choco install vale
    ```

## Clone this repository

```bash
git clone git@github.com:ditatechwriter/dtw-vale.git
```

## Configure Vale

1.  Add the `.vale.ini` file to the root of the folder of the repository whose content you want to lint.

2.  Add the `styles` folder to the `.github` folder of the repository.

3.  Update `.gitignore`:

    ```ini
    # Vale
    .github/styles  # required if the repo uses GitHub Actions
    .vale.ini       # optional
    ```


## Install Visual Studio Code Vale extension

1.  Install the Vale VS Code extension.

2.  Update the Vale VS Code extension settings to point to the Vale executable.
