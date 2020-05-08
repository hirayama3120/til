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
