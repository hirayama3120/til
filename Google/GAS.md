# GAS (Google Apps Script)
### Googleが提供するサービス全般で利用できるJavaScriptベースのスクリプト言語
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
    - 行で値が設定されている最終の列番号を取得
        ```
        Sheetオブジェクト.getLastColumn()
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
    - セル書き込み
        ```
        Rangeオブジェクト.setValue(data);
        ```
    - メッセージボックス表示
        ```
        Browser.msgBox("メッセージ")
        ```
    - チェックボックス
        - 挿入
            ```
            Rangeオブジェクト.insertCheckboxes();
            ```
        - 削除
            ```
            Rangeオブジェクト.removeCheckboxes();
            ```
    - 罫線設定
        - on: true, off: false, no change: null
            ```
            Rangeオブジェクト.setBorder(top, left, bottom, right, vertical, horizontal);
            ```
    - セルクリア
        - 全てクリア
            ```
            Rangeオブジェクト.clear();
            ```
