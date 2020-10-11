# Mysql
- ユーザー権限
    - user@localhostとuser@192.xxx.xxx.xxxは別ユーザー扱いで権限が異なる
- CSVインポート
    ```
    LOAD DATA LOCAL INFILE 'CSVファイルパス' 
    INTO TABLE テーブル名 
    FIELDS TERMINATED BY '区切り文字' 
    OPTIONALLY ENCLOSED BY '改行文字'
    ```
    - カラム指定
        ```
        (@1, @2)                    # CSVのカラム番号
        SET column1=@1, column2=@2  # Mysqlのカラム名
        ```
