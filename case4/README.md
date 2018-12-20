### **AWS기초 및 활용** 

# Nat 구성하기

> 
>
>
>

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/nat_img/nat-2.jpg)
우선 위 이미지처럼 구현된 VPC환경을 가지고 시작하도록 하겠습니다.
VPC 안에 두개의 서브넷을 만들고, 위쪽에는 public ip를 부여하고 아래쪽에는 부여하지 않았습니다.
그렇게 되면 인스턴스 서로간의 통신은 되지만 아래쪽 인스턴스는 외부와 통신을 할 수 없는 상태가 됩니다.
이때 외부로 나갈 수는 있게 하고 외부에서의 접속은 막는 방법이 바로 Nat Gateway입니다.

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/nat_img/nat-1.jpg)
최종적으로는 이런 형태가 되도록 만들어 볼겁니다.
private인스턴스에서 인터넷은 되지만 외부에서의 접속은 막고, public인스턴스를 통한 연결로 들어갈 수 있는 형태입니다.

우선 Nat Gateway를 생성해줘야 합니다.
위치는 VPC 서비스에 Nat Gateway메뉴로 가고, Nat Gateway생성을 하시면 됩니다.
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/nat_img/nat-3.jpg)
서브넷은 위 설계대로 public영역을 줘야하고 탄력적 ip할당은 미리 받아둔게 있다면 그걸로 하고 없다면 '새 EIP 생성'버튼을 눌러 만들면 됩니다.<br><br>

다음은 라우팅 테이블 설정입니다.
라우팅 테이블은 Nat Gateway를 담당해줄 메인 테이블과, public인스턴스가 Internet Gateway로 나가기 위한 커스텀 테이블 2개가 필요합니다.<br><br>

우선 메인 라우팅 테이블의 라우트 설정에 가셔서 0.0.0.0/0대역에 대한 Nat Gateway연결을 만들어 줍니다.
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/nat_img/nat-4.jpg)

그리고 커스텀 라우팅 테이블의 라우트 설정에선 같은 방법으로 0.0.0.0/0대역으로 Internet Gateway연결을 만듭니다.
그리고 추가로 커스텀 라우팅 테이블에서는 Subnet Associations설정에 들어가서 아래 이미지처럼 퍼블릭 서브넷을 선택하고 저장 해줍니다.
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/nat_img/nat-5.jpg)<br><br>

![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/nat_img/nat-6.jpg)
그럼 이런 상태가 됩니다. 그럼 이대로 터미널로 public ip를 가진 인스턴스를 통해 접속해서 ping이나 apt, yum명령어를 사용해 보시면 되는걸 확인할수 있습니다.
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/nat_img/nat-7.jpg)
