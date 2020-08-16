# Rails
- migration
    - データベースの構造の変更に使用する機能
    - DSLを用いてSQLを書く必要がない
        - 以下を行うことでmigrationファイルの内容でデータベース構造が変更される
            1. migrationファイル作成
            1. rails db:migrateコマンド実行
- HTTPステータスのシンボル表現
    - Controllerからのステータにシンボルが使用できる(200 -> :ok, 201 -> :created 等)
- あいまい検索
    - 完全一致
        ```
        モデル名.where('カラム名 like ?','検索文字列')
        ```
    - 前方一致
        - % 任意の0文字以上の文字列
            ```
            モデル名.where('カラム名 like ?','検索文字列%')
            ```
- レコード数取得
    ```
    モデル名.count
    ```

- ActiveReocrdで生成されるSQLを確認
    - to_sql
    ```
    User.all().to_sql -> SELECT "users".* FROM "users"
    ```
 
- URLヘルパー
    - 与えられたコードからパスを推測して返すメソッド
    - rake routesで取得したPrefixに_path、_urlを付与して使用する
        - 例: Prefixがrootの場合 -> root_path or root_url
- before_action
    - Actionが実行される前に指定した処理を行うことが出来る
    - 各アクションで共通する処理を１箇所に集約することができる
        - オプション
            - only: 指定したActionでのみ処理を行う
                ```
                before_action :メソッド名, only: [:Action]
                ```
    - application_controller.rbに定義することで全Controllerで共通する処理を定義出来る
- destroyとdeleteの違い
    - destroy
        - ActiveRecordを介して削除する
        - 依存関係があるレコードも削除する
    - delete
        - ActiveRecordを介さずに削除
        - 直接SQLを実行して削除する
- newとcreateの違い
    - new
        - オブジェクトの生成行う
        - 生成したオブジェクトをsaveすることでDBに保存される
    - create
        - オブジェクトの生成と保存を行う
        - new + save
- render
    - Viewの表示の制御を行うためのメソッド
        - オプション
            - :location オプション
                - HTTPのLocationヘッダー（リダイレクト先のURL）を設定できる
- flashメッセージ
    - アクション実行後にメッセージを表示させる機能
    - アクションでflash[:notice]に文字列を代入するとflash[:notice]をビューで使用出来るようになる
- gem
    - React-Rails
        - RailsがwebpackによってビルドされたJavaScriptファイルを読み込めるよう、webpackerのjavascript_pack_tag helperを指定する必要がある
            - app/views/layouts/application.html.erbにjavascript_pack_tagを追加
                ```
                <%= javascript_pack_tag 'application' %>
                ```
            - ※Rails6の場合は、デフォルトで追加される
    - Webpacker
        - Webpackがrailsで使用できるようになるgem
            - Webpack
                - Webアプリケーションを構成するリソースを1つにまとめるモジュールバンドラー
    - Jbuilder
        - jsonのテンプレートエンジン
            - xxx.json.jbuilderファイルにDSLを記述するとjson形式でレスポンスを返すことができる
- resourceベースでないルーティング
    - usersにアクセスした場合、users_controller.rbのindexソッドが実行される
        ```
        get 'users', to: 'users#index'
        ```
    - 実行するアクションは省略可能(URLにパラメータを含む場合は省略不可)
        - URLにパラメータ(:id)を含まない
            ```
            namespace :api do
              delete 'users/destroy'
            end
            ```
            - 実行アクションを省略した場合、自動でアクションが設定される
                - ルーティング
                ```
                           Prefix Verb   URI Pattern                   Controller#Action
                api_users_destroy DELETE /api/users/destroy(.:format)  api/users#destroy
                ```
        - URLにパラメータ(:id)を含む(実行アクション省略)
            ```
            namespace :api do
              delete 'users/:id'
            end
            ```
            - ArgumentErrorが発生する
        - URLにパラメータ(:id)を含む
            ```
            namespace :api do
              delete 'users/:id', to: 'users#destroy'
            end
            ```
            - ルーティング
            ```
            Prefix Verb   URI Pattern              Controller#Action
               api DELETE /api/users/:id(.:format) api/users#destory
            ```
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
