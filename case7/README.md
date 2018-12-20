# **AWS기초 및 활용 (VPC Peering) ** 

__VPC 피어링이란?__

VPC(Virtual Private Network)간에 트래픽을 라우팅 할수 있도록 하기 위한 두 VPC 사이의 네트워킹 기술입니다.


1. 피어링을 구성하기 위해서 2개의 VPC영역을 생성합니다. <br>

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-1.jpg)<br><br><br>
![구성2](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-2.jpg)<br><br><br>
![구성3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-3.jpg)<br><br><br>
![구성4](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-4.jpg)<br><br><br>
![구성5](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-5.jpg)<br><br><br>
![구성6](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-6.jpg)<br><br><br>

2. 구성한 2개의 VPC내에 Subnet을 각각 생성합니다.<br>

![구성7](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-8.jpg)<br><br><br>
![구성8](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-9.jpg)<br><br><br>
![구성9](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11.jpg)<br><br><br>

3. 생성된 VPC에 연결될 인터넷 게이트웨이를 2개 생성 후 해당 VPC 연결합니다.<br>

![구성10](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-1.jpg)<br><br><br>
![구성11](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-2.jpg)<br><br><br>
![구성11](https://github.com/dockerdongjin/aws-network-examples/blob/master/case7/img/case7-11-3.jpg)<br><br><br>
<hr>


