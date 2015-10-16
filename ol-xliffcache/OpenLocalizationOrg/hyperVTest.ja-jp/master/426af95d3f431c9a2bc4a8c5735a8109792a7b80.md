デザイン ドキュメントの発行を開くへようこそ
======================

これは、MSDN 開く公開が電源に開いている公開デザイン ドキュメントのリポジトリです。

クイック スタート
---------

原因となっている、次の手順を使用して発行オープンのドキュメントを開始します。

1. リポジトリを複製するには。
   ```
   git clone https://github.com/openpublish/docs.git
   ```

2. Markdown エディターを使用して、Markdown ファイルを編集します。
3. コミットし、変更をプッシュします。
   ```
   git add -u
   git commit -m "update doc"
   git push
   ```

4. 少し待ってからに、変更が自動的に発行されます。
    
    -   ドキュメント セット 1: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/community
    -   ドキュメント セット 2: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/hyperv_で_windows
    -   ドキュメント セット 3: https://msdnnext.redmond.corp.microsoft.com/olorg/hypervtest/virtualization/windowscontainers


> このリポジトリにプッシュするアクセス許可を持っていない場合は、自分のアカウントを分岐することとプルの要求を使用して、バックアップの変更を送信します。

検証とプレビュー
--------

変更内容をリモートにプッシュする前に、ビルドしを早期に問題を検出するローカルのドキュメントをプレビューできます。

1. 変更内容を検証するには、実行するだけ `msbuild` リポジトリのルートにあります。
2. 変更内容をプレビューするには。
    1. 実行 `msbuild/t:serve` リポジトリのルートにあります。
    2. 開いている `http://localhost:8000` 、ブラウザーにします。





