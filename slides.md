---
theme: seriph
themeConfig:
  primary: '#FF9800'
fonts:
  sans: 'Noto Sans Japanese'
  mono: 'Fira Code'
background: /images/2024-01-21-08-24-30.png
colorSchema: 'dark'
lineNumbers: true
hideInToc: true
---

# <logos-flutter /> **Flutter を知ろう** <logos-flutter />


---
layout: cover
background: /images/cover.jpg
class: 'text-start'
hideInToc: true
---

# 目次

<Toc />

---

# はじめに
<br/>

Flutter 初めての方向け 🔰

Flutter ってこんなものって言うのを話します

## 話さないこと 🙅‍♂️

⚙️環境構築、🛠️具体的な実装方法、👍ベストプラクティス的なこと


---
class: 'bg-no-repeat bg-contain bg-right bg-[url(/images/build_multi_platform.png)]'
---

# Flutter とは？

<div class="flex flex-row">
  <div class="basis-1/2">
    <p>
      1つのコードベースからマルチプラットフォームのアプリケーションを構築するためのフレームワーク
    </p>
    <p>
      iOS、Android、Mac、Linux、Windows、Web<br />
      これらのアプリケーションを1つのコードベースからビルドできる
    </p>
    <p>開発言語として Dart を採用している</p>
    <h2>Dart とは</h2>
    <p>Google が開発・公開したプログラミング言語</p>
    <p>Java や JavaScript に似た文法で、JavaScript、Java、C#、Swift などの経験者にとっては馴染みやすいものになっている</p>
  </div>
</div>

<!-- 
Dart は今でこそバージョンアップを重ねていい感じに書けるようになっていますが、Flutter バージョン 1 くらいのころは言語機能が弱くて書きにくかった
-->

---

# Flutter 使うと何が嬉しいの？<mdi-hail />
<br/>

1. 1つのコードからマルチプラットフォームのアプリを構築できる
2. 複数のプラットフォーム向けにビルドされ、あらゆるデバイスで高速に動作する
3. 独自UIで構築されているため、複数のプラットフォームで同じ見た目を実現できる
4. UIを作るためのパーツが揃っており、それらを組み合わせることで凝ったUIを簡単に作成できる
5. Hot Reload / Hot Restartにより高速に実装を進めることができる
6. エディタのサポートが手厚く、開発ツールも充実しており開発を進めやすい

<!-- 
Google という大きいところが開発・サポートしているため将来性もある   
コミュニティも大きく、今後さらに盛り上がってくると予想される
-->

---
layout: section
hideInToc: true
---

# とは言っても 🚢

---
hideInToc: true
---

# クロスプラットフォームのフレームワークは他にもある
## `React Native`
## `.NET MAUI` 
## `Cordova`
## `Ionic`
## `Kotlin Multiplatform`

<!-- 
既存の資産とかスキルを鑑みて、それぞれのフレームワークを検討してみるのも良いと思う  
ここでは他のフレームワークの比較はせず Flutter のことだけ話す
-->

---

# Flutter ではどうやってUIを作るの？

## Flutter では UI を構築するパーツはすべて `Widget` と呼ぶ
<br/>

### この `Widget` をツリー状に組み合わせることで様々なUIを構築できる

<!-- 
ツリー上に組み合わせるってどうゆうこと？  
コードやFlutter Outlineを見ることでわかる
-->

---

<div class="flex flex-row">
  <div class="basis-1/2">
    <img src="/images/K8AIGF006914VAB-2024_01_21_10_03_55.png" class="h-130">
  </div>
  <div class="basis-1/2">
    <h1>例えばこんな画面</h1>
    Flutter プロジェクト作成時のデモアプリ
  </div>
</div>

---
class: 'bg-slate-900 bg-no-repeat bg-contain bg-center bg-[url(/images/nest.png)]'
---

---
hideInToc: true
---

# コードだと
```dart {all|2-4|4|6-19|7-18|10-16|20-24|all}
Scaffold(
  appBar: AppBar(
    backgroundColor: Theme.of(context).colorScheme.inversePrimary,
    title: Text(widget.title),
  ),
  body: Center(
    child: Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        const Text(
          'You have pushed the button this many times:',
        ),
        Text(
          '$_counter',
          style: Theme.of(context).textTheme.headlineMedium,
        ),
      ],
    ),
  ),
  floatingActionButton: FloatingActionButton(
    onPressed: _incrementCounter,
    tooltip: 'Increment',
    child: const Icon(Icons.add),
  ),
);
```

---

# どんな Widget がある？

- Container
- Text
- Image
- Icon
- ElevatedButton
- Row
- Column
- ListView
- etc...

[Widget catalog](https://docs.flutter.dev/ui/widgets)でも色々な Widget が紹介されている

---
layout: section
hideInToc: true
---

# Container

## その名の通りコンテナ
サイズやパディング、色など様々なプロパティを指定できる便利な Widget

---
layout: iframe
url: https://dartpad.dev/?id=52f557403c0323de125b37d5a9166df0
---

---
layout: section
hideInToc: true
---

# Text

## 文字を表示する Widget
文字を表示するならこれ

---
layout: iframe
url: https://dartpad.dev/?id=276330937aafa6eb36b5e5923488b452
---

<!-- 
もちろん画像とか普通に表示しますよね  
それ用のWidgetもあります
-->

---
layout: section
hideInToc: true
---

# Image

## 画像を表示する Widget
ローカル画像でもネットワーク上の画像も表示できる<br/>
何だったらバイト配列からでも表示できる

---
layout: iframe
url: https://dartpad.dev/?id=fe1b42d57995049a12129b7a858bb260
---

<!-- 
文字ばかりだと退屈ですよね  
ちょっとアイコンとか入れていい感じにしましょう
-->

---
layout: section
hideInToc: true
---

# Icon

## アイコンを表示する Widget

[Material Icon](https://fonts.google.com/icons)を表示できる

アプリで使うアイコンならだいたい揃っている

---
layout: iframe
url: https://dartpad.dev/?id=e38273c8dde2b9dd88bb9d60e663b4c5
---

<!-- 
アプリには普通にあるボタン  
簡単に作れます
-->

---
layout: section
hideInToc: true
---

# ElevatedButton

## マテリアルデザインのボタン


---
layout: iframe
url: https://dartpad.dev/?id=9224fcdb983676949daa0db528ba9055
---

<!-- 
Widgetを縦横に並べたい？  
Widget 一つ挟むだけでできるよ
-->

---
layout: section
hideInToc: true
---

# Row / Column

## 行（Row）、列（Column）に Widget を並べるWidget

---
layout: iframe
url: https://dartpad.dev/?id=f36aa2b14ca099d8dfa582a152259d21
---

<!-- 
API で取得したデータを一覧で表示することありますよね  
ListView を使って動的にWidgetを作って表示しましょう
-->

---
layout: section
hideInToc: true
---

# ListView

## Widget を縦または横に配置し、スクロール可能なリストを作成するための Widget
ちなみに、ColumnやRowは単体だとスクロール不可

---
layout: iframe
url: https://dartpad.dev/?id=5e7c47a2025af950ae92aad4a209cf7f
---

---
layout: section
hideInToc: true
---

# どんな `Widget` があるのかはわかった

---
layout: section
hideInToc: true
---

# 自分で `Widget` 作りたいんだけど
## 複数画面で使うボタンやレイアウトなど…

---

# Widget を作るには？

## 基本的には下記 2 つのいずれかを継承して Widget を作成する
<br/>

- `StatelessWidget`
- `StatefulWidget`

名前の通り状態を持つ Widget と持たない Widget

---
layout: section
class: "text-center text-6xl"
---

<emojione-thinking-face/>

<!--
状態を持つとか持たないWidgetとは何か？
-->

---
layout: section
hideInToc: true
---

# カウンターサンプルアプリを参考に `StatefulWidget` を見てみる

---
layout: iframe
url: https://dartpad.dev/?id=e75b493dae1287757c5e1d77a0dc73f1
---

<!-- 
状態とはカウンターアプリでいうと、何回押されたかという回数のこと  
回数を保持して、ボタンが押されたときに数をインクリメントし、画面へ範囲する必要がある  
StatefulWidget は Widget 単体で状態を保持し、更新し表示へ反映するという用途に使用する
-->

---
layout: two-cols
hideInToc: true
---

### カウンターアプリのコード

```dart {all|1|10|13-20|all}
class MyHomePage extends StatefulWidget {
  final String title;

  const MyHomePage({
    super.key,
    required this.title,
  }) : super();

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    ...
  }
}
```

<!-- 
まず最初の行、StatefulWidgetを継承してWidgetを作っています  
そして、createState関数をオーバーライドして_MyHomePageStateを返しています 
これがこのWidgetの状態で、Widgetはこの状態を保持時続けます  
_MyHomePageStateを見てみると、メンバー変数としてintの変数を持っています 
これが画面に表示されるカウンターの数ですね  
_incrementCounterがボタン押されたときに実行される処理ですが、その中で実行している処理が重要 
setStateという関数を実行しています  
で、その中で_counterをインクリメントしています  
このsetStateという関数を実行することにより、状態が更新されたことをWidgetに通知し、Widgetが新しい状態を元に作り直されることで表示が更新される  
setStateを実行しないと、_counterはインクリメントされますが、状態更新を通知していないので、Widgetは更新されず表示は変わらなくなります
-->

---
layout: section
hideInToc: true
---

# `StatelessWidget` は状態を持たない分簡素になる

## 基本的に渡されたものを表示するだけ

---
layout: two-cols
hideInToc: true
---

```dart {all|1|2-13|15-27|all}
class IconList extends StatelessWidget {
  const IconList({
    super.key,
    this.icons = const [],
    this.iconsSize = 24,
    this.iconColor = Colors.black,
  });

  final List<IconData> icons;

  final double iconsSize;

  final Color iconColor;

  @override
  Widget build(BuildContext context) {
    return Row(
      children: icons
          .map(
            (e) => Icon(
              e,
              size: iconsSize,
              color: iconColor,
            ),
          )
          .toList(),
    );
  }
}
```

---
hideInToc: true
---

## こんな感じで標準で用意されているWidgetと同じように使える

```dart
IconList(
  icons: [Icons.back_hand, Icons.cable, Icons.dashboard, Icons.eco],
  iconColor: Colors.green,
  iconSize: 36,
)
```

---
layout: iframe
url: https://dartpad.dev/?id=580abdc6d9ae8cda43d0f7b8aeabeaf3
---

---

# Flutter での状態管理
<br/>

Flutter では状態管理が重要

手法として下記のようなものがある
- `StatefulWidget` の `setState`
- `Provider`
- `Riverpod`
- `GetX`
- `get_it`
- `flutter_bloc（BLoCパターン）`

### `StatefulWidget` について
状態の数が十分に少なく、規模が小さい Widget の場合は有用

しかし、ほとんどは他の状態管理手法を用いられることが多い

---

# Flutter のパッケージ・プラグインについて
<br/>

Flutter は外部パッケージを使用してアプリの機能を拡張することが可能<br/>
Flutter 本体に組み込まれていないような便利な Widget などが多数公開されており、それらを使用して開発効率を上げられる

また、それぞれの OS の機能（カメラ等）を使用する場合はそれぞれの OS のネイティブコードを書く必要があるが、それらネイティブ機能のプラグインも公開されている<br/>
そのおかげで自分でネイティブコードを書くことはあまりない

[pub.dev](https://pub.dev/)からパッケージを検索・導入できる

---

# おわりに

## Widget の種類が多く、すべてを把握するのは難しいですが
## その分 `Hot Reload` があるので爆速で試行錯誤できます
<br/>

## いろんな Widget を組み合わせてレイアウト作るのは楽しいので、どんな Widget があるのか見てみて、ちょっと試したりすると面白いかも
<br/>

### 公式が出している[Flutter Widget of the Week](https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG)は、動画で Widget を紹介していて分かりやすいので、是非見てみてください！

---
layout: end
hideInToc: true
---

# END

---

# Appendix
<br/>

[Container example](https://dartpad.dev/?id=52f557403c0323de125b37d5a9166df0)  
[Text example](https://dartpad.dev/?id=276330937aafa6eb36b5e5923488b452)  
[Image example](https://dartpad.dev/?id=fe1b42d57995049a12129b7a858bb260)  
[Icon example](https://dartpad.dev/?id=e38273c8dde2b9dd88bb9d60e663b4c5)  
[Elevated Button example](https://dartpad.dev/?id=9224fcdb983676949daa0db528ba9055)  
[Row Column example](https://dartpad.dev/?id=f36aa2b14ca099d8dfa582a152259d21)  
[ListView example](https://dartpad.dev/?id=5e7c47a2025af950ae92aad4a209cf7f)  
[Counter example](https://dartpad.dev/?id=e75b493dae1287757c5e1d77a0dc73f1)  
[StatelessWidget example](https://dartpad.dev/?id=580abdc6d9ae8cda43d0f7b8aeabeaf3)  

[pub.dev](https://pub.dev/)  
[Material Icon](https://fonts.google.com/icons)  
[Widget catalog](https://docs.flutter.dev/ui/widgets)  
[Flutter Widget of the Week](https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG)  
