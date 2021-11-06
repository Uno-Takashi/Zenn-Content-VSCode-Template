---
title: "VSCodeとDockerで作る再配布可能なZenn執筆環境（Remote Container+）"
emoji: "💬"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["zenn-cli","docker","VSCode","markdown","github"]
published: false
---

## zenn-cliめっちゃべんりですね

こんにちは。

最近Zennデビューしました、U-Notです。

Qiitaから移民して驚いたのですが、[Zenn CLI](https://zenn.dev/zenn/articles/install-zenn-cli)がめちゃめちゃ便利であると同時に、先駆者の皆様が志向を凝らした環境を色々と共有してくれていて、とてもありがたいです。

ただ、自由度の高さ故に、ある程度共通化されている設定を導入するだけでも結構大変なうえに、ローカル環境を汚しそうだと感じました。

なので、今回は[Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)を使って、再配布性、機能性、再現性に優れた環境の構築と配布します。

今回構築する環境には、以下の機能が含まれます。

- VSCodeでの実装
    - ほかのワークスペースを汚さないように配慮した設定ファイル
    - [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)を推奨拡張機能に設定
    - [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)を導入することでコンテナ立ち上げ時の手順の簡略化
    - 記事ファイルの作成コマンドをタスクとして容易に実行可能
    - markdown執筆に必要な拡張機能のインストールと設定
- textlintによる日本語の自動校正
- Dockerコンテナによって隔離された環境
    - Zenn-cliをインストール済み
    - textlintでローカルに必要なソフトのインストール済み
    - コンテナを立ち上げた瞬間自動でプレビュー用のサーバーを起動したままにする




## 参考文献

- [Developing inside a Container using Visual Studio Code Remote Development](https://code.visualstudio.com/docs/remote/containers)