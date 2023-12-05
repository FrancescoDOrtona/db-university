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
SELECT `courses`.*
FROM `courses`
INNER JOIN `course_teacher`
ON `course_teacher`.`course_id` = `courses`.`id`
INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
WHERE `teachers`.`id` = 44;

```

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

``` MYSQL 
SELECT `students`.`name`, `students`.`surname`, `degrees`.`name` AS `degree_name`, `departments`.`name` AS `department_name` 
FROM `departments`
INNER JOIN `degrees`
ON `degrees`.`department_id` = `departments`.`id`
INNER JOIN `students`
ON `students`.`degree_id` = `degrees`.`id`  
ORDER BY `students`.`surname` ASC , `students`.`name` ASC;

```

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

``` MYSQL 
SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS `course_name`, CONCAT(`teachers`.`name`, ' ' , `teachers`.`surname`) AS `teacher_fullname` 
FROM `degrees`
INNER JOIN `courses`
ON `courses`.`degree_id` = `degrees`.`id`
INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`;

```

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

``` MYSQL 
SELECT DISTINCT CONCAT(`teachers`.`name`,' ',`teachers`.`surname`) AS `teacher_fullname`, `departments`.`name` AS `department_name` 
FROM `departments`
INNER JOIN `degrees`
ON `degrees`.`department_id` = `departments`.`id`
INNER JOIN `courses`
ON `courses`.`degree_id` = `degrees`.`id`
INNER JOIN `course_teacher`
ON `courses`.`id` = `course_teacher`.`course_id`
INNER JOIN `teachers`
ON `teachers`.`id` = `course_teacher`.`teacher_id`
WHERE `department_id` = 5;

```

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.

``` MYSQL 


```