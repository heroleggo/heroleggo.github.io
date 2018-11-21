

# Writeup for 6th week

## 목차 

## 1. bsqli 

## 2. esqli 

## 3. ebsqli 

## 4. sqli2 

## 5. sqli3

---

## bsqli 

bsqli 문제는 우리가 쿼리의 결과를 알 수 없는 blind sql injection 문제였다. 이를 해결하기 위해서 sleep 함수를 이용하여 쿼리가 참일 경우 sleep을 실행하고 그렇지 않을 경우 그냥 넘어가도록 로직을 짰다. 가장 많이 사용한 쿼리는 " %bf' or id=0x61646d696e and sleep(~~) # "였다. 

---

## esqli 

esqli 문제는 쿼리에 에러가 있을 경우 echo를 통해 에러를 출력해주는 로직이 있었는데, 이를 이용해서 문제를 해결할 수 있었다. 쿼리가 정상적으로 수행되었을 경우, extractvalue 를 통해서 에러를 발생시키도록 했다. 이를 통해서 select 문을 사용하여 원하는 쿼리를 뽑아냈다. 사용한 쿼리는 " %bf' or id=0x61646d696e and extractvalue(rand(), concat(0x3a, (select pw from user where id=0x61646d696e)))# "이다.



---

## sqli2 

sqli2 문제는 DB 내에 존재하는 플래그를 얻어와야 하는 문제였다. 플래그를 얻기 위해서 DB의 이름을 이용해서 테이블의 이름을 가져오고, 테이블의 이름을 이용해서 컬럼의 이름을 가져온 뒤, 테이블과 컬럼의 이름을 사용해서 데이터를 긁어오도록 했다. 밑의 쿼리 문장들을 사용해서 쉽게 플래그를 얻어올 수 있었다. ' union select (select table_name from information_schema.tables where table_schema=database() limit 0, 1), 2#" # table_name is fl4ggggg ' union select (select column_name from information_schema.columns where table_name='fl4ggggg' limit 0,1), 2#" # column_name is fllllag ' union select (select fllllag from fl4ggggg limit 0,1), 2#" 

---

## sqli3 

sqli3 문제는 조금 어려운 문제였다. 블라인드로 플래그를 얻어와야 했기 때문에, 여러 번의 인젝션을 수행해야 했다. 우선 테이블의 길이를 얻어오고, 테이블의 이름을 얻어와야하고, 그 이후 그 테이블의 이름을 이용해서 컬럼의 길이와 이름을 얻어와야 했다. 테이블을 얻어올 때 limit 1, 1 을 이용해서 첫 번째 row를 얻어오는 것이 아닌 두 번째 row를 얻어와야 플래그가 존재하는 테이블을 얻어올 수 있었다. 나머지는 간단했으므로 일반적인 blind sql injection 을 하는 것 처럼 수행하여 플래그를 구할 수 있었다.
