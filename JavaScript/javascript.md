# JavaScript
- Fetch API
    - 非同期通信でHTTPリクエスト送信、レスポンスの受け取りが出来る
    - fetch()メソッドを呼び出すことでリクエストを送信できる
- fetch()メソッド
    - Promiseを返す
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
- Promise
    - 非同期処理の成否(resolved/reject)を表すオブジェクト
        - then() と catch() という2つのメソッドを持っている
            - 成功時: then()の処理を実行
            - 失敗時: catch()の処理を実行
