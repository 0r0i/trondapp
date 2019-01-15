# Tron API Server(express)

Tron-web 프로젝트 복사
---------------------
출처 : https://github.com/tronprotocol/tron-web 


root@tkpark-VirtualBox:~# pwd
/root
mkdir project
cd project
git clone https://github.com/tronprotocol/tron-web
cd tron-web/

  
Nodejs 설치
-----------
apt install curl
curl -sL https://deb.nodesource.com/setup_8.x | sudo bash -
node -v
npm -v
 
yarn 업데이트
------------
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -

echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

apt-get update && sudo apt-get install yarn

yarn -v
 
yarn 빌드
cd tron-web
yarn
yarn build -d
 
express 기본틀 만들기
yarn global add express 
yarn global add express-generator
 
yarn 심볼릭 링크
cd ~
mkdir bin
cd bin
ln -s /usr/share/yarn/bin/yarn
 
Myapp 제작
cd ~
cd project
express --view=pug myapp
cd myapp
yarn install
yarn add tronweb
yarn start


