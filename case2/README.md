# **AWS기초 및 활용** 

### VPC 구성하기

> 1. VPC 만들기.
> 2. Subnet 만들기.
> 3. 인스턴스 만들기.
> 4. 인터넷 게이트웨이 만들기.
> 5. 라우팅 테이블 편집.



### 1. VPC 만들기.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/vpc_1.jpg)

VPC서비스에 들어와서 좌측의 VPCs메뉴를 클릭하여 들어오면 보이는 화면입니다. 이 화면에서 Create VPC버튼을 누르면 VPC를 생성할 수 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/vpc_2.jpg)

이 화면이 Create VPC를 클릭하여 들어온 화면입니다. 여기서 생성할 VPC의 이름과 CIDR대역을 입력하면 VPC를 생성할 수 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/vpc_3.jpg)

만들어진 VPC는 위와 같은 모습으로 확인할 수 있습니다.<br><br>

### 2. Subnet 생성.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/sub_1.jpg)

VPC를 만들고 나면 Subnet을 생성할 차례입니다. 위 화면에서처럼 서브넷 메뉴로 들어가면 서브넷 생성 버튼을 확인할 수 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/sub_2.jpg)

그리고 서브넷의 이름과 서브넷이 생성될 위치(VPC), 가용영역을 선택하고 CIDR대역을 입력하면(VPC의 CIDR대역 내 범위를 입력해야 합니다) 서브넷이 생성됩니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/sub_3.jpg)

Subnet이 생성된 모습입니다.<br><br>

### 3. 인스턴스 만들기

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/ec2_1.jpg)

이제 인스턴스를 만들 차례로 서비스에 EC2 메뉴로 이동하여 좌측의 인스턴스 메뉴로 이동한 모습입니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/ec2_2.jpg)

인스턴스 시작 버튼으로 들어온 화면이며 위에 형광펜으로 표시된 항목들을 진행하여 인스턴스를 생성할 수 있습니다.
그중 인스턴스 구성 항목에서는 전에 만든 VPC와 서브넷을 선택하여 인스턴스를 그 안에 생성 할 수가 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/ec2_3.jpg)

마지막 검토단계까지 입력한 후 시작 버튼을 누르면 키파일을 선택하는 창이 나오는데 키파일이 있다면 기존 키파일을, 없다면 새로 생성을 하시면 됩니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/ec2_4.jpg)

그렇게 해서 인스턴스까지 생성된 모습입니다. 위처럼 public ip가 없다면 좌측 메뉴의 탄력적 IP메뉴에서 IP를 할당받아 적용할 수 있으며 그렇지 않으면 생성단계떄 인스턴스 구성 항목에서 public ip를 가진채로 생성할수도 있습니다.<br><br>

### 4. 인터넷 게이트웨이 만들기

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/igw_1.jpg)

VPC를 만들고, Subnet을 만들고, 인스턴스를 만들었으니 이제 외부와의 연결을 위해서 인터넷 게이트웨이를 만듭니다. 서비스의 VPC메뉴로 돌아가서 좌측의 인터넷 게이트웨이 메뉴로 들어온 모습입니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/igw_2.jpg)

인터넷 게이트웨이는 아주 심플하게 이름만 입력하면 생성할 수 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/igw_3.jpg)

그렇게 생성된 모습입니다. 하지만 생성된 직후에는 제 역할을 하지 못하니 동작을 위해 마우스 우클릭이나, 인터넷 게이트웨이를 클릭한 후 상단의 작업 버픈을 클릭, VPC에 연결 버튼을 입력해 줍니다.

연결할 전에 생성한 myVPC를 선택한후 연결해 주시면

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/igw_4.jpg)

이렇게 attached상태가 뜨며 연결이 됩니다.<br><br>

### 5. 라우팅 테이블

인터넷 게이트웨이까지 연결하고 나면, 라우팅 테이블을 작성해줘야 합니다.
라우팅 테이블 메뉴도 또한 서비스 VPC메뉴에서 좌측을 보시면 있습니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/route_1.jpg)

보시면 자동으로 라우팅 테이블이 하나 생겨나 있는걸 보실 수 있습니다.
VPC ID를 보고 자신이 설정하려는 VPC의 라우팅 테이블이 맞는지 확인하신 후에 하단의 Routes탭을 클릭하여 edit routes로 들어갑니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/route_2.jpg)

들어가시면 이런 화면이실 겁니다. add route 눌러줍니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/route_3.jpg)

위처럼 입력하시면 인터넷과 연결이 됩니다. 오른쪽은 인터넷 게이트웨이의 id입니다.


이렇게 완성된 상태를 그림으로 그려보면-

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case2/img/finish.jpg)
