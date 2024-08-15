# Solidity 사용법

* ### fallback 함수
    - contract 에 존재하지 않는 함수를 호출할 때 호출됨
    - contract 를 호출할 때 아무런 데이터를 담아 보내지 않으면 호출됨

    ```c
    fallback() external payable {
    // This function is executed on a call to the contract if none of the other
    // functions match the given function signature, or if no data is supplied at all
    }
    ```
    > 출처 : https://shishirsingh66g.medium.com/solidity-part-2-payable-fallback-and-receive-42c00cb75108

<br>
<hr>

* ### receive 함수
    - contract 에 존재하지 않는 함수를 호출할 때 호출됨
    
    *중요 차이점 : contract 메세지가 존재하면 fallback 아니면 receive*
<br>
<br>
<hr>

* ### Delegate
    - 