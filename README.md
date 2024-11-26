# AppFrameReadme
AppFrame を使用した作品の説明サンプル  
(この段落は使用しない)

# 作品タイトル名(自身の作品名)
DX ライブラリと C++ 言語で作成した 3D ハイスピードシューティングゲーム

# 開発環境
Windows 11  
Visual Studio Community 2022

# 使用ライブラリ
[DX ライブラリ](https://dxlib.xsrv.jp/)  
[nlohmann-json](https://github.com/nlohmann/json)

# プロジェクト構成と起動方法
下記 DxLib ディレクトリ内に [DX ライブラリ Windows版 VisualStudio(C++)用](https://dxlib.xsrv.jp/DxLib/DxLib_VC3_24d.zip) を DownLoad して解凍後の ***プロジェクトに追加すべきファイル_VC用*** ディレクトリの内容を全てコピーします。
<details>
<summary>ディレクトリ詳細</summary>
<pre>
.
├── DxLib(ライブラリ用ディレクトリ)
│
├── AppFrame(自作ゲームフレームワーク用のライブラリ Project)
│   │
│   ├── AppFrame
│   │   │
│   │   └── Source(ソースファイル)
│   │
│   └── AppFrame.sln(Game.sln の方を起動して下さい)
│
└── Game(ゲーム本体の Project)
    │
    ├── Game
    │   │
    │   ├── Res(ゲーム用リソースディレクトリ)
    │   │
    │   └── Source(ソースファイル)
    │
    └── Game.sln(こちらを起動して下さい)
</pre>
</details>

# AppFrame フレームワーク概要
ゲームを作成する上で定形的に必要となる機能をまとめたフレームワーク  
Static Library の形式で提供(Project 設定)

### ApplicationBase
DX ライブラリを用いた Windows アプリケーションを作成する基底クラス  
本クラスを継承したクラスを作成すれば最小のコードでアプリのメイン部分を記述出来る

### ModeBase / ModeServer
本フレームワークはモードと呼ぶ単位でプログラミング可能になっており、モードを切り替える機能も提供します。  
これによりアプリ作成者は、モード単位の実装をする事でゲームのフローを構築出来ます。  

ModeBase を継承したクラス単位でタイトルやインゲーム、設定画面など好きな単位で構築でき  
ModeServer が各モードを切り替える機能を提供します。

# ゲーム設計概要
ゲーム内の全ての物が ObjectBase 継承して作成された OOP で作成されています。  
- 3D モデル
  - プレイヤー機体
  - エネミー
  - 配置物
  - 地形
- 2D UI
- エフェクト

これらを ObjectServer クラスで管理してオブジェクトプールを実現しています。
