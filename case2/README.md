**AWS기초 및 활용** 

VPC 구성하기


# Dongjin AWS VPC TEST

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/VPC.PNG)

1. VPC 만들기.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/vpc_1.jpg)

VPC서비스에 들어와서 좌측의 VPCs메뉴를 클릭하여 들어오면 보이는 화면입니다. 이 화면에서 Create VPC버튼을 누르면 VPC를 생성할 수 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/vpc_2.jpg)

이 화면이 Create VPC를 클릭하여 들어온 화면입니다. 여기서 생성할 VPC의 이름과 CIDR대역을 입력하면 VPC를 생성할 수 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/vpc_3.jpg)

만들어진 VPC는 위와 같은 모습으로 확인할 수 있습니다.

2. Subnet 생성.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/sub_1.jpg)

VPC를 만들고 나면 Subnet을 생성할 차례입니다. 위 화면에서처럼 서브넷 메뉴로 들어가면 서브넷 생성 버튼을 확인할 수 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/sub_2.jpg)

그리고 서브넷의 이름과 서브넷이 생성될 위치(VPC), 가용영역을 선택하고 CIDR대역을 입력하면(VPC의 CIDR대역 내 범위를 입력해야 합니다) 서브넷이 생성됩니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/sub_3.jpg)

Subnet이 생성된 모습입니다.
