# Slack連携
DIMBULAでは、以下の目的でWebブラウザを使いますが、それ以外のことはSlashコマンドを使ってDIMBULAを利用します。

* DIMBULA SlackアプリをSlackワークスペースにインストールし、初回にアクティベイトするため
* DIMBULA teaBreakを使うために、Githubへログインして、アクセストークンを取得するため
* DIMBULA teaBreakで実行・録画したテスト中の動画やスクリーンショットを確認するため
* DIMBULA atWorkを使うため
* また、上記のためにブラウザでログインするため

ここでは、一部よく使うコマンドを紹介します。他のコマンドについては、`dimbula help`を実行し、どんなコマンドがあるのか、一読頂ければと思います。

# `dimbula me`
アカウントについて情報を表示します。

SlackのワークスペースにインストールしたDIMBULAアプリをアクティベイトするために、初回はワークスペース所有者又は管理者権限を持つ利用者が`Activate`リンクからアクティベーションを行ってください。
![img.png](../../../assets/image/welcome_dimbula.png)

アクティベイト済みの場合は、以下のようにメッセージが表示されます。
![img.png](../../../assets/image/dimbula_me_not_github.png)

DIMBULA teaBreakを使うために、Githubと接続されていれば、以下のメッセージがポストされます。
![img.png](../../../assets/image/dimbula_me_github.png)

機能的な面を以下に説明します。
* `Activate`は、Slackワークスペースの管理者又は所有者のみ実行可能
* ワークスペースの`reconect`も上記同様
* `Sign in`は、ブラウザにログインセッションを作成
* `Sign out`は、ブラウザに残っているログインセッションを破棄
* Githubの`connect` `reconnect` は、DIMBULA teaBreakを利用するためのGithubのアカウント連携
* `Disconnect Github`は、接続したGithubアカウントの連携解除
* `Delete from DIMBULA`は、DIMBULAの利用を終了するために、ワークスペースを削除する

# `dimbula use`
DIMBULA atWorkを利用するときに利用するコマンドです。モーダル表示で具体的に利用可能なモバイルの選択肢を表示されます。

![img.png](../../../assets/image/dimbula_use_modal.png)

モバイルの確保が出来ると、ブラウザで使うリンクがポストされます。
![img.png](../../../assets/image/dimbula_use_mobile.png)

# `dimbula quit`
現在利用中のモバイルの終了を行います。
![img.png](../../../assets/image/dimbula_quit_modal.png)

# `dimbula subscribe`
Github連携し、DIMBULA teaBreakでE2Eテストを行いますが、テスト終了の通知やGithub Checksを更新したときに通知してほしい、チャンネルを登録します。コマンドを実行すると、選択可能なGithubのリポジトリの選択肢が表示されます。
![img.png](../../../assets/image/dimbula_subscribe_modal.png)

対象のリポジトリは、DIMBULAのGithubアプリをインストールした個人や組織にのリポジトリです。全ての選択可能なリポジトリのトップ100件を表示します。もし選択したいリポジトリが選択肢に現れていない場合は、`dimbula subscribe <リポジトリのURL>`などで絞り込むことができます。詳細は、`dimbula help`をご確認ください。
![img.png](../../../assets/image/dimbula_subscribe_modal2.png)
