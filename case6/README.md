**AWS CloudFront** 




CloudFront 기능으로 EdgeLocation에 배포되는 과정
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/how-cloudfront-delivers-content.png)

EdgeLocation 지도
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/cloudfront-map.png)

S3 설정만 하였을 경우
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/s3.jpg)

S3 설정후 CloudFront를 설정하여 배포할 경우
![구성1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/s3-cloudfront.jpg)

CloudFront 설정
![설정1](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/img00.png)
![설정2](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/img01.png)
![설정3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/img02.png)
EdgeLocation 을 한정해서 배포할다. (Use All Edge Locations 선택)
![설정3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/img03.png)
![설정3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/img04.png)
설정을 하면 In Progress(진행중)을 확인 15분 정도 기다리면 Deployed 상태로 변경됨
![설정3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/img05.png)
![설정3](https://github.com/dockerdongjin/aws-network-examples/blob/master/case6/images/img06.png)