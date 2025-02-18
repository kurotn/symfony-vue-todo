## インストール～ Vue コンポーネントでの HelloWorld まで

### プロジェクト作成

https://symfony.com/doc/6.4/setup.html

```sh
symfony symfony-vue-todo --version="6.4.*"
```

### Webpack Encore インストール

https://symfony.com/doc/6.4/frontend/encore/installation.html

```sh
composer require symfony/webpack-encore-bundle
```

package.json ができるので、js 用のパッケージをインストール。

```sh
npm install
```

### Symfony UX Vue.js をインストール

https://symfony.com/bundles/ux-vue/current/index.html#installation

```sh
composer require symfony/ux-vue
```

### 追加で Vue.js のパッケージをインストール

```sh
npm install vue@^3.2.14 vue-loader@^17.0.0 @vue/compiler-sfc --save-dev
```

### assets をビルド

```sh
npm run dev

# 継続してwatchするなら
npm run watch
```

### base.html.twig を編集

head タグ内に以下を追加。
これにより、ビルドされた assets のファイルが参照できるようになる。
※つまり Vue のコンポーネントなども参照できるようになる。

```twig
    {{ encore_entry_link_tags('app') }}
    {{ encore_entry_script_tags('app') }}
```

### サーバーに Controller と Twig ファイルを用意しサーバーを起動

新規に適当な Twig ファイルを作成。
`base.html.twig`を継承し、コンポーネントを展開したい場所に以下を含める。

```twig
<div {{ vue_component('Hello', {'name': username}) }} ></div>
```

これにより、対象の要素に Vue コンポーネントがマウントされる。
あとは Controller を作成し、上記の処理を入れたコントローラーを作成。
ここまでできれば、あとはサーバーを起動してブラウザから表示すれば OK。

## 起動方法

```sh
./up.sh
npm run watch
```
