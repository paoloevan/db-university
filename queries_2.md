Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT YEAR(`enrolment_date`) AS 'Year', COUNT(`id`) FROM `students` GROUP BY YEAR(`enrolment_date`);
```
Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT `office_address` AS 'Edificio', COUNT(`id`) FROM `teachers` GROUP BY `office_address`;
```
Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT `exams`.`id` AS 'ID Esame', AVG(`exam_student`.`vote`) AS 'Media Voti' FROM `exam_student` JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id` GROUP BY `exams`.`id`;
```
Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT `departments`.`name` AS `Dipartimento`, COUNT(`degrees`.`id`) AS 'Numero corsi di laurea' FROM `degrees` JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` GROUP BY `Dipartimento`;
```



Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT `students`.* FROM `students` JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

```
Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
SELECT `degrees`.* FROM `degrees` JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` WHERE `departments`.`name` = 'Dipartimento di Neuroscienze' AND `degrees`.`level` = 'magistrale';
```
Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
SELECT `courses`.* FROM `courses` JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` WHERE `teachers`.`id` = 44;

```
Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
