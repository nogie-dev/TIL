# S3 ETC

* ### Pre-Signed URL
    - S3 Console, AWS CLI or SDk를 이용해 생성가능
        * URL 만료기간
            - S3 Console : 최소 1분 ~ 최대 720분 (12시간)
            - AWS CLI : default -> 3600s, max -> 604800s (168시간)
        
    - Pre Signed URL은 GET/PUT에 대한 URL을 생성한 사용자의 권한을 상속한다.

* ### Glacier Value Lock
    - WORM (Write Once Read Many) 모델 적용
    - 설정한 기간동안 Block 시킴 (기간 만료 전까지 절대 건들 수 없음) #모드별로 차이 있음
    - Mode 별 설명
        * Compliance : Root 유저를 포함해서 어떤 유저도 ***Overwrite*** 혹은 ***Delete*** 불가
            - Retention Mode도 수정 불가, 기간 수정도 불가

        * Governance : 대부분의 유저가 ***Overwrite*** 혹은 ***Delete*** 불가, 잠금 설정 변경 불가

        * Legal Hold : 무기한 보호
            - s3:PutObjectLegalHold IAM permission 을 통해 자유롭게 해제 가능

* ### Object Lambda
    - Caller Application 에서 검색되기 전에 Lambda Func를 통해 가공해서 보냄
    - 오직 하나의 버킷만을 필요로 함
    > 참고 : https://aws.amazon.com/ko/blogs/korea/introducing-amazon-s3-object-lambda-use-your-code-to-process-data-as-it-is-being-retrieved-from-s3/