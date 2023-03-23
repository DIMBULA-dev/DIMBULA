# YAMLフォーマット

DIMBULA E2Eのテスト手順や条件を記すYAMLファイルについて、ここでは簡単な例として、ToDoアプリを一例に説明していきます。

```yaml
device: Pixel 4a
os-version: "13"
step-wait-time: 2
languages:
  - en
  - ja
steps:
  - name: Tap ToDo
    tap: 0.571 0.920
  - text: Go to the Bank
  - name: Tap Add
    tap: 0.894 0.541
  - name: Tap ToDo
    tap: 0.530 0.908
  - text: Submit quote in the afternoon
  - name: Tap Add
    tap: 0.888 0.551
  - name: Tap ToDo
    tap: 0.648 0.925
  - text: Meeting at 4pm
  - name: Tap Add
    tap: 0.886 0.545
  - name: Done Submit quote in the afternoon
    tap: 0.835 0.251
  - name: Done Go to the Bank
    tap: 0.884 0.168
  - name: Done Meeting at 4pm
    tap: 0.833 0.160
```

動作させるモバイルは、以下の条件をDIMBULAに要求しています。

* モバイルは、Pixel 4a
* OSバージョンは、13

テストでは以下の条件で動作します。
* テストする言語は、日本語と英語
* 手順間の待機時間は、2秒

操作したい手順を要約すると、3つのToDoを登録して、3つ全て完了にする手順です。
YAML内では、それぞれの座標や実際のテキスト入力を記述しています。
1. テキストフィールドをタップ
2. 「Go to the Bank」とテキスト入力
3. 「Add」ボタンをタップ
4. テキストフィールドをタップ
5. 「Submit quote in the afternoon」とテキスト入力
6. 「Add」ボタンをタップ
7. テキストフィールドをタップ
8. 「Meeting at 4pm」とテキスト入力
9. 「Add」ボタンをタップ
10. 「Submit quote in the afternoon」の完了ボタンをタップ
11. 「Go to the Bank」の完了ボタンをタップ
12. 「Meeting at 4pm」の完了ボタンをタップ

## プロパティ

| 名称                | 説明                      |                             必須                             | 有効値                                                                |
|:------------------|:------------------------|:----------------------------------------------------------:|--------------------------------------------------------------------|
| device            | テスト対象のデバイス名             |            <font color="orange">Required</font>            | [Name](https://dimbula-web.kunimasu.com/support/devices) を参照       | 
| os-version        | テスト対象のOSのバージョン          |            <font color="orange">Required</font>            | [OS Version](https://dimbula-web.kunimasu.com/support/devices) を参照 |
| step-wait-time    | `steps` で実行する各ステップの待ち時間 | <font color="grey"><i>Optional</i></font><br/>Default: 3秒  | Linuxの`sleep`コマンドと同等の引数                                            |
| system-navigation | システムUIのナビゲーションバーの表示     | <font color="grey"><i>Optional</i></font><br/>Default: 未指定 | `gesture` `two` `three`                                            |
| languages         | テストするOSの言語              |            <font color="orange">Required</font>            | `en` `ja` 他 [言語切り替え](../docs/change_language.md) のコードを参照                   |
| steps             | テストする手順                 |            <font color="orange">Required</font>            | 以下stepsの説明を参照                                                      |


## steps

操作したい手順を辞書の形式で記入します。
操作できる種類と有効値を以下の通りです。

### 共通仕様
* `name`は、各ステップを説明する名称等をOptionalで自由入力
* 座標(0,0)を画面左上、座標(1,1)を画面右下とする

### tap
```yaml
- tap: <x position> <y position>
``` 
* XとYの座標を指定してタップする

### swipe
```yaml
- swipe: <from x position> <from y position> <to x position> <to y position>
```
* スワイプ開始のXとY、終了のXとYの座標を指定して画面をスワイプする

### long-tap
```yaml
- long-tap: <x position> <y position>
```
* XとYの座標を指定して長押しする

### capture
```yaml
- capture: <filename w/o extension>
```
* ファイル名を渡して、スクリーンショットを撮る
* PNG形式で保存
* 拡張子は不要
* DIMBULA E2Eでのみ有効

### wait
```yaml
- wait: <wait time>
```
* 指定秒数待機する
* 有効値は、Linux `sleep` コマンドの引数と等価

### text
```yaml
- text: <alphanumeric character etc>
```
* 日本語等マルチバイトな文字列は不可
* マルチバイトに変換したい場合は、英数字等を送信してモバイル側で変換する
* 具体的には [KEYCODE](https://developer.android.com/reference/android/view/KeyEvent) で送信できる文字に限る

### home
```yaml
- home
```
* 物理ホームボタン押下と等価

### back
```yaml
- back
```
* 物理戻るボタン押下と等価

### power
```yaml
- power
```
* 物理電源ボタン押下と等価

### volume-up
```yaml
- volume-up
```
* 物理ボリュームアップボタン押下と等価

### volume-down
```yaml
- volume-down
```
* 物理ボリュームダウンボタン押下と等価

