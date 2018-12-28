** Lambda 사용하기 ** 
-----

>SNS 설정 (푸시 서비스 | SNS 푸시 알림 서비스 | Amazon Web Services)

구독정보 만들기
>> aws> sns create-topic --name my-topic

구독 인증메일 보내기
>> aws> sns subscribe --topic-arn arn:aws:sns:ap-northeast-2:376178164160:my-topic --protocol email --notification-endpoint atmega@naver.com

구독정보에 메세지 보내기
>> aws> sns publish --topic-arn arn:aws:sns:ap-northeast-2:376178164160:my-topic --message "Hello World!"

생성한 구독정보 리스트보기
>> aws> sns list-subscriptions



> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/img00.png)

> 1)사용자가 S3 버킷(객체 생성 이벤트)에 객체를 업로드합니다.
>
> 2)Amazon S3가 객체 생성 이벤트를 감지합니다.
>
> 3)Amazon S3는 버킷 알림 구성에 지정된 Lambda 함수를 호출합니다.
>
> 4)AWS Lambda는 Lambda 함수를 생성할 때 지정한 실행 역할을 가정하여 Lambda 함수를 실행합니다.
>
> 5)Lambda 함수가 실행됩니다.



이미지 파일을 Resize 하는 Lambda 기능
서비스 -> Lambda -> 함수 생성 -> AWS Serverless Application Repository 를 선택후 검색창에 "resize" 를 입력한다.
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/lambda00.png)
resize 어플리케이션을 선택한다.
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/lambda01.png)
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/lambda02.png)
> 어플리케이션 설정 정보를 입력하고 배포를 클릭한다.
> S3 메뉴에서 버킷을 확인한다. 어플리케이션에서 설정한 desc2.valuedesign.co.kr 버킷이 자동으로 만들어지지 않아 수동으로 만든다.
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/lambda03.png)
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/lambda04.png)
> sorc2.valuedesign.co.kr 버킷에 이미지파일을 업로드한다.
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/lambda05.png)
> desc2.valuedesign.co.kr 버킷에 이미지파일 사이즈가 작아진 것을 확인한다.
> 만들어진 어플리케이션은 CloudFormation 메뉴에서 확인이 가능하다.












> 1-0-0) aws cli 에서 S3 버킷을 생성합니다.
>> aws> s3 mb s3://data.valuedesign.co.kr
>>
>> make_bucket: data.valuedesign.co.kr
>>
>> aws> s3 mb s3://dataresized.valuedesign.co.kr
>>
>> make_bucket: dataresized.valuedesign.co.kr


> 1-0-1) Amazon S3 이벤트 알림 구성
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/img02.png)
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/img03.png)
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/img04.png)


> 1-1)사용자가 S3 버킷(객체 생성 이벤트)에 객체를 업로드합니다.
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/img02.png)


Lambda 함수를 생성하고 수동으로 호출(샘플 이벤트 데이터 사용)