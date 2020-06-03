# Git
- リモートURL確認
    ```
    git remote -v
    ```
- リモートURL変更
    ```
    git remote set-url <リポジトリ名> <変更後URL>
    ```
- 変更を一時的に退避
    - 退避
        ```
        git stash
        ```
    - 退避状態を確認
        ```
        git stash list
        ```
    - 退避した変更を再適用
        ```
        git stash apply stash@{x}
        ```
    - 退避した変更を削除
        ```
        git stash drop stash@{x}
        ```
    - 再適用と削除を同時に行う
        ```
        git stash pop stash@{x}
        ```
