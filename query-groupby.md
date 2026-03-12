1. Contare quanti iscritti ci sono stati ogni anno

SELECT YEAR(enrolment_date),COUNT(ID) 
FROM db_university.students
GROUP BY YEAR(enrolment_date)

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT office_address, COUNT(id)
FROM teachers
GROUP BY office_address

3. Calcolare la media dei voti di ogni appello d'esame

SELECT student_id, AVG(vote) AS media_voti
FROM db_university.exam_student
GROUP BY student_id;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT department_id,COUNT(name)
FROM db_university.degrees
GROUP BY department_id;