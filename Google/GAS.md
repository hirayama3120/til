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
        - 行, 列, 行数, 列数指定
            ```
            var range = sheet.getRange(行番号, 列番号, 行数, 列数)
            ```
        - A1形式指定
            ```
            var range = sheet.getRange("A1:A1")
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
        - 値が存在するセル範囲を取得
            ```
            Sheetオブジェクト.getDataRange();
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
   - 数値をアルファベットに変換(0 -> A, 2 -> C)
      ```
      function ConvertToLetter(iCol) {
        var str = "";
        var iAlpha = 0;
        var iRemainder = 0;
         
        iAlpha = parseInt((iCol / 26), 10);
        iRemainder = iCol - (iAlpha * 26);
        if(iAlpha > 0) {
          str = String.fromCharCode(iAlpha + 64);
        }
        if(iRemainder >= 0) {
          str = str + String.fromCharCode(iRemainder + 65);
        }
        return str;
      }
      ```
   - 処理速度改善
       - ループ内でGAS API(getValue、setValue等)を毎回呼び出すと遅延につながる(都度、サーバー上のデータ更新、画面反映となるため)
       - GAS APIの呼び出しを減らすことで改善される
           - getValue、setValueをgetValues, setValuesにすることで呼び出す回数を削減できる
           - (２次元配列での取得、書き込みになり、呼び出しが各1回で済むため)
