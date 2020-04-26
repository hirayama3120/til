- ログ出力
    - Logger.log(data);
        - スクリプトエディタからGASのプログラムを実行後、Ctrl + Enter で確認出来る
- スプレッドシート
    - スクリプト実行ボタン設定
        - 挿入 -> 図形描写 -> 保存して終了 -> 図形選択 -> スクリプト割り当て
    - シート名指定でSheetオブジェクトを取得
        ```
        var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName('テーブル名');
        ```
    - Rangeオブジェクト(セル範囲)の取得
        - 行数指定
            ```
            var range = sheet.getRange(行番号, 列番号, 行数)
            ```
    - 列で値が設定されている最終の行番号を取得
        ```
        Sheetオブジェクト.getLastRow()
        ```
    - セル値の取得
        - 指定範囲のセルの最初の値を取得
            ```
            Rangeオブジェクト.getValue();
            ```
        - 指定範囲のセル全ての値を取得
            ```
            Rangeオブジェクト.getValues();
            ```