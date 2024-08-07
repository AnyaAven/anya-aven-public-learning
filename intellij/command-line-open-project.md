## Setting up `idea your-dir` command for IntelliJ

To run IntelliJ IDEA from the shell, use the open command with the following options:
* `-a` Specify the application.
* `-n` Open a new instance of the application even if one is already running.
* `--args` Specify additional arguments to pass to the application.

For example, you can run IntelliJ IDEA.app with the following command:
```shell
open -na "IntelliJ IDEA.app"
```

### Create `idea your-dir` Shell Script

1. Open Terminal: You can open Terminal by searching for it in Spotlight (Command + Space) and typing "Terminal".
2. Navigate to /usr/local/bin: Ensure the directory exists. If not, you may need to create it.
    ```shell
    sudo mkdir -p /usr/local/bin
    ```
3. Create and Edit the Script: Use a text editor to create and edit the file.
   You can use nano, vi, or any other terminal-based editor. Here, I'll use nano.
    ```shell
    sudo nano /usr/local/bin/idea
    ```
4. Add the Script Content:
  * In the nano editor, type or paste the following content:
    ```shell
    #!/bin/sh
    open -na "IntelliJ IDEA.app" --args "$@"
    ```

    * Save the file by pressing Control + O, then press Enter to confirm.
    Exit the editor by pressing Control + X.
5. Make the Script Executable:
  * You need to change the file permissions to make it executable.
    ```shell
    sudo chmod +x /usr/local/bin/idea
    ```
---
### Explanation

* `sudo` enables superuser access.
* `#!/bin/sh`: This line specifies that the script should be run with the Bourne shell.
* `open -na "IntelliJ IDEA.app" --args "$@"`: This line uses the open command to 
launch the IntelliJ IDEA application, passing any additional arguments ("$@") to it.
---
#### Resources
* [IntelliJ Docs](https://www.jetbrains.com/help/idea/2024.1/working-with-the-ide-features-from-command-line.html?Working_with_the_IDE_Features_from_Command_Line#standalone)
* [Toolbox Way Stack Overflow](https://stackoverflow.com/questions/46351096/create-command-line-launcher-intellij-not-found/56050914#56050914)