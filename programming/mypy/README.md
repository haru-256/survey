# mypyについて

# なぜ必要か

Pythonは動的型付言語ですが、それ故に様々なバグを保有しがち。

それを受け静的に型付をおこなうために、Python3.5から型アノテーションを付ける構文（PEP484）が追加されました。この流れはJavaScript等でも同じ（TypeScriptの台頭）。しかし、その型アノテーションが本当に正しいのかチェックする手段がなく、単にオプションとしてつけられていることが多いです。その方チェックツールとしてmypyが使用される。

利点

- **静的型アノテーションを使うと可読性が向上します。**
  - 関数定義内で引数の型チェック（isinstace等を使用した）をしなくて良いpy 
- **自信を持ってリファクタリングできます。**
- **mypy によって頻繁にバグが捕捉される。**
- 

# 参考

- https://qiita.com/t2y/items/f95f6efe163b29be59af
- https://mypy.readthedocs.io/en/latest/cheat_sheet_py3.html
- https://www.python.org/dev/peps/pep-0484/
- https://qiita.com/t2y/items/2a1310608da7b5c4860b
- https://qiita.com/k-saka/items/8f05c89f675af219e081