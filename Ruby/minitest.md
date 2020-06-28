# minitest
### テスティングフレームワーク
- xUnit形式とspec形式の書き方がある
    - xUnit形式
        - シンタックス: ピュアRuby
    - spec形式
        - シンタックス: DSL(ドメイン固有言語)
        - RSpecに近い形式
        - describe,contextが使える
- spec
    - RSpec風のDSLが使えるようになる
    ```
    require 'minitest/spec'
    ```
 
- autorun
    - autorunをrequireするとファイルを実行するとテストが実行されるようになる
    ```
    require 'minitest/autorun'
    ```
    
- setupメソッド
    - テストメソッドの実行前に毎回呼び出される
    
- アサーション
    - assert
        - 実行結果が真かチェック
    - refute
        - 実行結果が偽かチェック
    - assert_equal
        - 2つの値が同じかチェック
    - refute_equal
        - 2つの値が異なるかチェック

- テストデータ登録
    - Fixture
        - テスト実行前に対応テーブルのデータを削除してからfixtureのデータを登録する
        - YAMLで記述し、/test/fixturesに配置
            ```
            user1:
              name: xxx
              age: xxx
            ```
        - テストでのレコード取得
            ```
            @user = users(:user1)
            @user.name
            ```
            
- assert_difference
    - 第1引数の値がブロック内で変更されることを検証する
    - 第2引数に期待値を指定する
        - 省略した場合は、+1になる
