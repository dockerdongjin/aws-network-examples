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

5. 해당 도메인 주소를 클릭후에 들어오면 아래의 그림과 같이 설정되어져 있습니다. 여기서 __Type(타입) NS__ 부분에 설정된 4개의 __Value(값)__ 을 도메인을 신청한 호스팅 업체에 __네임서버__ 로 등록을 해줘야 합니다. 

![도메인등록6](https://github.com/dockerdongjin/aws-network-examples/blob/master/case1/img/case1-6.jpg)<br><br><br>
