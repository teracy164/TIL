# Vagrantfileとは

`vagrant init`で生成されるVM起動設定ファイル

## 各種設定
↓サンプル
```
Vagrant.configure("2") do |config|
  # contos/7というイメージを使用
  config.vm.box = "centos/7"
  # プライベートネットワークで、IPアドレスは「192.168.33.10」
  config.vm.network "private_network", ip: "192.168.33.10"
  
  # メモリサイズ設定
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  
  ####################################################################
  # ホスト（Windows）側で以下のプラグインをインストールしておくこと
  # 「vagrant plugin install vagrant-disksize」
  ####################################################################
  
  # ディスクサイズ設定
  config.disksize.size = '50GB'

  # 初回（もしくはvagrant provision実行時）のみ実行
  config.vm.provision :shell, :path => "provision/provision.sh"

  # 毎回実施
  # SELinuxを一時的に無効にしてSambaを再起動
  config.vm.provision :shell, run:"always", inline: "setenforce 0 && sudo systemctl restart smb nmb"
end

```

## VagrantのBOXイメージ
以下のサイトで利用可能なイメージを検索できる
https://app.vagrantup.com/boxes/search
