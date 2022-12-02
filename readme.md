Modellizzare la struttura di una tabella per memorizzare tutti i dati riguardanti una università:
- sono presenti diversi **Dipartimenti** (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
- ogni Dipartimento offre più **Corsi di Laurea** (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
- ogni Corso di Laurea prevede diversi **Corsi** (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
- ogni Corso può essere tenuto da diversi **Insegnanti**;
- ogni Corso prevede più appelli d'**Esame**;
- ogni **Studente** è iscritto ad un solo Corso di Laurea;
- ogni Studente può iscriversi a più appelli di Esame;
- per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.
Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

Tabelle:
- Departments
- Degree_courses
- Course
- Teachers
- Exams
- Studenti
- Voti

oneToMany => Dipartimenti - Corsi_di-laurea
manyToMany => Corsi_di_laurea - Corsi
oneToMany => Inseganti - Corsi
oneToMany => Corsi - Esami
manyToMany => Corsi - Studenti
oneToMany => Studenti - Corsi_di_laurea
manyToMany => Studenti - Esami

Departments:
-id
-name
-code

Degree_courses:
-id
-id_department
-name
-code

Course_DegreeCourse: #####
-id
-id_Course
-id_DegreeCourse

Courses:
-id
-id_teacher
-name
-code

Student_Course: #######
-id
-id_student
-id_course

Students:
-id
-id_degree_course
-fullname
-freshman
-date_of_birth
-email
-phone

Student_exam: ######
-id
-id_student
-id_exam

Exams:
-id
-id_course
-id_student
-name
-date
-number
-voto


Teachers:
-id
-fullname
-email
-phone
-code
-role
