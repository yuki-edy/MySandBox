
# 0. 想定環境
- Git
- GitHub
- VSCode

# 1. 環境構築

## 1.1. Gitのインストール・初期設定

インストールされたかどうかを確認する。
```bash
git --version
```

### configファイルに名前とアドレスを設定する
- これによって、pushした際に誰がpushしたかをGitHub側が判別できる。

```bash
git config --global user.name "Firstname Lastname"
git config --global user.email "my_email@example.com"
```

### デフォルトブランチ名を設定する
```bash
git config --global init.defaultBranch main
```

### 文字化け対策
```bash
git config --global core.quotepath false
```


上記の設定が反映されているか、グローバルの構成(config)情報を確認する。


```bash
git config --global --list
```

以下のコマンドで接続テストする。

```bash
ssh -T git@github.com
```

## 1.2. GitHubのアカウント作成

## 1.3. ローカル環境とGItHubとのSSH接続


SSHキーがあるかを確認する。
```bash
ls ~/.ssh
```

- すでにある場合の出力例。
- .pubは公開鍵を意味する。.pubがついていない方は**必ずローカル環境の中に保管しておく**。
```text
id_ed25519
id_ed25519.pub
```

鍵がない場合は、次の方法で作成できる。
- ed25519は暗号の種類
- ""の中には正しいアドレスを入れる。
  
```bash
ssh-keygen -t ed25519 -C "My_GitHub_Account_Adress@github"
```


試しに確認。

※とあるユーザーが作ったMySandBoxというレポジトリをクローンしてみる

```
git clone https://github.com/（ユーザー名）/MySandBox.git
```

## 1.4. VSCodeのインストール/各種設定





## 1.5. VSCodeとの連携

- ターミナルからレポジトリ指定でVSCodeを立ち上げないとSSH認証が通らない？
- VSCodeからターミナルを開くことができる


# 2. 用語の意味

# 3. 基本的な操作

## 3.1. cloneからpushまでの流れ

## 3.2. pull requestの使い方

## 3.3. branchの切り方/mergeの仕方

# X. 注意点

## SSHの秘密鍵をリモート環境（GitHub上など）に置かない

## ファイル名を変更する際は、git mvを使用する


# XX. その他Tips

## commitは差分単位のみでしか扱われない


# XXX. 今後の追加調査／勉強事項
- pull request時の承認フロー
- CIの導入
- テストコードの考え方（どこまでのテストを用意するべきか）
- mermaid(UMIツール)の導入
