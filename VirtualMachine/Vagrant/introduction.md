# Vagrantとは

VirtualBOXを使いやすくするためのツール
イメージを使用したり、起動時にシェルを流し込む設定等ができる。
設定はVagrantfileというファイルに記載するため、これを共有することでチームで同じ環境を複製することが容易となる。

## よく使うコマンド
### vagrant init
Vagrant初期化  
→Vagrantfileが生成される。

### vagrant up
Vagrantfileに記載した内容に従ってVM起動

### vagrant halt
VM停止

### vagrant reload
VM再起動

### vagrant ssh
起動したVMにSSH接続を行う  
vagrantユーザーで接続する

### vagrant provision
Vagrantfileの変更をVMに反映する。

### vagrant box list
追加したBOMの一覧を表示

### vagrant box add {任意のbox名} {URLもしくはBOX名}
Vagrantfileでboxを指定していれば不要

### vagrant box remove {box名}

### vagrant package
現在のBOXをパッケージング。  
できた.boxファイルは`vagrant box add xxx.box`すれば取り込むことができる
