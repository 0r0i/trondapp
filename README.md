# Tron API Server(express)



README

일반 정보

AUTHORS

제작 정보

THANKS	

도와주신 분들에 대한 정보

ChangeLog	

프로그래머들이 참고 할 수 있는 자세한 체인지로그

NEWS

사용자들이 참고할 수 있는 기본적인 체인지로그

INSTALL

설치 안내

COPYING/LICENSE

저작권 및 사용권 정보

BUGS

알려진 버그 및 새로운 버그 보고 방법 안내






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





