# DB
- オプティマイザ(optimizer)
    - SQLを効率的に実行するための仕組み
    - SQLの最適化及び実行計画の作成を行う
- コネクションプール(connection pool)
    - データベースにコネクション(接続)する場合に都度コネクションを作成するのではなく、コネクションをプール（保持）して再利用する機能
    - データベースへコネクションする回数が軽減し、データベースへのコネクションを確立するアプリケーションの負荷が軽減される
