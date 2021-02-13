===========================================
WSL のための諸設定およびドキュメント
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
