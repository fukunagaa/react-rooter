# react-router-training
react-routerの基礎を学ぶプロジェクト

## プロジェクト作成
- ディレクトリ作成
```
$ mkdir react-basic
$ cd react-basic
```
- 初期化
```
$ npm init -y
```
- webpackに関するインストール(今回はbabelもインストール)
```
$ npm install --save-dev webpack webpack-cli webpack-dev-server
$ npm install --save webpack webpack-cli
$ npm install --save-dev @babel/core @babel/preset-env @babel/preset-react babel-loader
$ npm install --save-dev react react-dom
```

- react-routerをインストールする(**今回のメイン**)
```
$ npm install --save-dev react-router react-router-dom
```

- ~~babel-plugin-react-html-attrsをインストールする(JSXではclassNamesを使うところ、classを使えるようにする)~~ これは今回使えなくてclassnamesで対応したので使わず...
```
$ npm install --save-dev babel-plugin-react-html-attrs
```

- JSXでclass定義のためにclassnamesをインストール
```
npm install --save-dev classnames
```

- @types/react-domが必要と言われたので、、、
```
$ npm install @types/react-dom
```

- @types/react-router-domが必要と言われたので、、、
```
$ npm install @types/react-router-dom
```

- @types/classnamesが必要と言われたので、、、
```
npm install @types/classnames
```

- babelでbind()を省略する際の記法で必要となったため、@babel/plugin-proposal-class-propertiesをインストール(.bind(this)関数の省略について)
```
$  npm install --save-dev @babel/plugin-proposal-class-properties
```

## 補足
### react-router-dom
react-router-domからインポート
#### Router,Route,Linkとは
Routerが親タグでRouteを作成。
Routeでpathとcomponentを紐づけ。
Linkで紐づけたconponentをpropsに入れますよ。みたいな感じかな？
- Router
  - Route
- Link
- NavLink

#### Route
pathに書かれた内容の時だけ表示を行う。componentに書かれた内容で動作を分けることができる。
exactをつけると完全一致。
pathに「:article」をつけると部分一致
pathに「:mode(main|extra)」をつけると、mainまたはextraの時のみ動作する。 => {this.props.match.params.mode}を使えるようになる。

#### Link
toで押下時のpathを指定することが出来る。

#### NavLink
Linkの拡張版みたいなイメージ。
activeClassNameをつけることで、active時にclassを変更できる。

#### withRouter
componentクラスに対して`export default withRouter(Layout);`のようにすると、
propsに「history,location,match,staticContext」等を持っている。
今回は履歴管理でhistory()で履歴を残している。
逆にreplace()を使うことで履歴が残らない。(※前のボタンの履歴)

### URLSearchParams
クエリパラメータを取得に使用。
これが使えないライブラリはquery-string等を使って対応。

