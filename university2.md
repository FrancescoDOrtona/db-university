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


```

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

``` MYSQL 


```


<!-- Query Join -->

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

``` MYSQL 


```

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze

``` MYSQL 


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