# S3 Security

* ### Encryption 방법 4가지
    - #### Server Side
        + S3 Managed Key (SSE-S3)
            1. Key는 아마존이 소유하고 관리한다.
            2. AES-256 방식의 암호화를 사용한다.
            3. 새로운 Bucket, Object에 default로 활성화가 되어있다.
            4. x-amz-server-side-encryption:"AES-256" 헤더가 박혀있어야 환다.   
   <br>

        + KMS Keys Stored in AWS KMS (SSE-KMS)
            1. Key는 아마존의 AWS KMS(Key Management Service) 에서 관리한다.
            2. 사용자의 컨트롤이 들어간다.
            3. x-amz-server-side-encryption:"aws:kms" 헤더가 박혀있어야 한다.

            > KMS 제한사항   
                - 파일 업로드 시 GenerateDataKey KMS API 호출   
                - 파일 다운로드 시 Decrypt KMS API 호출   
                - 리전에 대한 초당 호출제한 존재
<br>

    
        + Customer-Provided Keys (SSE-C)
            1. 키를 AWS 외부에서 관리
            2. 사용자가 제공하는 Key값을 AWS에서 저장하지 않는다. (이용 후 삭제)
            3. HTTPS 만 이용할 수 있다.
            4. HTTP 의 일부로 키를 넘겨야한다? (이해안됨)


    - #### Client Side
        1. 파일을 사용자가 암호화 한 후 S3에 업로드하는 방식
            - 복호화도 사용자측에서 진행한다
            
        2. HTTP, HTTPS 둘 다 이용가능

<br>
추가사항

> Amazon S3 – Force Encryption in Transit aws:SecureTransport