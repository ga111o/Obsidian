## snippet

1. Create a Snippet File: `ctrl + shift + p`, search `snippet` and open `Configure User Snippets`

2. Add a Snippet: fllowing format:

    ```
    {
        "Print to Console": {
            "prefix": "log",
            "body": [
                "console.log('$1');",
            ],
            "description": "Log output to console"
        }
    }
    ```

    - `log`: if type _log_, recommended `body`'s content. then press `tab`, appear that
    - `$1`: cursor placed
