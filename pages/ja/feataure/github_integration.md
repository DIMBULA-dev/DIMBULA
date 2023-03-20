# Github連携
Githubと連携する目的は、Github WorkflowからDIMBULA teaBreakを活用することです。これまで個人もしくは自社で運用してきたGithub Workflowの運用ルールに加えるだけで、DIMBULA teaBreakを活用出来ます。

# セットアップ
まずは、DIMBULAのGithubアプリを、利用したいGithub上の個人や組織にインストールしてください。

<a href="https://github.com/marketplace/dimbula-real-mobile-ci-computing" style="border-radius: 8px;background-color: white;height: 38px;display: inline-block;position: relative;width: 165px; border: 1px solid #c8c8c8;font-weight: normal !important;" target="_blank">
  <img src="../../../assets/image/github-icon.png" alt="Github" height="30" style="display: inline-block;margin: 4px 8px 5px 8px;">
  <span style="color: black; font-size: 16px; position: absolute; top: 8px;">Add to <b>Github</b></span>
</a>

次に、Githubのアカウントを連携します。Githubが未接続の場合、`/dimbula me`を送信すると、以下のように`Not connected`と表示されます。`connect`のリンクからGithubアカウントを接続してください。
![dimbula_me_not_github.png](../../../assets/image/dimbula_me_not_github.png)

接続して再度`/dimbula me`を送信すると、Githubが`Connected`になり、`Client ID`が表示されます。`Client ID`は、あなたを識別するIDで、Github WorkflowでteaBreakのアクションを使う際に使用します。
![dimbula_me_not_github.png](../../../assets/image/dimbula_me_github.png)

これは必須のセットアップではありませんが、DIMBULA teaBreakのE2Eテストが終わった時やGithub Checksを更新したときの通知を受けたい場合は、Slackのチャンネルに講読したいリポジトリを登録してください。
詳しくは、[通知を受け取る](../docs/receive_notification.md) を参照ください。

