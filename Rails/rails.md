# Rails
- migration
    - データベースの構造の変更に使用する機能
    - DSLを用いてSQLを書く必要がない
        - 以下を行うことでmigrationファイルの内容でデータベース構造が変更される
            1. migrationファイル作成
            1. rails db:migrateコマンド実行
- rails test実行時にエラー発生
    ```
    xxxx-xx-xx xx:xx:xx WARN Selenium [DEPRECATION] Selenium::WebDriver::Chrome#driver_path= is deprecated. Use Selenium::WebDriver::Chrome::Service#driver_path= instead.
    C:/Ruby/Ruby24-x64/lib/ruby/site_ruby/2.4.0/bundler/runtime.rb:84:in `rescue in block (2 levels) in require': There was an error while trying to load the gem 'chromedriver-helper'. (Bundler::GemRequireError)
    Gem Load Error is: not executable: "C:/Ruby/Ruby24-x64/lib/ruby/gems/2.4.0/gems/chromedriver-helper-2.1.1/bin/chromedriver-helper"
    Backtrace for gem load error is:
    ```
    - chromedriver-helperのバージョンに1.2.0を指定することでエラーは解消する
        - https://stackoverflow.com/questions/52630480/rails-seleniumwebdrivererrorwebdrivererror-not-executable-chromedriver
    - chromedriver-helperは、2019年3月31日でサポートが終了しているため、webdriversへの移行が推奨されている
        - https://qiita.com/jnchito/items/f9c3be449fd164176efa