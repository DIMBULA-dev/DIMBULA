# YAMLフォーマット

DIMBULA teaBreakのテスト手順や条件を記すYAMLファイルについて説明します。

以下は、一例です。

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

## プロパティ

| 名称                | 説明                           |    必須    | タイプ | 有効値                                                                | 備考             |
|:------------------|:-----------------------------|:--------:|:---:|--------------------------------------------------------------------|:---------------|
| device            | テスト対象のデバイス名                  | Required | 文字列 | [Name](https://dimbula-web.kunimasu.com/support/devices) を参照       | -              | 
| os-version        | テスト対象のOSのバージョン               | Required | 文字列 | [OS Version](https://dimbula-web.kunimasu.com/support/devices) を参照 | -              |
| step-wait-time    | `steps` で実行する各ステップの間の待ち時間を指定 | Optional | 文字列 | Linuxの`sleep`コマンドと同等の引数                                            | `3s`を設定すると3秒待機 |
| system-navigation | システムUIのナビゲーションバーの表示方法を指定     | Optional | 文字列 | `gesture` `two` `three`                                            | -              |
| languages         | テストするOSの言語                   | Required | リスト | `en` `ja` 他 [言語切り替え](change_language.md) を参照                       | -              |
| steps             | テストする手順                      | Required | リスト | 以下stepsの説明を参照                                                      | -              |


### `steps`について。

操作したい手順を辞書の形式で記入します。
操作できる種類と有効値を以下の通りです。

#### 共通仕様
* `name`は、各ステップを説明する名称等をOptionalで自由入力
* 座標(0,0)を画面左上、座標(1,1)を画面右下とする

#### tap
```yaml
- tap: <x position> <y position>
``` 
* XとYの座標を指定してタップする

#### swipe
```yaml
- swipe: <from x position> <from y position> <to x position> <to y position>
```
* スワイプ開始のXとY、終了のXとYの座標を指定して画面をスワイプする

#### long-tap
```yaml
- long-tap: <x position> <y position>
```
* XとYの座標を指定して長押しする

#### capture
```yaml
- capture: <filename w/o extension>
```
* ファイル名を渡して、スクリーンショットを撮る
* PNG形式で保存
* 拡張子は不要
* DIMBULA teaBreakでのみ有効

#### wait
```yaml
- wait: <wait time>
```
* 指定秒数待機する
* 有効値は、Linux `sleep` コマンドの引数と等価

#### text
```yaml
- text: <alphanumeric character etc>
```
* 日本語等マルチバイトな文字列は不可
* マルチバイトに変換したい場合は、英数字等を送信して端末側で変換する
* 具体的には [KEYCODE](https://developer.android.com/reference/android/view/KeyEvent) で送信できる文字に限る

#### home
```yaml
- home
```
* 物理ホームボタン押下と等価

#### back
```yaml
- back
```
* 物理戻るボタン押下と等価

#### power
```yaml
- power
```
* 物理電源ボタン押下と等価

#### volume-up
```yaml
- volume-up
```
* 物理ボリュームアップボタン押下と等価

#### volume-down
```yaml
- volume-down
```
* 物理ボリュームダウンボタン押下と等価

