# 通知を受け取る
DIMBULA teaBreakでは、E2Eテストの終了時や、Github Checks更新時に、講読されたSlackチャンネルに通知してお知らせします。

通知を受け取る設定をしていなくても、DIMBULA teaBreakは機能しますが、テストが終了したことに気付かないといったことが起きますので、登録しておく方が良いでしょう。

# セットアップ
通知を受信したいチャンネルで、`/dimbula subscribe <GithubリポジトリURL>`を入力して、通知を受けたいDIMBULA teaBreakの対象リポジトリを指定します。
![img.png](../../../assets/image/dimbula_subscribe_url.png)

設定が完了すると、以下のようなメッセージがポストされます。
![img.png](../../../assets/image/dimbula_subscribed.png)

# 通知のイメージ
DIMBULA teaBreakで指定の言語、端末やOSバージョンの組み合わせで全てのE2Eテストが終えたときやChecksが更新されたときに、以下のような内容でポストされます。
![dimbula_me_not_github.png](../../../assets/image/dimbula-teaBreak-notification.png)
