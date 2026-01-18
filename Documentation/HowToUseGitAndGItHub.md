
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

## 1.2. GitHubのアカウント作成

## 1.3. ローカル環境とGItHubとのSSH接続

SSH接続を確立するためには、ローカルで発行したSSHキーに対して、
- SSHエージェント
- Gitのconfigファイル
- GitHub（公開鍵のみ）
の3者が認識できる状態にする必要がある。

### SSHキーの確認

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
### SSHキーの作成

鍵がない場合は、次の方法で作成できる。
- ed25519は暗号の種類
- ""の中には正しいアドレスを入れる。
  
```bash
ssh-keygen -t ed25519 -C "My_GitHub_Account_Adress@github"
```
この際に、鍵の名前やパスワードを設定する。
以下、鍵の名前はmykeyとする


### SSHエージェントでの有効化

sshエージェントを起動して、秘密鍵を有効化する。

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/mykey
```

不安であれば、SSHキーがあるかを再度確認する。
```bash
ls ~/.ssh
```
ここに、先ほど作成したmykeyがあればOK。

### Gitのconfigファイルへの追加



### GitHub上への公開鍵の設定

公開鍵を表示する

```bash
cat ~/.ssh/mykey.pub
```
これで表示した公開鍵をGitHub上に登録する。

以下のコマンドでssh接続テストする。

```bash
ssh -T git@github.com
```

試しに確認。

※とあるユーザーが作ったMySandBoxというレポジトリをクローンしてみる

```
git clone https://github.com/（ユーザー名）/MySandBox.git
```

これで、MySandBoxが確認されていればクローン成功。


## 1.4. VSCodeのインストール/各種設定





## 1.5. VSCodeとの連携

- ターミナルからレポジトリ指定でVSCodeを立ち上げないとSSH認証が通らない？
- VSCodeからターミナルを開くことができる


# 2. 用語の意味

### ステージ

コミットする前に一時的な領域のこと。
また、ステージ領域に登録することをステージングと言う。

### クローン

### コミット
ステージ領域に登録されている時点のファイル群を、リポジトリの変更履歴として記録すること。

### プッシュ
コミットした変更内容をリモートリポジトリに送信すること。

### プル
リモートリポジトリに反映された他のユーザーなどの最新の変更内容を自分のローカルリポジトリに反映すること。

### プルリクエスト






# 3. 基本的な操作

## 3.1. cloneからpushまでの流れ



## 3.2. pull requestの使い方

## 3.3. branchの切り方/mergeの仕方

# X. 注意点

## SSHの秘密鍵をリモート環境（GitHub上など）に置かない

## ファイル名を変更する際は、git mvを使用する


# XX. その他Tips

## commitは差分単位のみでしか扱われない

## 特定のcommitに対してtagを与えることでリリースバージョンとして管理できる

まず、commitのログを確認する。

```bash
git log --oneline
```

各コミットにはコミットID(SHA-1ハッシュ形式)が与えられているので、タグをつけたいコミットのコミットIDを特定する。
例えば、そのコミットIDがxyzabcの場合、

```bash
git tag -a v1.0.0 xyzabc -m "特定コミットに対してタグをつける"
```

とすれば、該当のコミットにバージョン名をつけることが可能になる。


# XXX. 今後の追加調査／勉強事項
- pull request時の承認フロー
- CIの導入
- テストコードの考え方（どこまでのテストを用意するべきか）
