** aws cli 사용하기 ** 
-----

리눅스 터미널 작업환경
(https://docs.google.com/document/d/1LsqSMYPcfdAmhAsMY4LhZOP1YdBUaA5rilqpGkhM4g0/edit)



AWS CLI 설정하기
AWS IAM 에서 사용자를 추가한다. (web page)


>➜ ~ aws configure
>>AWS Access Key ID [None]: AKIAIGFVJJOEDXXXXGA
>>
>>AWS Secret Access Key [None]: y5ZVV/0HKCHxlQPaW3We4dXFQ3cawOH3hKrJxxxxxxxoW6h
>>
>>Default region name [None]: ap-northeast-2
>>
>>Default output format [None]: json

>아래 파란색 vlaue 는 자신의 값에 맞춰 확인해서 입력한다.

>➜ aws ec2 create-vpc --cidr-block 10.0.0.0/16

>➜ aws ec2 create-subnet --vpc-id vpc-0c7dc3922a0c5db85 --cidr-block 10.0.1.0/24

>➜ aws ec2 create-subnet --vpc-id vpc-0c7dc3922a0c5db85 --cidr-block 10.0.2.0/24

>➜ aws ec2 create-internet-gateway

>➜ aws ec2 attach-internet-gateway --vpc-id vpc-0c7dc3922a0c5db85 --internet-gateway-id igw-01019896048d317b1

>➜ aws ec2 create-route-table --vpc-id vpc-0c7dc3922a0c5db85

>➜ aws ec2 create-route --route-table-id rtb-0cf265798cc0497c6 --destination-cidr-block 0.0.0.0/0 --gateway-id igw-01019896048d317b1

>➜ aws ec2 describe-route-tables --route-table-id rtb-0cf265798cc0497c6

>➜ aws ec2 describe-subnets --filters "Name=vpc-id,Values=vpc-0f1a4720f9e3ca7f4" --query 'Subnets[*].{ID:SubnetId,CIDR:CidrBlock}'

>➜ aws ec2 associate-route-table --subnet-id subnet-011a57b5dd5b060a1 --route-table-id rtb-0c06565341be0ca08

>➜ aws ec2 modify-subnet-attribute --subnet-id subnet-011a57b5dd5b060a1 --map-public-ip-on-launch **해당 서브넷에서 인스턴스 생성시 공용IP 를 받을수있게 수정

키페어 파일 만들기
>➜  ~ aws ec2 create-key-pair --key-name myVPCkey --query 'KeyMaterial' --output text > myVPCkey.pem
>➜  ~ ls -alt myVPCkey.pem
>>-r-------- 1 byoungsoo byoungsoo 1671 Dec 24 15:27 myVPCkey.pem
>➜  ~ chmod 400 myVPCkey.pem

보안그룹 만들기
>➜  ~ aws ec2 create-security-group --group-name SSHAccess --description "Security group for SSH access" --vpc-id vpc-0f1a4720f9e3ca7f4
>➜  ~ aws ec2 authorize-security-group-ingress --group-id sg-07b69eb315d7fd464 --protocol tcp --port 22 --cidr 0.0.0.0/0
>➜  ~ aws ec2 run-instances --image-id ami-0b4fdb56a00adb616 --count 1 --instance-type t2.micro --key-name myVPCkey --security-group-ids sg-07b69eb315d7fd464 --subnet-id subnet-011a57b5dd5b060a1
>➜  ~ aws ec2 describe-instances --instance-id i-0de3817b296641647  (인스턴스 상태)
>>➜  ~ ssh -i myVPCkey.pem ec2-user@13.209.85.246
>>>The authenticity of host '13.209.85.246 (13.209.85.246)' can't be established.
>>>ECDSA key fingerprint is SHA256:ndEKjqWpPUaihEgQccrJLxcnmLr+b5INgZlcBF0pUqg.
>>>Are you sure you want to continue connecting (yes/no)? yes
>>>Warning: Permanently added '13.209.85.246' (ECDSA) to the list of known hosts.
>>>
>>>       __|  __|_  )
>>>       _|  (     /   Amazon Linux 2 AMI
>>>      ___|\___|___|
>>>
>>>https://aws.amazon.com/amazon-linux-2/
>>>15 package(s) needed for security, out of 16 available
>>>Run "sudo yum update" to apply all updates.
>>>[ec2-user@ip-10-0-0-230 ~]$


작업로그 저장하기
>➜  ~ history | grep 'aws ec2' > aws-job-history.txt




> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case11/images/img00.png)
도쿄 리전에 AMI 를 확인(아직은 존재하지 않는다.)
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case11/images/img01.png)
서울 리전에 있는 AMI를 도쿄리전으로 복사한다.
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case11/images/img02.png)
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case11/images/img03.png)
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case11/images/img04.png)
만들어진 이미지 확인 (좌측메뉴 AMI)
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case11/images/img05.png)