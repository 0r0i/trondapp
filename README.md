# Tron API Server(express)



README
========
TronWeb으로 Dapp 개발에 처음 입문 하시는분들의 도움을 주기 위해 위해서 코드를 배포




QUOTE	
========
https://github.com/tronprotocol/tron-web 

https://developers.tron.network/v3.0/reference#tronwebapi

https://shasta.tronscan.org/#/






INSTALL
========
개발환경 
---------------------

OS : Ubuntu 18.04(ubuntu-18.04.1-desktop-amd64.iso)

MariaDB : ubuntu0.18.04.1 

VM : VirtualBox-5.1.38-122592-Win.exe




Tron-web 프로젝트 복사
---------------------
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
------------
cd tron-web

yarn

yarn build -d

 
express 기본틀 만들기
--------------------------
yarn global add express 

yarn global add express-generator

 
yarn 심볼릭 링크
--------------------------
cd ~

mkdir bin

cd bin

ln -s /usr/share/yarn/bin/yarn
 
Myapp 제작
--------------------------
cd ~

cd project

express --view=pug myapp

cd myapp

yarn install

yarn add tronweb

yarn start



database 스키마
--------------------------

CREATE TABLE `transactionscan` (

  `idx` int(11) NOT NULL AUTO_INCREMENT,
  
  `from_address` varchar(100) NOT NULL COMMENT '보내는 사람 주소',
  
  `to_address` varchar(100) NOT NULL COMMENT '받는 사람  주소',
  
  `amount` bigint(20) NOT NULL COMMENT '양',
  
  `txid` varchar(150) NOT NULL COMMENT '트랜젝션 id',
  
  `regdate` datetime default current_timestamp,
  
  PRIMARY KEY (`idx`)
  
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='트랜젝션 조회 테이블';




MariaDB [tkpark]> desc transactionscan;

+--------------+--------------+------+-----+-------------------+----------------+

| Field        | Type         | Null | Key | Default           | Extra          |

+--------------+--------------+------+-----+-------------------+----------------+

| idx          | int(11)      | NO   | PRI | NULL              | auto_increment |

| from_address | varchar(100) | NO   |     | NULL              |                |

| to_address   | varchar(100) | NO   |     | NULL              |                |

| amount       | bigint(20)   | NO   |     | NULL              |                |

| txid         | varchar(150) | NO   |     | NULL              |                |

| regdate      | datetime     | YES  |     | CURRENT_TIMESTAMP |                |

+--------------+--------------+------+-----+-------------------+----------------+

실행방법
--------------------------
root@tkpark-VirtualBox:~/project/myapp/routes# pwd
/root/project/myapp/routes

index.js를 github소스로 변경 후 

root@tkpark-VirtualBox:~/project/myapp/routes# yarn start
yarn run v1.12.3
$ node ./bin/www

Crome 브라우저 실행


계좌신청

http://192.168.0.118:3000/createAccount/

잔액조회 지갑주소 

http://192.168.0.118:3000/getBalance/지갑주소

http://192.168.0.118:3000/getBalance/지갑주소


송금

http://192.168.0.118:3000/sendToken?PK=개인키&value=1000000&toAddress=지갑주소

PK, value, toAddress


트렌젝선 조회

http://192.168.0.118:3000/transactionview/지갑주소

http://192.168.0.118:3000/transactionview/지갑주소


트랜젝션 조회는 현재 TronWeb API함수가 업데이트로 인해 동작을 하지 않아

송금한 txid를 DB에 넣고 조회하는 형식으로 구현




COPYING/LICENSE
========
GNU Lesser General Public License, version 3 (SPDX short identifier: LGPL-3.0)




BUGS
========



