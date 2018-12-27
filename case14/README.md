** Lambda 사용하기 ** 
-----

>SNS 설정 (푸시 서비스 | SNS 푸시 알림 서비스 | Amazon Web Services)
>>sns create-topic --name my-topic
>>sns subscribe --topic-arn arn:aws:sns:ap-northeast-2:376178164160:my-topic --protocol email --notification-endpoint atmega@naver.com
>>sns publish --topic-arn arn:aws:sns:ap-northeast-2:376178164160:my-topic --message "Hello World!" 




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



> 1-0-0) aws cli 에서 S3 버킷을 생성합니다.
>> aws> s3 mb s3://data.valuedesign.co.kr
>>
>> make_bucket: data.valuedesign.co.kr
>>
>> aws> s3 mb s3://dataresized.valuedesign.co.kr
>>
>> make_bucket: dataresized.valuedesign.co.kr

> 1-0-1) Amazon S3 이벤트 알림 구성



> 1-1)사용자가 S3 버킷(객체 생성 이벤트)에 객체를 업로드합니다.
> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/img02.png)


Lambda 함수를 생성하고 수동으로 호출(샘플 이벤트 데이터 사용)