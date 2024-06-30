CREACION BASE DE UN SISTEMA DE GESTION DE ALUMNOS PARA UN COLEGIO
Problema:
La idea es manejar los datos y desempeño de alumno desde el ingreso a la institución hasta su egreso. El sistema incluye a todas las personas que trabajan en la institución ya sea docentes y no docentes y específicamente todo lo relacionado a la parte académica del alumno y su avance a través del tiempo mientras permanece como estudiante.
1.	tipo de reserva.
Objetivo:
Diseñar e implementar una base de datos relacional que satisfaga todas las necesidades de gestión académica para que tanto padres, alumnos y docentes puedan ver reflejado en el sistema el desarrollo del alumno a través de los años y quienes participaron en ese proceso y desde que lugar: alumno, docente, tutor, preceptor, etc.
Descripción de la Base de Datos 
Tablas:
1.	PERSONA
o	Almacena información sobre todas las personas que trabajan en la institución más allá del puesto que ocupen.
o	Atributos: ID_PERSONA, NOMBRE, APELLIDO, TELEFONO, SEXO, DNI, TIPO, FECHA NAC, MAIL, ESTADO CIVIL, FECHA DE ALTA, USUARIO ALTA, FECHA MODIFICACION, USUARIO MODIFICACION
2.	DOMICILIO:
o	Contiene información sobre los domicilios de las personas involucradas en el sistema.
o	Atributos: ID_DOMICILIO, ID_PERSONA, ID_LOCALIDAD, CALLE, NUMERO, PISO, DEPARTAMENTO, BARRIO, CIUDAD, PROVINCIA,  USUARIO ALTA, FECHA DE ALTA, USUARIO MODIFICACION, FECHA ODOFICACION
3.	LOCALIDAD
o	Guarda datos sobre las diferentes localidades existentes
o	Atributos: ID_LOCALIDAD, NOMBRE, C.P.
4.	CONCEPTO_ALUMNO:
o	Guarda el concepto de los alumnos en las diferentes materias.
o	Atributos: ID_ALUMNO, ID_CONCEPTO, CONCEPTO, USUARIO ALTA, FECHA DE ALTA, USUARIO MODIFICACION, FECHA MODOFICACION
5.	ESCALA:
o	Almacena información sobre el valor de las escalas para calificar.
o	Atributos: ID_ESCALA, TIPO, VALOR
6.	CONCEPTO:
o	Contiene la descripción del concepto 
o	Atributos: ID_CONCEPTO, DESCRIPCION, ESCALA
7.	CALIFICACIONES:
o	Registra las las calificaciones de los alumnos en cada materia
o	Atributos: ID_CALIFICACION, ID_ALUMNO, AÑO, CICLO, CURSO, DIV, ID_MATERIA, NOTA, ESCALA, TIPO, USUARIO ALTA, FECHA DE ALTA, USUARIO MODIFICACION, FECHA MODOFICACION
8.	CURSO_MATERIA
o	Registra las materias correspondientes a cada año curricular
o	ID_CURSO/MATERIA, ID_MATERIA, AÑO, CICLO, CURSO, DIV
9.	ALUMNOS:
o	Contiene el listado de alumnos y el curso al cual corresponden
o	Atributos: ID_ALUMNOS, ID_PERSONA, AÑO, CICLO, CURSO, DIV, USUARIO ALTA, FECHA DE ALTA, USUARIO MODIFICACION, FECHA MODOFICACION
10.	USUARIOS DEL SISTEMA
o	Contiene el listado de todos los usuarios del sistema con su respectivo nombre de usuario y contraseña
o	Atributos: ID_USUARIO, ID_PERSONA, USUARIO CONTRASEÑA
11.	TELEFONO
o	Contiene los teléfonos de las personas
o	Atributos: ID_TELEFONO, ID_PERSONA, CODIGO, NUMERO
12.	MATERIA
o	Contiene todas las materias que se dictan en la institución
o	Atributos: ID_MATERIA, NOMBRE, ANO, CICLO, CURSO, DIVISION




o	Problemática Resuelta:
Esta base de datos permite gestionar el sistema académico de un colegio permitiendo registrar el proceso que llevan los mismos desde el ingreso al establecimiento hasta el egreso.
Aspectos que aborda incluyen:
•	Registro de todos los involucrados en el proceso, ya sean alumnos, docentes, no docentes.
•	Registro de las calificaciones año tras año y visualización de las mismas a través del sistema.
•	Visualización de los integrantes de la empresa y el rol que desempeñan.
•	Visualización de las materias que componen cada curso y año y de los docentes de las mismas como así también preceptores y tutores.
•	Registro detallado de las reservas realizadas, incluyendo la fecha, cliente, mesa, empleado y tipo de reserva.








'''

DER SIMPLIFICADO
+------------------+        +-----------------------+    +--------------+
|      PERSONA     |        |       DOMICILIO       |    |  LOCALIDAD   |      +------------------+        +-----------------------+    +--------------|     | id_persona(PK)   |------  | id_domicilio (PK)     | ---| id_localidad |   | nombre           |        | id_persona (FK)       |    | nombre       |
| apellido         |        | id_localidad (FK)     |    | cp           |
| dni              |        | calle                 |    +--------------+        
| tipo             |        | numero                |
| fecha_nac        |        | piso                  |                      | mail             |        | dpto                  |       
| sexo             |        | barrio                |           
| estado_civil     |        +-----------------------+
| fecha_alta       |
| usuario_alta     |--|       
| fecha_modifi     |  |
| usuario_modifi   |  |
+------------------+  | 
                      |
                      |
+------------------+  |     +------------------+     +--------------------+
| concepto_alumno  |  |     |     concepto     |     |  calificaciones    |     +------------------+  |     +------------------+     +--------------------+ 
|id_con_alumno (pk)|------- |  id_concepto (pk)|     |id_calificaciones(pk|
| id_concepto (fk) |  |     |  descripcion     |     |id_alumno (fk)      |
| id_alumno (fk)   |  |     |  escala          |     |ano                 |
+------------------+  |     +------------------+     |ciclo               |
    |                 |          |                   |curso               |
    |                 |          |                   |división            |
    |                 |          |                   |id_materia          |
    |                 |          |                   |nota                |
    |  |---------------------------------------------|escala              |
    |  |     ---------           |                   |tipo                |
    |  |    |                   |                   +--------------------+
+-----------------+      +-----------------+    
|  alumnos        |      |    escala       |
+-----------------+      +-----------------+
| id_alumno (PK)  |      |  id_escala (PK) |
| id_persona (FK) |      |  tipo           |
| ano_cursa       |      |  valor          |
| ciclo           |      +-----------------+
| curso           |
| division        |
| dni             |
+-----------------+


+-----------------+      +------------------------+  +--------------------+
|  curso-materia  |      |    usuario_sistema     |  |    teléfono        +
+-----------------+      +------------------------+  +--------------------+
|id-curso_mat (PK)|      |   id-usuario (PK)      |  |  id-telefono (PK)  |
| id_materia (FK) |      |   id_persona (FK)      |  |  id_persona (FK)   |
| ano             |      |   usuario              |  |  código            |
| ciclo           |      |   contraseña           |  |  numero            |
| curso           |      +------------------------+  +--------------------+
| división        |
+-----------------+                                                                                                                     
+-------------------+                                                    
|   materia         |                                                        
+-------------------+                                                       
|  id-materia  (PK) |
|  nombre           |
|  curso            |
| división          |
| ciclo             |
+-------------------+      

'''


