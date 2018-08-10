LOS Wolfman
===========

<img src="assets/wolfman_los_1.png" width=50%/>

***

이번 문제는 preg_match 함수에 의하여 whitespace(공백)이 걸러지고 있었다. 이 공백을 우회하기 위해서 탭문자를 사용해서 문제를 해결할 수 있었다.

***

<img src="assets/wolfman_los.png" width=50%/>

***

>**문제를 해결하기 위해서 작성한 페이로드는 pw=1'%09or%09id='admin'#이다.**
**모두 url encoding을 적용하면 pw=1%27%09or%09id=%27admin%27%23이다.**
