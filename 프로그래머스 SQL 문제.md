# 프로그래머스 SQL

❗ oracle과 mysql 섞여있음

<br/>

#### [SELECT]

1. [모든 레코드 조회하기](https://programmers.co.kr/learn/courses/30/lessons/59034)

   🐶 SELECT * FROM ANIMAL_INS ORDER BY ANIMAL_ID ASC;

2. [역순 정렬하기](https://programmers.co.kr/learn/courses/30/lessons/59035)

   🐶 SELECT NAME, DATETIME FROM ANIMAL_INS ORDER BY ANIMAL_ID DESC;

3. [아픈 동물 찾기](https://programmers.co.kr/learn/courses/30/lessons/59036)

   🐶 SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION='Sick';

4. [어린 동물 찾기](https://programmers.co.kr/learn/courses/30/lessons/59037)

   🐶 SELECT ANIMAL_ID, NAME FROM ANIMAL_INS WHERE INTAKE_CONDITION != 'Aged';

5. [동물의 아이디와 이름](https://programmers.co.kr/learn/courses/30/lessons/59403)

   🐶 SELECT ANIMAL_ID, NAME FROM ANIMAL_INS;

6. [여러 기준으로 정렬하기](https://programmers.co.kr/learn/courses/30/lessons/59404)

   🐶 SELECT ANIMAL_ID, NAME, DATETIME FROM ANIMAL_INS ORDER BY NAME ASC, DATETIME DESC;

7. [상위 n개 레코드](https://programmers.co.kr/learn/courses/30/lessons/59405)

   🐶 SELECT NAME FROM ANIMAL_INS ORDER BY DATETIME ASC LIMIT 1;

<br/>

#### [SUM, MAX, MIN]

1. [최댓값 구하기](https://programmers.co.kr/learn/courses/30/lessons/59415)

   🐰 SELECT DATETIME FROM ANIMAL_INS ORDER BY DATETIME DESC LIMIT 1;

   🐰 SELECT MAX(DATETIME) FROM ANIMAL_INS;

2. [최솟값 구하기](https://programmers.co.kr/learn/courses/30/lessons/59038)

   🐰 SELECT MIN(DATETIME) FROM ANIMAL_INS;

3. [동물 수 구하기](https://programmers.co.kr/learn/courses/30/lessons/59406)

   🐰 SELECT COUNT(ANIMAL_ID) FROM ANIMAL_INS;

4. [중복 제거하기](https://programmers.co.kr/learn/courses/30/lessons/59408)

   🐰 SELECT COUNT(DISTINCT(NAME)) FROM ANIMAL_INS;

<br/>

#### [GROUP BY]

1. [고양이와 개는 몇 마리 있을까](https://programmers.co.kr/learn/courses/30/lessons/59040)

   🐱 SELECT ANIMAL_TYPE, COUNT(ANIMAL_ID) AS count 

   ​      FROM ANIMAL_INS 

   ​      GROUP BY ANIMAL_TYPE ORDER BY ANIMAL_TYPE ASC;

2. [동명 동물 수 찾기](https://programmers.co.kr/learn/courses/30/lessons/59041)

   🐱 SELECT NAME, COUNT(NAME) AS COUNT 
         FROM ANIMAL_INS 
         GROUP BY NAME HAVING COUNT(NAME) >= 2
         ORDER BY NAME ASC;

3. [입양 시각 구하기 (1)](https://programmers.co.kr/learn/courses/30/lessons/59412)

   🐱 SELECT HOUR(DATETIME) AS HOUR, COUNT(HOUR(DATETIME)) AS COUNT
         FROM ANIMAL_OUTS
         GROUP BY HOUR
         HAVING HOUR >= 9 AND HOUR <= 19
         ORDER BY HOUR ASC;

<br/>

#### [IS NULL]

1. [이름이 없는 동물의 아이디](https://programmers.co.kr/learn/courses/30/lessons/59039)

   🐷 SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME IS NULL ORDER BY ANIMAL_ID ASC;

2. [이름이 있는 동물의 아이디](https://programmers.co.kr/learn/courses/30/lessons/59407)

   🐷 SELECT ANIMAL_ID FROM ANIMAL_INS WHERE NAME IS NOT NULL ORDER BY ANIMAL_ID ASC;

3. [NULL 처리하기](https://programmers.co.kr/learn/courses/30/lessons/59410)

   🐷 SELECT ANIMAL_TYPE, NVL(NAME, 'No name'), SEX_UPON_INTAKE
         FROM ANIMAL_INS ORDER BY ANIMAL_ID ASC;

<BR/>

#### [JOIN]

1. [없어진 기록 찾기](https://programmers.co.kr/learn/courses/30/lessons/59042)

   🐹 SELECT O.ANIMAL_ID, O.NAME
         FROM ANIMAL_INS I ,ANIMAL_OUTS O
         WHERE I.ANIMAL_ID (+) =  O.ANIMAL_ID 
         AND I.ANIMAL_ID IS NULL
         ORDER BY ANIMAL_ID;

2. [있었는데요 없었습니다](https://programmers.co.kr/learn/courses/30/lessons/59043)

   🐹 SELECT I.ANIMAL_ID, I.NAME
         FROM ANIMAL_INS I, ANIMAL_OUTS O
         WHERE I.ANIMAL_ID = O.ANIMAL_ID
         AND O.DATETIME < I.DATETIME
         ORDER BY I.DATETIME ASC;

3. [오랜 기간 보호한 동물 (1)](https://programmers.co.kr/learn/courses/30/lessons/59044)

   🐹 SELECT I.NAME, I.DATETIME
         FROM ANIMAL_INS I LEFT JOIN ANIMAL_OUTS O ON I.ANIMAL_ID = O.ANIMAL_ID
         WHERE O.ANIMAL_ID IS NULL
         ORDER BY I.DATETIME
         LIMIT 3;

