Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT YEAR(`enrolment_date`) AS 'Year', COUNT(`id`)
FROM `students`
GROUP BY YEAR(`enrolment_date`);
```
Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT `office_address` AS 'Edificio', COUNT(`id`)
FROM `teachers`
GROUP BY `office_address`;
```
Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT `exams`.`id` AS 'ID Esame', AVG(`exam_student`.`vote`) AS 'Media Voti'
FROM `exam_student`
JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id`
GROUP BY `exams`.`id`;
```
Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT `departments`.`name` AS `Dipartimento`, COUNT(`degrees`.`id`) AS 'Numero corsi di laurea'
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
GROUP BY `Dipartimento`;
```



Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT `students`.*
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

```
Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT `degrees`.*
FROM `degrees`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
AND `degrees`.`level` = 'magistrale';
```
Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT `courses`.*
FROM `courses`
JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
WHERE `teachers`.`id` = 44;

```
Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
SELECT `students`.`surname` AS `Cognome`,`students`.`name` AS `Nome` , `students`.`id` AS `ID`, `degrees`.`name` AS `Corso di Laurea`, `departments`.`name` AS `Dipartimento`
FROM `students`
JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
ORDER BY `students`.`surname`, `students`.`name`;
```

Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
SELECT `degrees`.`name` AS `Corso di Laurea`, `courses`.`name` AS `Corso`, `teachers`.`surname` AS `Insegante`
FROM `courses`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`
ORDER BY `Corso di Laurea`;

```

Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
SELECT DISTINCT `teachers`.*
FROM `teachers`
JOIN `course_teacher` ON `course_teacher`.`teacher_id` = `teachers`.`id`
JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id`
JOIN `degrees` ON `courses`.`degree_id` = `degrees`.`id`
JOIN `departments` ON `degrees`.`department_id` = `departments`.`id`
WHERE `departments`.`name` = 'Dipartimento di Matematica'
ORDER BY `teachers`.`id` ASC;

```
BONUS: Selezionare per ogni studente quanti tentativi d???esame ha sostenuto per superare ciascuno dei suoi esami

```sql
SELECT `students`.`name` AS `Nome`, `students`.`surname` AS `Cognome`, `courses`.`name` AS `Nome corso`, COUNT(`exams`.`id`) AS 'Tentativi'
FROM `exams`
JOIN `courses` ON `exams`.`course_id` = `courses`.`id`
JOIN `exam_student` ON `exam_student`.`exam_id` = `exams`.`id`
JOIN `students` ON `exam_student`.`student_id` = `students`.`id`
GROUP BY `students`.`id`, `courses`.`id`
ORDER BY `Cognome`, `Nome`, `Nome corso`;

```
