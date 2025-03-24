# 子側と親側の両方がブランチの作成、削除するまでの流れ(1周分)


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
  ![alt text](<images/スクリーンショット 2025-03-19 180219.png>)

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


    ・featureブランチの作成（developブランチからfeatureブランチを新規作成してブランチを移動する）

    git checkout -b feature/ブランチ名　を入力
    ターミナルのディレクトリ名（青色の部分）がdevelopからfeature/ブランチ名に変わったのを確認
  ![alt text](<images/スクリーンショット 2025-03-24 172059.png>)

    git branch を入力しても確認できる（任意）


    ・テストファイルの追加編集

    テスト用のファイルに任意の文章を追加、保存
    git status を入力して、現在の状態を確認する（任意）
    git add ファイル名　を入力して任意のファイルをステージングする
    git commit -m "任意の編集メッセージを記載"　を入力する
    git push　を入力してリモートリポジトリに反映させる（
    ※子側にgit pushの権限がないとエラーが出る
    エラーが出た場合は、親側がgithubから子側のgithubユーザー名を検索して権限を与える
■親側（権限付与のエラーが出た場合）

    [github]
    「Settings」タブをクリック
    サイドメニューの「collaborators」をクリック
    「add people」から任意のアカウント名を検索、追加する
  ![alt text](<images/スクリーンショット 2025-03-21 104539.png>)


◆子側

    ・エラーの続き

    [github]
    右上のメールアイコンから、権限許可の認証を承認する


    ・エラー解消またはエラーが出なかった場合

    [vscode]
    ※最初のみ　git push --set-upstream origin feature/ブランチ名
    を入力してリモートリポジトリに反映させる　以後　git push　のみで可

    [github]
    feature/ブランチ名のブランチに追加したファイルがあるか確認する
  ![alt text](<images/スクリーンショット 2025-03-24 174106.png>)

    ・プルリクエストを送る

    リポジトリのメインページに移動
    「Pull requests」タブをクリック
    「New pull request」ボタンをクリック
    ブランチを以下のように選択し、「Create pull request」をクリック
    「base: develop」 ← 「compare: feature/ブランチ名」
    「Open a pull request」画面で「Create pull request」をクリック

  ![alt text](<images/スクリーンショット 2025-03-24 180142.png>)


■親側

    ・プルリクエストを確認し、merge後にfeatureブランチ（github側）を削除する

    [github]
      Merge pull request」ボタンをクリック
    「Confirm merge」ボタンをクリックし、マージを行う。
    「Delete branch」ボタンをクリックし、Featureブランチを削除
   ![alt text](<images/スクリーンショット 2025-03-24 110946.png>)


◆子側

    ・ローカル（vscode側）のfeatureブランチを削除する

    [vscode]
    git checkout develop　を入力してdevelopブランチに移動する
    git branch -d feature/ブランチ名　を入力してブランチを削除する
    git branch　を入力してfeature/ブランチ名が削除されているか確認（任意）

    ・ローカルリポジトリのdevelopブランチを最新の状態に合わせる（任意）

    git pull　を入力する

    [github]
    feature/ブランチ名が削除されているか確認


■親側

    ・developブランチを最新の状態にする

    [vscode]
    git pull　を入力

    ・featureブランチの作成（developブランチからfeatureブランチを新規作成してブランチを移動する）

    git checkout -b feature/ブランチ名　を入力
    ターミナルのディレクトリ名がdevelopからfeature/ブランチ名に変わったのを確認
    git branch を入力しても確認できる（任意）

    [vscode]

    ・テストファイルの追加編集

    テスト用のファイルに任意の文章を追加、保存
    git status を入力して、現在の状態を確認する（任意）
    git add ファイル名　を入力して任意のファイルをステージングする
    git commit -m "任意の編集メッセージを記載"　を入力する
    git push　を入力してリモートリポジトリに反映させる（
    ※最初のみ　git push --set-upstream origin feature/ブランチ名
    を入力してリモートリポジトリに反映させる　以後　git push　のみで可

    [github]
    feature/ブランチ名のブランチに追加したファイルがあるか確認する

    ・プルリクエストを送る

    リポジトリのメインページに移動
    「Pull requests」タブをクリック
    「New pull request」ボタンをクリック
    ブランチを以下のように選択し、「Create pull request」をクリック
    「base: develop」 ← 「compare: feature/ブランチ名」
    「Open a pull request」画面で「Create pull request」をクリック

    ・プルリクエストを確認し、merge後にfeatureブランチ（github側）を削除する

    「Merge pull request」ボタンをクリック
    「Confirm merge」ボタンをクリックし、マージを行う。
    「Delete branch」ボタンをクリックし、Featureブランチを削除

    [vscode]
    ・ローカル（vscode側）のfeatureブランチを削除する
    git checkout develop　を入力してdevelopブランチに移動する
    git branch -d feature/ブランチ名　を入力してブランチを削除する
    git branch　を入力してfeature/ブランチ名が削除されているか確認（任意）

    ・ローカルリポジトリのdevelopブランチを最新の状態に合わせる（任意）
    git pull　を入力する

    [github]
    feature/ブランチ名が削除されているか確認





