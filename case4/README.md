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
