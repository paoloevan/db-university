Selezionare tutti gli studenti nati nel 1990 (160)
```sql
SELECT * FROM `students` WHERE YEAR(`date_of_birth`)=1990;
```
Selezionare tutti i corsi che valgono più di 10 crediti (479)
```sql
SELECT * FROM `courses` WHERE `cfu` > 10;
```
Selezionare tutti gli studenti che hanno più di 30 anni
```sql
SELECT * FROM `students` WHERE TIMESTAMPDIFF(YEAR, `date_of_birth`, CUREDATE()) > 30;
```
Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)
```sql
SELECT * FROM `courses` WHERE `period` = 'I semestre' AND `year` = 1;

```
Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)
```sql
SELECT * FROM `exams` WHERE HOUR(`hour`) > 13 AND `date` = '2020-06-20';
```
Selezionare tutti i corsi di laurea magistrale (38)
```sql
SELECT * FROM `degrees` WHERE `level` = 'magistrale';

```
Da quanti dipartimenti è composta l'università? (12)
```sql
SELECT COUNT(id) as total_departments FROM `departments`;
```
Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
```sql
SELECT COUNT(id) as total_teachers FROM `teachers` WHERE `phone` IS NUll;

```
Contare tutti i corsi per cfu
```sql
SELECT COUNT(id) as total_courses, cfu FROM courses GROUP BY cfu;
```

Contare gli studenti raggruppandoli per anno di nascita
```sql
SELECT COUNT(id) as total_students, YEAR(`date_of_birth`) AS year_of_birth FROM `students` GROUP BY `YEAR_OF_BIRTH`;
```

