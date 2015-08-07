# mt-devkit

## ディレクトリ構成

* `Vagrantfile` Vagrant用ファイル
* `playbook.yml` `files` `templates` Ansible用ファイル
* `www` VM内Webサイトのドキュメントルートへのリンク（VM起動中のみ）

## 用語の説明

* 作業用PC： あなたが操作しているPC・Mac
* 作業用VM： 作業用PC上に用意する、開発用Movable Typeを稼働させるための仮想マシン（Vagrantにより管理）
* 本番サーバー： 公開中のWebサイトが稼働しているサーバー

## 手順

### 1. 開発をはじめる

1. 作業用PC上にVagrant、vagrant-hostsupdaterをインストールしてください

2. Movable Typeのソースファイル（MT-6.1.2.zip）を取得し、Vagrantfileのあるディレクトリに配置してください

3. `vagrant up` を実行し、作業用VMを作成してください

4. 作業用VM上で開発を開始してください
    * http://mt-devkit.dev/mt/mt.cgi を開くと、初期設定が開始されます

