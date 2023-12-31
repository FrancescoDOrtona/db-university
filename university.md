1. Selezionare tutti gli studenti nati nel 1990 (160)

``` MYSQL
SELECT *
FROM `students`
WHERE YEAR(`date_of_birth`) = 1990 ;

```
2. Selezionare tutti i corsi che valgono più di 10 crediti (479)

``` MYSQL
SELECT *
FROM `courses`
WHERE `cfu` > 10;

```


3. Selezionare tutti gli studenti che hanno più di 30 anni

``` MYSQL 
<!-- 3051 -->
SELECT *, YEAR(CURRENT_DATE), YEAR(`date_of_birth`)
FROM `students`
WHERE YEAR(CURRENT_DATE) - YEAR(`date_of_birth`) > 30; 

<!-- 3489 -->
SELECT *
FROM `students`
WHERE TIMESTAMPDIFF(YEAR, `date_of_birth`, CURRENT_DATE()) > 30;

```


4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)

``` MYSQL
SELECT * 
FROM `courses`
WHERE `period` = 'I semestre'
AND `year` = 1;

```

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)

``` MYSQL
SELECT * 
FROM `exams`
WHERE `date` = '2020-06-20'
AND `hour` > '14%';

```

6. Selezionare tutti i corsi di laurea magistrale (38)

``` MYSQL
SELECT * 
FROM `degrees`
WHERE `level` = 'magistrale';

```

7. Da quanti dipartimenti è composta l'università? (12)

``` MYSQL
SELECT COUNT(*) as `departments_number` 
FROM `departments`;

```

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

``` MYSQL
SELECT COUNT(*) as `no_phone_number` 
FROM `teachers`
WHERE `phone` IS NULL;

```