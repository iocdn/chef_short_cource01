# 初めてのgithubへの保存

## ssh鍵の生成
- cookbookが保存されているサーバにログインします。

```
local $ ssh xxx.xxx.xxx.xxx
```

- cookbookが保存されたサーバでsshの鍵を生成します。

```
$ ssh-keygen -t rsa -P ''
$ cat ~/.ssh/id_rsa.pub
 == ココで出力される ssh公開鍵 を 下記　ssh鍵登録で登録します。 ==
```

## chef-repoリポジトリの作成
- [GitHub](https://github.com ,GitHub)にログインして、chef-repoリポジトリを作成します。
  - New Repositoryを選択 
  
  ![image](/images/01_create_new_repository.png)

  - Repository name に "chef-repo"を入力し, Create repository を押下
  
  ![image](/images/02_create_new_repository.png)

## ssh鍵登録
- リポジトリが生成されたら、Settingsタブから Deploy keys を選択
  
  ![image](/images/03_add_ssh_pub_key.png)

-  Add deploy key を押下
 
  ![image](/images/04_add_ssh_pub_key.png)

- Titleに "test" , Keyに _ssh鍵の生成_ で生成したssh公開鍵を貼り付け, Allow write accessにチェックしAdd keyを押下

  ![image](/images/05_add_ssh_pub_key.png)
  
## 初めてのpush
- cookbookが保存されているサーバにログインします。

```
local $ ssh xxx.xxx.xxx.xxx
```

- git コマンドのインストール

```
$ sudo yum -y install git
```

-  git リポジトリの初期化

```
$ cd ~/chef-repo
$ git init
$ git config --global user.name username
$ git config --global user.email username@ap-com.co.jp
```
-  remoteリポジトリ(githubリポジトリの登録)

```
$ git remote add origin git@github.com:アカウント名/chef-repo.git
```

- cookbookのコミット

```
$ git init
$ git add ./*
$ git commit -m "initial commit"
```

- remoteリポジトリへのpush
```
$ git push origin master
```
