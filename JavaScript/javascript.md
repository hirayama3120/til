# JavaScript
- Fetch API
    - HTTPリクエストを発行するAPI
        - 第1引数: url, 第2引数: オプション
        ```
        fetch(url);
        ```
        - デフォルトではGETリクエストになる
        - GET以外のリクエストの場合は、オプションでmethodを指定する
        ```
        fetch(url, {
          method: "POST",
          body: data
        });
        ```
