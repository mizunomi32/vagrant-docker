# Docker on Vagrant  
mac で快適にDockerを使うための環境

# 準備
## 開発対象のソースコードを配置する
一つ下の階層をVagrantにマウントするので親階層に開発対象のソースコードを配置する  
例: このドキュメントが/home/user/src/vagrant-dockerに配置してあればhome/user/srcに対象のソースコードを配置  

## Vagrantの環境を構築する

## nfsを有効化する(macの場合)
```
sudo touch /etc/exports
sudo nfsd enable
```

## Vagrantのプラグインを入れる
```
vagrant plugin install vagrant-vbguest
```

## vagrat up
仮想マシンの起動と構築を行う
```
vagrant up
```
## docker を起動する

```
vagrant ssh
```
ソースコードは~/srcに配置されるので移動しdockerコンテナを起動する

## ブラウザで開く
例: http://192.168.33.10:3000/