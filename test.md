■親側

    [github]

    ・リポジトリを作成

    自身のアカウントでリポジトリをGitHub上で作成
    https://github.com/new にアクセスする。
    以下を入力する。
    Owner: 自分のアカウント ※ 組織アカウントに作らないようにご注意ください。
    Repository name: training-git
    (任意の名称でもOK、以降はtraining-git前提で進めるので読み替えてください)
    公開範囲: Public
    Initialize this repository with: 「Add a README file」のみチェック
    「Create repository」ボタンをクリック

    
    ・developブランチ作成

    リポジトリのメインページに移動 (https://github.com/{★自身のユーザー名}/training-git/)
    ブランチ名に「develop」を入力し、「Create branch: develop from 'main'」をクリック
  ![alt text](<スクリーンショット 2025-03-19 180219.png>)

    ・ブランチ設定

    （※下記設定でデフォルトブランチをdevelopへ変更＆必ずプルリクエストしないとmerge出来ない設定になる）
    デフォルトブランチをdevelopに変更
    リポジトリのメインページに移動
    「Settings」タブをクリック
    Default branch
    切り替えアイコンをクリック
  ![alt text](<images/スクリーンショット 2025-03-19 182110.png>)

    「develop」を選択して、「Update」ボタンをクリック
    「I understand, update the default branch.」ボタンをクリック
    ブランチ保護ルール追加
    リポジトリのメインページに移動
    「Settings」タブをクリック
    サイドメニューの「Branches」をクリック
    Branch protection rules
    「Add rule」ボタンをクリック
    Branch name pattern: *[main|develop]* （mainとdevelopに適用）
    以下をチェック
    「Require a pull request before merging」
    ※ サブ項目のチェックは外す
    「Create」ボタンをクリック


    ・親側のテストファイル作成～git pushまで

    githubからファイルをダウンロードする
    「< >code」ボタンを選択してHTTPSのURLをコピー
  ![alt text](<images/スクリーンショット 2025-03-19 183151.png>)

    [vscode]
    vscodeのターミナルに
    git clone コピーしたURL　を入力
    「ファイル」タブから「フォルダーを開く」でダウンロードしてきたフォルダを開く
    touch ファイル名（例：テスト.txt）　を入力してテスト用のファイルを作成
    上記のテスト用のファイルに任意の文章を記載、保存
    git status を入力して、現在の状態を確認する（任意）
    git add ファイル名　を入力して任意のファイルをステージングする
    git commit -m "任意の編集メッセージを記載"　を入力する
    git push　を入力してリモートリポジトリに反映させる

    [github]
    githubに追加したファイルがあるか確認する


    ◆子側
    [github]
    ・子側のデータダウンロード

    githubからファイルをダウンロードする
    「< >code」ボタンを選択してHTTPSのURLをコピーまたは親側の人にURLを教えてもらう
    [vscode]
    vscodeのターミナルに
    git clone コピーしたURL　を入力
    「ファイル」タブから「フォルダーを開く」でダウンロードしてきたフォルダを開く
    ・featureブランチの作成（developブランチからfeatureブランチを新規作成してブランチを移動している）
    git checkout feature/ブランチ名　を入力
    ターミナルのディレクトリ名がdevelopからfeature/ブランチ名に変わったのを確認
    git branch を入力しても確認できる（任意）


    ・テストファイルの追加編集
    テスト用のファイルに任意の文章を追加、保存
    git status を入力して、現在の状態を確認する（任意）
    git add ファイル名　を入力して任意のファイルをステージングする
    git commit -m "任意の編集メッセージを記載"　を入力する
    git push　を入力してリモートリポジトリに反映させる（
    ※子側にgit pushの権限がないとエラーが出る
    エラーが出た場合は、親側がgithubから子側のgithubユーザー名を検索して権限を与える

    git push　
    （上記エラーが出た場合は認証後にgit push --set-upstream origin feature/ブランチ名）
    を入力してリモートリポジトリに反映させる
    [github]
    feature/ブランチ名のブランチに追加したファイルがあるか確認する


    ・プルリクエストを送る





