LOS Darkelf
===========

<img src="assets/darkelf_los_1.png" width=50%/>

##

이번 문제는 언뜻 보기엔 쉬워보였지만, or, and가 preg_match 함수에 의해 걸러지고 있었기 때문에 이를 우회할 방법이 필요했다.

<img src="assets/darkelf_los.png" width=50%/>

##

그래서 간단히 || 기호를 통해서 or을 사용했다.
####작성한 페이로드는 pw=1' || id='admin이다.
####url encoding을 적용한 페이로드는 pw=1%27%20||%20id=%27admin이다.
