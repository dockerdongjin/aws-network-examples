# ** AWS기초 및 활용 (도메인 등록) ** 

### Route53을 이용한 도메인 등록<br><br>

1. 아래의 그림과 같이 AWS로그인 후에 서비스 검색창에 'Route53'입력 후 검색된 내용 클릭.<br>

![도메인등록1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-1.jpg)<br><br><br>


2. DNS Management영역에 __Create Hosted Zone__ 버튼을 클릭합니다.<br>

![도메인등록2](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-2.jpg)<br><br><br>

3. DNS Management영역에 __Create Hosted Zone__ 버튼을 클릭후 들어간후에<br>
> Domain Name : 신청한 도메인 예) google.com 혹은 naver.com<br>
> Comment : 해당 도메인에 대한 설명글 (반드시 입력 X)<br>
> Type : Public Hosted Zone (기본값으로 두자)

![도메인등록3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-3.jpg)<br><br><br>
![도메인등록4](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-4.jpg)<br><br><br>

4. 등록된 __Hosted Zone__ 파일은 아래와 같습니다. 아래의 도메인명을 클릭하여 들어갑니다.<br> 

![도메인등록5](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-5.jpg)<br><br><br>

5. 해당 도메인 주소를 클릭후에 들어오면 아래의 그림과 같이 설정되어져 있습니다. 여기서 __Type(타입) NS__ 부분에 설정된 4개의 __Value(값)__ 을 도메인을 신청한 호스팅 업체에 __네임서버__ 로 등록을 해줘야 합니다.<br>

![도메인등록6](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-6.jpg)<br><br><br>

6. 도메인을 신청한 호스팅 업체의 사이트(예 : 가비아,까페24, 고도몰)로 이동하여 __서비스 관리__ 혹은 __마이페이지__ 메뉴로 이동하여 해당 도메인의 __네임서버__ 정보를 방금전 위쪽에서 확인한 4개의 값으로 각각 변경해줍니다.<br>

![도메인등록7](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-7-2.jpg)<br><br><br>
![도메인등록8](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-7.jpg)<br><br><br>

7. __Create Record Set__ 버튼을 클릭후 오른쪽에 새로운 레코드에 대한 정보를 입력합니다. <br>

+ __Name__ : __www__  자신의 도메인주소 앞에 www가 붙도록 설정하고자 하는 경우 사용합니다. 예) www.도메인주소
+ __Type__ : 기본적으로 __A - IPv4 Address__ 로 설정합니다.
+ __Value__ : 현재 도메인주소와 연결한 서버의 아이피 주소를 입력합니다.

![도메인등록8](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-8.jpg)<br><br><br>
![도메인등록8]https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-8.jpg<br><br><br>

8. 도메인 주소가 적용되기까지 약간의 시간이 필요합니다. 잠시 기다린 후에 브라우저를 실행후 등록한 도메인 주소를 입력해보신후 정상적으로 출력된다면 도메인 주소 등록이 완료됩니다. <br>



