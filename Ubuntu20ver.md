# DS_100Knocks_Guide
データサイエンス100本ノック（構造化データ加工編）の環境構築ガイド  
  
# 実行環境
OS CentOS20LTS  
IPアドレス  
192.168.0.21  
IPアドレスは各自で確認した上でインストールしてください  

# インストールされているパッケージを更新
sudo apt -y update
# 必要なパッケージのインストール
sudo apt -y install git curl apt-transport-https software-properties-common  
# Docker の公式 GPG 鍵を追加します
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
# フィンガープリントの確認
sudo apt-key fingerprint 0EBFCD88  
  
9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88  
と表示されていることを確認する  
# リポジトリセットアップ
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
# 更新
sudo apt update  
sudo apt -y upgrade  
# Dockerのインストール
sudo apt install -y docker-ce docker-ce-cli containerd.io

#docker-composeのインストール

sudo curl -L https://github.com/docker/compose/releases/download/1.26.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose  

sudo chmod +x /usr/local/bin/docker-compose  

docker-compose --version  


# Dockerの起動
sudo systemctl start docker
# 自動起動
sudo systemctl enable docker
# インストールしたバージョンの確認
docker --version

# リポジトリをクローンする
git clone https://github.com/The-Japan-DataScientist-Society/100knocks-preprocess  
cd 100knocks-preprocess  
sudo docker-compose up -d --build  
※マシンスペックにもよりますが10分以上かかりました。    
※特に移動しないのでログインしたユーザのhomeディレクトリにクローンファイルを設置する  
# コンテナの起動
sudo docker start dss-notebook  
sudo docker start dss-postgres  
# コンテナの自動起動
sudo docker update --restart=always dss-notebook  
sudo docker update --restart=always dss-postgres  
