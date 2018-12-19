**AWS 로드밸런스** 
-----

구성하기


# 
서버 및 ELB 설정
-----
1)ELB 테스트를 위한 서버 A,B를 각각 생성해둡니다.
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/EC22.JPG?raw=true)

2)로드벨런서를 구성합니다.
![구성2](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/ELB_1.JPG?raw=true)

3)진행 중 대상등록에는 ELB가 적용되는 서버 A,B의 가용영역을 설정해 줍니다.
![구성3](https://raw.githubusercontent.com/dockerdongjin/aws-network-examples/master/case3/img/ELB_4_%EB%8C%80%EC%83%81%EB%93%B1%EB%A1%9D.JPG)

4)대상등록 완료되었습니다.
![구성4](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/ELB_5_%EB%93%B1%EB%A1%9D%EC%99%84%EB%A3%8C.JPG?raw=true)

5)설정확인
![구성5](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/ELB_con.JPG)


ROUTER53 설정
-----
1)ROUTER53메뉴에서 'Create HostsZone'을 클릭합니다. 
![구성6](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/router53_1.JPG)

2)ELB에서 생성된도메인 네임을 DNS도메인과 연결시킵니다.
![구성7](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/router53_2.JPG)

3)elb로 사용될 도메인이 생성된것을 확인합니다.
![구성8](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/router53_3.JPG)

web서버 설정
------

1)web A,B 아파치를 설치하고 index페이지를 구별하기 쉽게 설정합니다. 해당 웹서버 접근시 'SERVER A'라는 메시지가 나타납니다.
![구성9](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/webserver_3_a.JPG)

2)위의 방법과 마찬가지로  웹서버 접근 시 'SERVER B'가 나타나게 설정합니다. 
![구성10](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/webserver_3_b.JPG)


결과확인
------
ROUTER53에 설정한 DNS주소로 접근 시 serverA와 serverB가 Hash방식으로 동작하여 각각 번갈아가며 화면에 출력됩니다.
![구성10](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/webserver_3_%EA%B2%B0%EA%B3%BC%ED%99%95%EC%9D%B8.JPG)

![구성11](https://github.com/dockerdongjin/aws-network-examples/blob/master/case3/img/server_AB%EA%B2%B0%EA%B3%BC_2.JPG)
