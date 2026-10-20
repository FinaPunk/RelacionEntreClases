# Tarea: Relaciones entre Clases en POO
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Caso 1: Gestión de Asignaturas Universitarias
Descripción del Modelo
  Este sistema administra los departamentos, profesores, asignaturas, sesiones de clases y un gestor académico, aplicando las relaciones de asociación, agregación y composición según las restricciones semánticas del dominio.

Clases, Atributos y Métodos
1. Departamento
   Atributos: nombre(String), codigo(String)
   Métodos: agregarProfesor(), listarProfesores()
2. Profesor
   Atributos: rut(String), nombre(String), especialidad(String)
   Métodos: impartirClase()
3. Asignatura
   Atributos: codigo(String), nombre(String), creditos(int)
   Métodos: agregarSesion()
4. SesionDeClase
   Atributos: numeroSesion(int), horario(String), sala(String)
   Métodos: iniciarSesion()
5. GestorAcademico
   Atributos: nombreEncargado(String)
   Métodos: registrarAsignatura(), consultarAsignatura()

Relaciones y Multiplicidades
Departamento y Profesor (Agregación): `1` Departamento agrupa `1..*` Profesores. Los profesores existen de forma independiente.
Profesor y Asignatura (Asociación): `1..*` Profesores imparten asignaturas, y cada Asignatura tiene `1` Profesor responsable.
Asignatura y SesionDeClase (Composición): `1` Asignatura está compuesta por `1..*` Sesiones de Clase. Si la asignatura se elimina, las sesiones desaparecen.
GestorAcademico y Asignatura (Agregación): `1` Gestor Académico mantiene un registro de `0..*` Asignaturas. Las asignaturas pueden transferirse de gestor sin dejar de existir.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Caso 2: Gestión de un Supermercado

Descripción del Modelo
  Este sistema administra el supermercado, sus secciones, empleados, productos, el inventario y un verificador de stock temporal, aplicando relaciones estructurales y de dependencia.

Clases, Atributos y Métodos
1. Supermercado
   Atributos: nombre(String), direccion(String)
   Métodos: abrirSupermercado()
2. Empleado
   Atributos: rut(String), nombre(String), cargo(String)
   Métodos: trabajar()
3. Seccion
   Atributos: nombre(String), codigoSeccion(String)
   Métodos: agregarProducto()
4. Producto
   Atributos: sku(String), nombre(String), precio(double), stock(int)
   Métodos: actualizarStock()
5. GestorInventario
   Atributos: idGestor(String)
   Métodos:consultarDisponibilidad()
6. VerificadorStock
   Atributos: idVerificador(String)
   Métodos: verificar()

Relaciones y Multiplicidades
Supermercado y Empleado (Agregación): `1` Supermercado agrupa `1..*` Empleados independientes.
Supermercado y Seccion (Composición): `1` Supermercado está compuesto por `1..*` Secciones. Si el supermercado desaparece, las secciones también lo hacen.
Seccion y Producto (Asociación): `1..*` Secciones exhiben `1..*` Productos (relación M:N). Los productos existen independientemente de las secciones.
GestorInventario y Producto (Asociación): `1` Gestor de Inventario mantiene un registro de `0..*` Productos.
GestorInventario y VerificadorStock (Dependencia): El gestor utiliza temporalmente al verificador de stock en una operación, sin mantenerlo como atributo.
