1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia 

SELECT students.degree_id,students.name,degrees.department_id,degrees.name
FROM db_university.degrees
JOIN db_university.students
ON students.degree_id = degrees.id
WHERE degrees.id LIKE 53
row=( 68 );

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

SELECT departments.id,departments.name,degrees.department_id,degrees.name
FROM db_university.departments
JOIN db_university.degrees
ON departments.id = degrees.department_id
WHERE departments.name LIKE "%NEUROSCIENZE%"
AND degrees.level = "magistrale"

row=( 1 );

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT * 
FROM courses
join course_teacher
ON courses.id = course_teacher.teacher_id
JOIN teachers
ON teachers.id = course_teacher.teacher_id
WHERE teacher_id = 44


4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome

SELECT students.id,students.name,students.surname,degrees.name,departments.name
FROM db_university.students
JOIN degrees
ON students.degree_id = degrees.id
join departments
ON degrees.department_id = departments.id

ORDER BY students.surname,students.name

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT degree_id,degrees.name,courses.name ,teachers.name,teachers.surname
FROM db_university.degrees
JOIN  courses
ON courses.degree_id = degree_id
JOIN course_teacher
ON courses.id = course_teacher.teacher_id
JOIN teachers
ON course_teacher.teacher_id = teacher_id


6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)

SELECT 
    departments.name, degrees.name, courses.name, teachers.name, teachers.surname, teachers.id
FROM departments
JOIN degrees ON departments.id = degrees.department_id
JOIN courses ON degrees.id = courses.degree_id
JOIN course_teacher ON courses.id = course_teacher.course_id
JOIN teachers ON course_teacher.teacher_id = teachers.id
WHERE departments.id = 5
GROUP BY 
    teachers.id,
    teachers.name,
    teachers.surname,
    courses.name,
    degrees.name,
    departments.name;



7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18