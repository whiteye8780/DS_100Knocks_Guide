# DS_100Knocks_Guide
データサイエンス100本ノック（構造化データ加工編）の環境構築ガイド  
  
# 実行環境
OS CentOS7  
IPアドレス  
192.168.0.10  
IPアドレスは各自で確認した上でインストールしてください  
  
  
# ROOTでログイン
su -
# インストールされているパッケージを更新
yum -y update

# 必要なパッケージのインストール
yum -y install git curl

yum install -y yum-utils device-mapper-persistent-data lvm2

# Docker-CEのインストール
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo

yum install -y docker-ce docker-ce-cli containerd.io

# docker-composeのインストール
curl -L https://github.com/docker/compose/releases/download/1.26.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose

docker-compose --version

# Dockerの起動
systemctl start docker

# 自動起動
systemctl enable docker

# インストールしたcバージョンの確認
docker --version

# リポジトリをクローンする
git clone https://github.com/The-Japan-DataScientist-Society/100knocks-preprocess

cd 100knocks-preprocess

docker-compose up -d --build

※特に移動しないのでrootのhomeディレクトリにクローンファイルを設置する

# コンテナの起動
docker start dss-notebook
docker start dss-postgres
# コンテナの自動起動
インストールした状態ではサービスが起動していないので、自動起動するようにする
docker update --restart=always dss-notebook
docker update --restart=always dss-postgres

# ブラウザでアクセス
http://192.168.0.10:8888

