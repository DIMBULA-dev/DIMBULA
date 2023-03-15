# DIMBULAについて

DIMBULAは、[株式会社Kunimasu](https://kunimasu.com/)が開発・運営するプロダクトです。<br />
弊社管理のモバイル実機端末を、以下の目的でご利用になることを想定しています。

1. **DIMBULA atWork**：ユーザサポートに必要な実機デバッグをスポット利用する
2. **DIMBULA teaBreak**：Github Workflowと連携し、アプリケーションのE2Eテストで継続利用する

DIMBULAでは、専用のSlackアプリとGithubアプリがあります。<br />
DIMBULA atWork、teaBreak共通して、Slackのアプリはインストール必須です。<br />
teaBreakをご利用する場合は、Githubアプリをインストールください。

# 特徴

DIMBULAの特徴は4つです。

## E2Eテスト手順はノーコード

E2Eテストするための手順は、YAML形式のテキストファイルに記載します。  
記載する情報は、テストする端末名、OSのバージョン、OSの言語、テストの手順を記した一覧です。  
DIMBULA atWorkで、操作を記録しYAMLファイルへ出力する機能をご活用ください。

 * [YAMLファイルの一例](https://github.com/DIMBULA-dev/simple-tap-text-input)

## 実機とエッジコンピュータ

ご利用いただく端末は全て実機で、その傍らには実機を制御するエッジコンピュータがペアで配備されています。<br />
E2Eテストでは、エッジコンピュータがテスト手順を制御するので、<br />
テストプログラムで不具合が起きたり、テストプログラムがモバイルリソースに与える影響は抑えられています。

## Github Workflow連携

Github Workflow上で、DIMBULA専用のアクションを記述すると、DIMBULA teaBreakを要求します。<br />
要求するモバイルに、Github Workflowで生成した指定のアーティファクトをインストールしてテストを実行します。<br />
テスト実行中は、録画され、必要に応じてスクリーンショットが撮影されます。<br />
テスト終了後に、録画された画面やスクリーンショットを確認し、Github Checksを更新することで合否判定とします。

## Slackがユーザインターフェース

SlackのSlashコマンドを使って、DIMBULAに対して要求を行います。<br />
Githubからの通知もSlackで受け取ります。<br />
Slackに参画するメンバーがDIMBULAのSlashコマンドを使えますので、DIMBULAへ個別に招待する等は不要です。

# デモ

事前準備として、DIMBULAのSlackアプリとGithubアプリはインストール済みです。

## DIMBULA atWork

## DIMBULA teaBreak
