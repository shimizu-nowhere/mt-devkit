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

1. 作業用PC上に[Vagrant](https://www.vagrantup.com/)、[vagrant-hostsupdater](https://github.com/cogitatio/vagrant-hostsupdater)、[Ansible](http://www.ansible.com/)をインストールしてください
    * Ansibleは、OSXでは `brew install ansible` でインストール可

2. Movable Typeのソースファイル（MT-6.1.2.zip）を取得し、Vagrantfileのあるディレクトリに配置してください

3. `vagrant up` を実行し、作業用VMを作成してください

4. 作業用VM上で開発を開始してください
    * http://mt-devkit.dev/mt/mt.cgi を開くと、初期設定が開始されます

## 注意点

* MySQLのrootパスワードは設定されません。

## 参考

* [VagrantのCentOS6.5にAnsibleでMovable Typeを入れる - the code to rock](http://note103.hateblo.jp/entry/2015/04/17/010528)
* [Ansible - Provisioning - Vagrant Documentation](http://docs.vagrantup.com/v2/provisioning/ansible.html)
* [ApacheのAddHandlerはセキュリティ上の懸念から使用すべきではない - Dマイナー志向](http://d.hatena.ne.jp/tmatsuu/20150221/1424531513)
