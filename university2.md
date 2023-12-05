<!-- Query group by -->

1. Contare quanti iscritti ci sono stati ogni anno

``` MYSQL 
SELECT COUNT(*) as `enrolments_every_year`, YEAR(`enrolment_date`) as `year_of_enrolment`
FROM `students`
GROUP BY `year_of_enrolment`;

```

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

``` MYSQL 
SELECT COUNT(*) as `same_office`, `office_address`
FROM `teachers`
GROUP BY `office_address`;

```

3. Calcolare la media dei voti di ogni appello d'esame

``` MYSQL 
SELECT `exam_id` ,COUNT(*) as `exam`, AVG(`vote`) as `avg_vote` 
FROM `exam_student`
GROUP BY `exam_id`  
ORDER BY `exam` ASC;

```

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

``` MYSQL 
SELECT COUNT(*) as `degrees_for_department`, `department_id` 
FROM `degrees`
GROUP BY `department_id`;

```


<!-- Query Join -->

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

``` MYSQL 
SELECT `students`.`id`, `degrees`.`name` AS `degree_name`, CONCAT(`students`.`name`, '  ', `students`.`surname`) AS `student_fullname`
FROM `degrees`
INNER JOIN `students`
ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze

``` MYSQL 
SELECT `degrees`.*, `degrees`.`name` AS `degree_name` 
FROM `degrees`
INNER JOIN `departments`
ON `degrees`.`department_id` = `departments`.`id`
WHERE `degrees`.`level` = 'magistrale'
AND `departments`.`name` = 'Dipartimento di Neuroscienze';

```

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

``` MYSQL 


```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

``` MYSQL 


```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

``` MYSQL 


```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

``` MYSQL 


```

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.

``` MYSQL 


```