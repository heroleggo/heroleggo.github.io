#  LOS Gremlin

> LOS란? 
>
> LOS 는 SQL Injection을 쉽게 공부할 수 있게 만든 사이트이다.
>
> 여러 가지의 SQL Injection을 풀 수 있는 환경을 만들어 놓았다.

![gremlin_los](https://github.com/heroleggo/heroleggo.github.io/assets/images/gremlin_los.jpg)

문제는 간단하다. id를 admin으로 바꾸어 주기만 하면 쉽게 문제를 해결할 수 있다.

여기서 pw를 우회하려면, $_GET[id] 부분에서 주석을 입력해서 뒤에 위치한 코드를 인식하지 않게 하면 된다.

그렇게 입력한 페이로드는 id=admin%27%23 (id=admin'#)이다.

