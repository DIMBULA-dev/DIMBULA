# DIMBULA Githubアクション
DIMBULA E2Eをリクエストするために、Github ActionsのWorkflowにはトリガーとなるアクションの記述が必要です。DIMBULAは、[専用アクション](https://github.com/kunimasu-com/DIMBULA-E2E-test-trigger) を提供しています。

一例として、[ToDoアプリ](https://github.com/kunimasu-com/DIMBULA-simple-tap-text-input) の [Github Workflowで専用アクションの呼び出し部分](https://github.com/kunimasu-com/DIMBULA-simple-tap-text-input/blob/main/.github/workflows/build.yml#L36) を参照ください。

# 専用アクションの記述
`.github/workflows`以下にWorkflowの定義を行いますが、DIMBULA専用アクションは以下のように記述します。ネイティブアプリをテストするときは、アプリをビルドし、生成したアプリのパスを指定します。本ページ冒頭にある一例では、以下のジョブに定義したとおり、ソースコードをチェックアウトしたあと、Gradleでビルドしたパスを指定します。
```yaml
  - uses: kunimasu-com/DIMBULA-E2E-test-trigger@main
    with:
      client-id: bWx7nS8Magkg5y1UuuaC
      app-artifact-path: app/build/outputs/apk/debug/app-debug.apk
```

もしテストがWebであれば、テストしたいURLを指定します。
```yaml
  - uses: kunimasu-com/DIMBULA-E2E-test-trigger@main
    with:
      client-id: bWx7nS8Magkg5y1UuuaC
      web-test-url: https://dimbula.kunimasu.com
```

# プロパティ
専用アクションに設定できる主要なプロパティです。他にも定義された [プロパティ](https://github.com/kunimasu-com/DIMBULA-E2E-test-trigger/blob/main/action.yml) がありますが、基本的には未指定でアクションを記述します。

| 名称                | 説明               |                    必須                     | 有効値                                              |
|:------------------|:-----------------|:-----------------------------------------:|--------------------------------------------------|
| client-id         | DIMBULAのクライアントID |   <font color="orange">Required</font>    | `/dimbula me`で取得                                 | 
| app-artifact-path | テストするアプリのパス      | <font color="grey"><i>Optional</i></font> | Github Actionsでビルドしたアプリに限らず、Github Actionsで扱えるパス |
| web-test-url      | テストするWebのURL     | <font color="grey"><i>Optional</i></font> | インターネット上のURL                                     |

# アクションのエラー

アクションは、bashスクリプトで記述されていますが、E2Eテストをリクエストするまでの間に以下の理由でエラーになる可能性があります。

| ステータスコード | 説明                                        | 解決方法                    |
|:---------|:------------------------------------------|:------------------------|
| 1        | `app-artifact-path` `web-test-url` が共に未指定 | どちらか一方を指定してください         | 
| 2        | 弊社ストレージにアップロードするURLの取得に失敗した               | 基本的には不具合なので、弊社にレポートください |
| 3        | 弊社ストレージにアップロードするURLの取得に失敗した               | 基本的には不具合なので、弊社にレポートください |
| 4        | 弊社ストレージにアプリのアップロードが失敗した                   | 基本的には不具合なので、弊社にレポートください |
| 5        | DIMBULA E2Eへのリクエスト失敗                      | 基本的には不具合なので、弊社にレポートください |

