# **AWS기초 및 활용 (VPC Peering) ** 

__VPC 피어링이란?__

VPC(Virtual Private Network)간에 트래픽을 라우팅 할수 있도록 하기 위한 두 VPC 사이의 네트워킹 기술이며.<br>
서로 다른 VPC에 통신이 기본적으로는 불가능하지만 피어링(Peering)을 이용하면 통신이 가능하게 됩니다.<br>

2개의 VPC를 생성후 피어링 설정전에 통신이 안되는 것을 확인하고, 피어링을 설정후 정상적으로 통신되는 모습을 확인하려고 합니다.

1. 피어링을 구성하기 위해서 2개의 __VPC영역을 생성__ 합니다. <br>

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-1.jpg)<br><br><br>
![구성2](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-2.jpg)<br><br><br>
![구성3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-3.jpg)<br><br><br>
![구성4](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-4.jpg)<br><br><br>
![구성5](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-5.jpg)<br><br><br>
![구성6](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-6.jpg)<br><br><br><br><br><br>


2. 구성한 2개의 __VPC__ 내에 __Subnet__ 을 각각 생성합니다.<br>

![구성7](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-8.jpg)<br><br><br>
![구성8](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-9.jpg)<br><br><br>
![구성9](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11.jpg)<br><br><br><br><br><br>

3. 생성된 VPC에 연결될 __인터넷 게이트웨이__ 를 2개 생성 후 해당 __VPC 연결__ 합니다.<br>

![구성10](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-1.jpg)<br><br><br>
![구성11](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-2.jpg)<br><br><br>
![구성12](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-3.jpg)<br><br><br>
![구성13](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-4.jpg)<br><br><br><br><br><br>

두번째 VPC도 인터넷 게이트웨이를 생성후 연결합니다<br>

![구성14](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-11.jpg)<br><br><br>
![구성15](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-12.jpg)<br><br><br><br><br><br>

4. 여기까지 구성후 VPC에 __라우팅 테이블__ 정보를 수정해야 하지만 아직 피어링이 설정되지 않은 상태이니 우선적으로 __EC2 인스턴스를 먼저 생성__ 후에 피어링 설정을 한 후에 라우팅 테이블을 수정하도록 하겠습니다. <br>
__EC2인스턴스__ 생성을 위해 이동 후 위에서 생성한 2개의 VPC 서브넷내에 각각 EC2인스턴스를 아래와 같은 형태로 생성합니다.

![구성17](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-12.jpg)<br><br><br>
![구성18](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-13.jpg)<br><br><br>
![구성19](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-14.jpg)<br><br><br>
![구성20](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-15.jpg)<br><br><br>
![구성21](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-16.jpg)<br><br><br>
![구성22](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-17.jpg)<br><br><br>
![구성23](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-18.jpg)<br><br><br>
![구성24](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-19.jpg)<br><br><br>
![구성25](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-20.jpg)<br><br><br><br><br><br>


5. EC2인스턴스 생성후에 4번에서 잠시 보류했던 __VPC 라우팅 테이블__ 수정을 하도록 하겠습니다.<br>
우선은 __피어링(peeriing)__ 이 적용되기 전 2 VPC가 서로 __Ping__ 이 되지 않는 형태를 보도록 하겠습니다. <br>
__(중요)__ 첫번째 VPC(peeringVPC-A)에 생성된 EC2인스턴스에 SSH접속이 가능하도록 __EIP(Elasitic IP)__ 를 설정하도록 하겠습니다.<br>
먼저 EIP를 하나 생성하기 위해서 아래 그림과 같이 실행해주세요.


![구성26](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-21.jpg)<br><br><br>
![구성27](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-22.jpg)<br><br><br>
![구성28](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-23.jpg)<br><br><br><br><br><br>

6. 생성된 __EIP__ 를 첫번째 VPC(peeringVPC-A)내에 생성된 EC2인스턴스에 등록합니다.<br>

![구성29](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-25.jpg)<br><br><br>
![구성30](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-26.jpg)<br><br><br>
![구성31](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-27.jpg)<br><br><br>
![구성32](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-28.jpg)<br><br><br><br><br><br>

6-2. 그리고 해당 EC2인스턴스에 접속하기 위하여 EC2인스턴스가 포함된 VPC의 __라우팅테이블__ 을 아래와 같이 0.0.0.0/0이 추가되도록 수정합니다.<br>

![구성32](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-8.jpg)<br><br><br><br><br><br>

7. EIP가 할당된 EC2인스턴스에 SSH프로그램을 이용하여 접속 후 2번째 VPC(peeringVPC-B)에 있는 EC2인스턴슨에 Ping을 보냅니다.<br>
Ping을 보냈을때 아래의 그림과 같이 핑에 대한 응답이 없음으로 표시되면 됩니다. (현재까지 두 VPC내에 EC2는 서로 통신이 되지 않는 상태입니다.)

![구성33](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-29.jpg)<br><br><br><br><br><br>

8. 서로 다른 VPC의 두 EC2인스턴스과 통신이 되도록 하기 위해서 __피어링(Peering)__ 설정을 하도록 하겠습니다.<br>
피어링을 생성하기 위해 아래 그림의 메뉴로 이동하여 피어링을 생성합니다.<br>

__VPC(요청자)* :__ peeringVPC-A<br>
__VPC(수락자)* :__ peeringVPC-B<br>


![구성34](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-31.jpg)<br><br><br>
![구성35](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-32.jpg)<br><br><br>
![구성36](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-33.jpg)<br><br><br>
![구성37](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-34.jpg)<br><br><br>
![구성38](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-35.jpg)<br><br><br><br><br><br>

8. 피어링(peering) 생성 후 __요청자--->수락자__ 수락자의 수락이 필요합니다. 수락을 위해서 아래의 그림과 같이 실행해주세요.<br>

![구성38](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-36.jpg)<br><br><br>
![구성38](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-37.jpg)<br><br><br>
![구성38](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-38.jpg)<br><br><br><br><br><br>

9. 피어링(peering) 요청과 수락이 완료되면 2개의 VPC에 라우팅테이블에 피어링을 이용한 통신이 가능하도록 라우팅테이블을 수정해야 합니다.<br>
우선 첫번째 VPC(peeringVPC-A) 라우팅 테이블을 아래의 그림과 같이 수정합니다.<br>

__10.7.0.0/16(peerginVPC-B)인 경우 Peering Connection을 이용하여 통신하도록 설정.__ <br>
__0.0.0.0/0(그외의 아이피)인 경우에는 해당 VPC의 인터넷 게이트웨이를 이용하여 통신하도록 설정.__ <br>

![구성39](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-14.jpg)<br><br><br>
![구성40](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-15.jpg)<br><br><br>
![구성41](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-16.jpg)<br><br><br>
![구성42](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-17.jpg)<br><br><br><br><br><br>

10. 두번째 VPC(peeringVPC-B) 라우팅 테이블을 아래와 같이 수정합니다.<br>

__10.6.0.0/16(peerginVPC-A)인 경우 Peering Connection을 이용하여 통신하도록 설정.__ <br>
__두번째 VPC는 외부(인터넷)연결이 필요없으므로 0.0.0.0/0은 설정하지 않습니다.__<br>

![구성43](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-18.jpg)<br><br><br>
![구성44](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-19.jpg)<br><br><br>
![구성45](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-20.jpg)<br><br><br><br><br><br>


11. 두 VPC의 라우팅 테이블 수정이 완료됐다면 다시 __peeringVPC-A의 EC2인스턴스__ 에서 __peeringVPC-B의 EC2인스턴스__ 에 Ping을 보내봅니다.<br>
ping을 보냈을때 이번에는 정상적으로 통신이 되야합니다. ^^


![구성46](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-39.jpg)<br><br><br>










