# CloudFront

* ### Content Delievery Network
    - 읽기 성능을 개선 및 여러 군데 contents 를 caching 함
    - Edge Location 216개 존재
    - 가격
        - >참고 :    
        https://aws.amazon.com/ko/cloudfront/pricing/
   
    - DDOS 방어 및 AWS WAF 
        - >세부 설명 :    
        https://docs.aws.amazon.com/ko_kr/waf/latest/developerguide/ddos-event-mitigation-logic-continuous-inspection.html   

<br>

---

### 작동 원리 

    Client에서 Server로 데이터 요청 -> CloundFront Edge Location은 Local Cache를 확인해 요청한 내용이 있는지 확인 -> 없으면 Origin 으로 가서 데이터를 직접 가져오고 Caching 함
---

## Cache Invalidation
백엔드 단에서 오리진을 업데이트 했을 때 CloudFront 는 그 사실을 알지 못해서 TTL이 만료된 후에나 업데이트 될 것이다.   
그러나 강제로 부분 혹은 전체의 Cache 들을 TTL을 Passing 하고 Cache Invalidation을 통해 Update 할 수 있다.

---
### CloudFront VS S3 Cross Region Replication

- CloudFront
    - 전세계에 뻗어있는 네트워크
    - 정적 파일을 어디서든 사용 할 수 있도록 하는데 적합
    - TTL 동안 살아있는 파일들

- S3
    - 본인이 직접 복제하고 싶은 Region 에 Setup 해야 함
    - 일부 지역에서 낮은 지연시간으로 동적인 콘텐츠를 제공하는데 적합
    - Read Only
    - 파일 실시간 업데이트

        