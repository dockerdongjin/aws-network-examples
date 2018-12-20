# **AWS기초 및 활용 (VPC Peering) ** 

__VPC 피어링이란?__

VPC(Virtual Private Network)간에 트래픽을 라우팅 할수 있도록 하기 위한 두 VPC 사이의 네트워킹 기술입니다.

1. 피어링을 구성하기 위해서 2개의 __VPC영역을 생성__ 합니다. <br>

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-1.jpg)<br><br><br>
![구성2](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-2.jpg)<br><br><br>
![구성3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-3.jpg)<br><br><br>
![구성4](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-4.jpg)<br><br><br>
![구성5](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-5.jpg)<br><br><br>
![구성6](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-6.jpg)<br><br><br>

2. 구성한 2개의 __VPC__ 내에 __Subnet__ 을 각각 생성합니다.<br>

![구성7](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-8.jpg)<br><br><br>
![구성8](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-9.jpg)<br><br><br>
![구성9](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11.jpg)<br><br><br>

3. 생성된 VPC에 연결될 __인터넷 게이트웨이__ 를 2개 생성 후 해당 __VPC 연결__ 합니다.<br>

![구성10](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-1.jpg)<br><br><br>
![구성11](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-2.jpg)<br><br><br>
![구성12](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-3.jpg)<br><br><br>
![구성13](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-4.jpg)<br><br><br>

두번째 VPC도 인터넷 게이트웨이를 생성후 연결합니다<br>

![구성14](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-11.jpg)<br><br><br>
![구성15](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-12.jpg)<br><br><br>

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
![구성25](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-20.jpg)<br><br><br>


5. EC2인스턴스 생성후에 4번에서 잠시 보류했던 __VPC 라우팅 테이블__ 수정을 하도록 하겠습니다.<br>
우선은 __피어링(peeriing)__ 이 적용되기 전 2 VPC가 서로 __Ping__ 이 되지 않는 형태를 보도록 하겠습니다. <br>
__(중요)__ 첫번째 VPC(peeringVPC-A)에 생성된 EC2인스턴스에 SSH접속이 가능하도록 __EIP(Elasitic IP)__ 를 설정하도록 하겠습니다.<br>
먼저 EIP를 하나 생성하기 위해서 아래 그림과 같이 실행해주세요.


![구성26](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-21.jpg)<br><br><br>
![구성27](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-22.jpg)<br><br><br>
![구성28](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-23.jpg)<br><br><br>

6. 생성된 __EIP__ 를 첫번째 VPC(peeringVPC-A)내에 생성된 EC2인스턴스에 등록합니다.<br>

![구성29](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-25.jpg)<br><br><br>
![구성30](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-26.jpg)<br><br><br>
![구성31](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-27.jpg)<br><br><br>
![구성32](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-28.jpg)<br><br><br>

7. EIP가 할당된 EC2인스턴스에 SSH프로그램을 이용하여 접속 후 2번째 VPC(peeringVPC-B)에 있는 EC2인스턴슨에 Ping을 보냅니다.<br>
Ping을 보냈을때 아래의 그림과 같이 핑에 대한 응답이 없음으로 표시되면 됩니다. (현재까지 두 VPC내에 EC2는 서로 통신이 되지 않는 상태입니다.)

![구성33](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-29.jpg)<br><br><br>

8. 서로 다른 VPC의 두 EC2인스턴스과 통신이 되도록 하기 위해서 __피어링(Peering)__ 설정을 하도록 하겠습니다.<br>
피어링을 생성하기 위해 아래 그림의 메뉴로 이동하여 피어링을 생성합니다.<br>

>> 피어링 연결 이름 태그 : peeringVPC_A_B
>>

![구성34](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-31.jpg)<br><br><br>
![구성34](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-32.jpg)<br><br><br>

