# OnsenUIとは

モバイル向けのHTML/CSSフレームワーク
https://ja.onsen.io/

HTMLでモバイル向けのリッチなUIを作成することができる。

## ハマったところ

### テンプレートを別にできない

#### 環境
OnsenUI+Angular

#### 状況
・ComponentとHTMLファイルを分離
・リスト表示にng-forを使う

#### 現象
・ng-forでエラーになる

#### 原因
・不明
　→テンプレートをrequire('{パス}')で読み込むためng-forが解釈できていない？

通常のAngularの場合テンプレートの読み込みは↓のようにパスを文字列で指定するだけだが、
```xxx.component.ts
@Component({
  templateUrl: 'パス',
  ・・・
```
OnsenUIの場合は↓のようにrequireで読み込まないといけない。
```xxx.component.ts
@Component({
  templateUrl: require('パス'),
  ・・・
```
これが、原因だとは思うが、詳細は不明。

#### 解決策
とりあえず、ComponentとHTMLを分離せず、1ファイルで書けば回避はできる
→1ファイルがかなり大きくなるため、何とかしたい。。。
