# FileWalker

FileWalker is a command-line utility for Windows designed to search for files within the filesystem and perform various operations on the search results.

## Parameters

*   **`fileName`**: The name of the file to search for. This can include wildcards (e.g., `*.log`, `document?.docx`).
*   **`rootPath`**: The starting directory for the search. You can provide a specific path (e.g., `D:\Users\MyUser\Documents`) or use `*` to search all logical drives on the system (excluding the C: drive).
*   **`<path_to_file_list.txt>`**: (Command-line argument) When starting the application, you can provide a single argument which is the path to a text file. Each line in this file should be a full path to a file. The application will then attempt to delete every file listed.

## Process

1.  **Launch the application**: Run `FileWalker.exe`.
2.  **Provide Search Criteria**:
    *   The application will first prompt you for the **`fileName`**.
    *   Next, it will ask for the **`rootPath`**.
3.  **Search**: The application searches for files matching the `fileName` starting from the `rootPath`. The results are saved to a file named `files_HHmmss.txt` in the application's directory.
4.  **Perform Operations**: Once the search is complete, a list of commands will be displayed, allowing you to perform actions on the list of found files.

### Available Commands

After a search is completed, you can use the following commands:

*   **`n` or `no`**: Clears the current search results and starts a new search.
*   **`delete`**: Deletes all the files found in the search. A confirmation prompt will appear.
*   **`show`**: Displays the full path of all found files directly in the console.
*   **`file`**: Opens the generated text file (e.g., `files_143055.txt`) that contains the list of found file paths.
*   **`hash`**: Calculates and displays the MD5 and SHA256 hashes for each file found. The results are also appended to a `Hash.txt` file in the respective file's directory.
*   **`creationtime now`**: Sets the creation and last modified time of all found files to the current system time.
*   **`creationtime dt:<datetime>`**: Sets the creation and last modified time of all found files to a specific date and time. The expected format is `yyyy-mm-dd hh:mm:ss`.
*   **`creationtime modifiedtime`**: Sets the creation time of all found files to match their last modified time.
*   **`execute all`**: Attempts to launch/execute every file found in the search.

### Deleting Files from a List

You can also use FileWalker to delete a predefined list of files by passing a text file's path as a command-line argument.

```shell
FileWalker.exe C:\path\to\your\filelist.txt
```

The application will read every file path from `filelist.txt` and ask for a final confirmation before deleting them.

```