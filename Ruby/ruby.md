# Ruby
- 数値と文字列の数値の比較
    - "1" == 1 ->比較可能
    - "1" > 1 ->比較不可(ArgumentErrorが発生)
        - ArgumentErrorが発生する原因
            - \> と == の動作の違いにより発生
                - 比較演算子は、 <=> 演算子を利用して定義される
                    - self <=> other は以下をそれぞれ返すことが期待されている
                        - self が other より大きいなら正の整数
                        - self と other が等しいなら 0
                        - self が other より小さいなら負の整数
                        - self と other が比較できない場合は nil
                            - <=> 演算子で、IntegerとStringを比較するとnilを返す
                - Comparable#>
                    - <=> が正の整数を返した場合に、true を返す
                    - それ以外の整数を返した場合に、false を返す
                    - <=> が nil を返したときにArgumentErrorが発生
                - Comparable#==
                    - <=> が 0 を返した時に、true を返す
                    - それ以外を返した場合は、false を返す
    - https://rurema.clear-code.com/library:_builtin/type:instance-method/query:comparable/query:%3E/version:2.3.0/
- require メソッド
    - $LOAD_PATHに指定されているパスからの相対パスで該当のファイルを参照する
- require_relativeメソッド
    - require_relativeが記述されたファイルからの相対パスを参照する