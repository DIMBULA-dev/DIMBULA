# DIMBULA E2E
DIMBULA E2Eは、Github Actionsと連携した、Mobile CI（Continuous Integration）プロダクトです。

<iframe style="margin-bottom: 20px; max-width: 100%;" width="560" height="315" src="https://www.youtube.com/embed/81v6j_NUvS4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# 特徴

### Github Actionsと連携したE2Eテスト
柔軟且つ強力なGithubの機能を活かし、ActionsでCI/CDを構築する運用に、専用アクションを1つ追加するだけでGithub Checks付きのE2Eテストをリクエストできます。

### テストの手順や条件はYAMLに記載
テストコード不要なので、テストコードの不具合によるアプリのクラッシュ、予期せぬ動作がありません。ユーザ視点でテストの手順を作成して、テストしたいモバイルの条件をYAMLファイアルに記述するだけです。DIMBULA Computingを利用することで、YAMLファイル自体の生成を支援します。

### 実機モバイルでE2Eテストを実行
弊社管理の実機モバイルでE2Eテストが出来ます。テスト中は画面を録画、テスト手順の1つにスクリーンショットを撮ることができるので、テスト結果を動画と静止画で確認できます。

### エッジコンピュータがテストを実行
実機モバイルとペアで存在するエッジコンピュータがテストコードを実行するため、テストコードが与える実機モバイルリソースの影響が抑えられています。

# 制約
* DIMBULA E2Eのテストは3分が上限
* 空き端末がなければ、空くまで待機

# セットアップ
1. [DIMBULA Slackアプリのインストールとセットアップ](./slack_setup.md)
2. [DIMBULA Githubアプリのインストールとセットアップ](./github_setup.md)
3. [DIMBULA E2Eのテスト条件と手順を作成](./create_e2e_test.md)
4. [Github ActionsのWorkflowにDIMBULA E2E専用アクションを記述](./dimbula_action.md)
