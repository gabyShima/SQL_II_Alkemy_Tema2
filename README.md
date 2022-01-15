1. Nombre, apellido y cursos que realiza cada estudiante

__SELECT e.nombre, e.apellido, c.nombre as "Curso que realiza"   
FROM estudiante e   
INNER JOIN inscripcion i ON e.legajo = i.ESTUDIANTE_legajo  
INNER JOIN curso c on c.codigo = i.CURSO_codigo;__

2. Nombre, apellido y cursos que realiza cada estudiante, ordenados por el nombre del curso

__SELECT e.nombre, e.apellido, c.nombre as "Curso que realiza"  
FROM estudiante e   
INNER JOIN inscripcion i ON e.legajo = i.ESTUDIANTE_legajo 
INNER JOIN curso c on c.codigo = i.CURSO_codigo  
ORDER BY c.nombre;__

3. Nombre, apellido y cursos que dicta cada profesor

__SELECT p.nombre, p.apellido, c.nombre as "Curso que dicta"  
FROM curso c  
INNER JOIN profesor p ON p.id = c.PROFESOR_id;__

4. Nombre, apellido y cursos que dicta cada profesor, ordenados por el nombre del curso

__SELECT p.nombre, p.apellido, c.nombre as "Curso que dicta"  
FROM curso c  
INNER JOIN profesor p ON p.id = c.PROFESOR_id  
ORDER BY c.nombre__

5. Cupo disponible para cada curso (Si el cupo es de 35 estudiantes y hay 5 inscriptos, el cupo disponible será 30)
cantidad de alumnos inscriptos por curso  

__SELECT c.nombre, ROUND(c.cupo-COUNT(*)) as 'Cantidad de cupos restantes'  
FROM curso c  
INNER JOIN inscripcion i ON c.codigo = i.CURSO_codigo  
GROUP BY c.nombre;__

6. Cursos cuyo cupo disponible sea menor a 10

__SELECT c.nombre,  
CASE  
WHEN ROUND(c.cupo - COUNT(i.CURSO_codigo)) < 10  
THEN 'Sí'  
ELSE 'No'  
END  
AS "¿Tiene menos de 10 cupos?"  
FROM curso c  
INNER JOIN inscripcion i ON c.codigo = i.CURSO_codigo  
GROUP BY c.nombre;__


