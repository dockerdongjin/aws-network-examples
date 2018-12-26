** Lambda 사용하기 ** 
-----

> ![메뉴](https://github.com/dockerdongjin/aws-network-examples/blob/master/case14/images/img00.png)

> 1)사용자가 S3 버킷(객체 생성 이벤트)에 객체를 업로드합니다.

> 2)Amazon S3가 객체 생성 이벤트를 감지합니다.

> 3)Amazon S3는 버킷 알림 구성에 지정된 Lambda 함수를 호출합니다.

> 4)AWS Lambda는 Lambda 함수를 생성할 때 지정한 실행 역할을 가정하여 Lambda 함수를 실행합니다.

> 5)Lambda 함수가 실행됩니다.



> 1-1) aws cli 에서 S3 버킷을 생성합니다.
>> aws> s3 mb s3://data.valuedesign.co.kr
>>
>> make_bucket: data.valuedesign.co.kr
>>
>> aws> s3 mb s3://dataresized.valuedesign.co.kr
>>
>> make_bucket: dataresized.valuedesign.co.kr



