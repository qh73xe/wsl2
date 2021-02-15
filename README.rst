===========================================
WSL のための諸設定およびドキュメント
===========================================

入力文字変換

wsl2 の導入
===========================================

https://qiita.com/rubytomato@github/items/a290ecef2ea86ea8350f

windows terminal
===========================================

power shell
https://blog.mamansoft.net/2020/05/31/windows-terminal-and-power-shell-makes-beautiful/

管理者モード
https://stackoverflow.com/questions/62496779/opening-up-windows-terminal-with-elevated-privileges-from-within-windows-termin

色テーマ
https://qiita.com/flat35hd99/items/06d766253eeebdbaca70

その他
https://qiita.com/hikaruright/items/b415d569b5bbeaf967bd

power sehll
===========================================

scoop
===========================================

YUBIKEY
===========================================

https://www.yubion.com/post/ssh%E3%81%AE%E7%A7%98%E5%AF%86%E9%8D%B5%E3%82%92yubikey%E3%81%A7%E7%AE%A1%E7%90%86-windows%E7%B7%A8

GITHUB CLI
===========================================

OPEN を何とかする
===========================================

とりあえずファイル操作ができないのがつらいので,
:code:`open` コマンドを設定します.

自作してもよいのですが以下のライブラリで十分でしょう.
    - https://www.npmjs.com/package/wsl-open

導入方法は以下の通りです.

.. code-block:: bash

   $ sudo npm install -g wsl-open

また, :code:`open` で使用したいので,
エイリアスをつけておきます.

.. code-block:: bash
   :caption: zshrc

   alias open='wsl-open'

IME を何とかする
===========================================

IME は基本的に WINDOWS の制御になります.
そうすると, ubuntu 側からはどうしようもないので,
ubuntu 側から操作可能にします.

.. code-block:: bash

   PS > scoop install zenhan

このコマンドを UBUNTU 側から使用可能にするために
PATH を通しておきます.

.. code-block:: bash
   :caption: .zshrc

   export PATH="$PATH:/mnt/c/Users/<Your name>/scoop/apps/zenhan/current/"

これで以下のコマンドが使用可能になります.

.. code-block:: bash

   $ zenhan.exe 1  # 日本語入力
   $ zenhan.exe 0  # アスキー入力


GIT を何とかする
===========================================

https://qiita.com/wnoguchi/items/f7358a227dfe2640cce3

ssh
https://qiita.com/wnoguchi/items/f7358a227dfe2640cce3

GIT の基本設定は以下の通りです.

.. code-block:: bash

   $ git config --global core.autocrlf false
   $ git config --global user.name "<Your name>"
   $ git config --global user.email "<Your email>"
   $ git config --global core.editor vim

認証関係および SSL 関連がいろいろ面倒なので,
windows の認証系を利用するのが手っ取り早いです.

.. code-block:: bash

    $ git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager.exe"
