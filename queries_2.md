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

