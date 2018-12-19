**가상 스토리지를 제공하는 EBS(Elastic Block Store)** 
-----

다음과 같은 단계로 EBS를 사용할수있다.


1. EBS 볼륨 생성하기
2. EC2 인스턴스에 EBS 볼륨 장착하기
3. EC2 인스턴스에서 EBS 볼륨 포맷하기
4. EC2 인스턴스에서 EBS 볼륨 마운트하기
5. EC2 인스턴스에서 EBS 볼륨 제거하기


-----
서비스 -> EC2 -> 좌측메뉴의 "ELASTIC BLOCK STORE"에서 볼륨 메뉴를 클릭한다.
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img00.png)

볼륨생성을 클릭한후 원하는 사이즈와 저장방식을 선택하고 생성 버튼을 클릭한다.
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img01.png)
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img02.png)
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img03.png)
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img04.png)
만들어진 볼륨에 이름을 붙여놓는다. (작업시 확인하기 쉽다.)
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img05.png)
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img06.png)
만들어진 볼륨을 인스턴스에 연결한다.
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img07.png)
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img08.png)
볼륨 목록에서 in-use 에 녹색 아이콘이 보이면 인스턴스에 연결이 완료.
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img09.png)
인스턴스에 ssh로 터미널로 접속한다.(이미 만들어 놓은 키를 이용)
![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case9/images/img09.png)
#sudo bash
#mkfs -t ext4 /dev/sdf
명령어로 포맷한다.

