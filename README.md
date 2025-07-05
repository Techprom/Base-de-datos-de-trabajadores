<!DOCTYPE html>
<html lang="es">

<head>
    <meta charset="UTF-8">
    <title>Sistema de Visualización de Datos</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 2em;
            background: #f4f4f4;
            color: #333;
        }

        #loginForm,
        #dataSection,
        #salarioSection {
            max-width: 1000px;
            margin: auto;
            background: white;
            padding: 2em;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 1em;
        }

        th,
        td {
            border: 1px solid #ccc;
            padding: 8px;
            text-align: left;
        }

        th {
            background-color: #007B8F;
            color: white;
        }

        .hidden {
            display: none;
        }

        h2,
        h3 {
            color: #007B8F;
        }

        pre {
            background: #eee;
            padding: 1em;
            white-space: pre-wrap;
            border-radius: 6px;
        }

        .csv-section {
            margin-top: 2em;
        }

        input,
        button {
            padding: 10px;
            margin-top: 10px;
            width: 100%;
            box-sizing: border-box;
            border-radius: 4px;
            border: 1px solid #ccc;
        }

        button {
            background-color: #007B8F;
            color: white;
            cursor: pointer;
        }

        button:hover {
            background-color: #005f6a;
        }
    </style>
</head>

<body>

    <div id="loginForm">
        <h2>Inicio de Sesión</h2>
        <label>Usuario: <input type="text" id="username"></label><br><br>
        <label>Contraseña: <input type="password" id="password"></label><br><br>
        <button onclick="login()">Ingresar</button>
        <p id="errorMsg" style="color: red;"></p>
    </div>

    <div id="dataSection" class="hidden">
        <h2>Datos Cargados</h2>
        <div id="csvData">
            <!-- Aquí van las secciones de tabla insertadas anteriormente -->
            <h3>Trabajadores</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>nombre</th>
                        <th>cedula</th>
                        <th>fecha_ingreso</th>
                        <th>cargo</th>
                        <th>estado</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Carlos Pérez</td>
                        <td>11-2246</td>
                        <td>2013-09-26 00:00:00</td>
                        <td>Gerente</td>
                        <td>Inactivo</td>
                    </tr>
                    <tr>
                        <td>María Rodríguez</td>
                        <td>11-6828</td>
                        <td>2011-05-02 00:00:00</td>
                        <td>Ingeniero</td>
                        <td>Activo</td>
                    </tr>
                    <tr>
                        <td>Juan Gómez</td>
                        <td>10-6948</td>
                        <td>2020-04-13 00:00:00</td>
                        <td>Analista</td>
                        <td>Activo</td>
                    </tr>
                    <tr>
                        <td>Ana Fernández</td>
                        <td>6-4215</td>
                        <td>2019-10-14 00:00:00</td>
                        <td>Desarrollador</td>
                        <td>Inactivo</td>
                    </tr>
                    <tr>
                        <td>Luis Martínez</td>
                        <td>9-7465</td>
                        <td>2013-06-23 00:00:00</td>
                        <td>Diseñador</td>
                        <td>Activo</td>
                    </tr>
                    <tr>
                        <td>Carmen López</td>
                        <td>13-6503</td>
                        <td>2019-05-27 00:00:00</td>
                        <td>Administrador</td>
                        <td>Inactivo</td>
                    </tr>
                    <tr>
                        <td>José Sánchez</td>
                        <td>2-2383</td>
                        <td>2012-03-03 00:00:00</td>
                        <td>Contador</td>
                        <td>Activo</td>
                    </tr>
                    <tr>
                        <td>Laura Díaz</td>
                        <td>12-8757</td>
                        <td>2017-11-26 00:00:00</td>
                        <td>Consultor</td>
                        <td>Inactivo</td>
                    </tr>
                    <tr>
                        <td>Miguel Ramírez</td>
                        <td>5-9045</td>
                        <td>2014-06-08 00:00:00</td>
                        <td>Técnico</td>
                        <td>Activo</td>
                    </tr>
                    <tr>
                        <td>Elena Torres</td>
                        <td>13-4655</td>
                        <td>2010-09-21 00:00:00</td>
                        <td>Supervisor</td>
                        <td>Activo</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="csv-section">
            <h3>Asistencia</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>fecha</th>
                        <th>hora_entrada</th>
                        <th>hora_salida</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>09/26/2013</td>
                        <td>7:00:00</td>
                        <td>16:00:00</td>
                    </tr>
                    <tr>
                        <td>05/02/2011</td>
                        <td>7:00:00</td>
                        <td>16:00:00</td>
                    </tr>
                    <tr>
                        <td>04/13/2020</td>
                        <td>7:00:00</td>
                        <td>16:00:00</td>
                    </tr>
                    <tr>
                        <td>10/14/2019</td>
                        <td>7:00:00</td>
                        <td>16:00:00</td>
                    </tr>
                    <tr>
                        <td>06/23/2013</td>
                        <td>7:00:00</td>
                        <td>16:00:00</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="csv-section">
            <h3>Atrasos</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>nombre</th>
                        <th>fecha</th>
                        <th>hora_entrada</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Carlos Pérez</td>
                        <td>01/01/2023</td>
                        <td>7:00:00</td>
                    </tr>
                    <tr>
                        <td>María Rodríguez</td>
                        <td>01/02/2023</td>
                        <td>7:00:00</td>
                    </tr>
                    <tr>
                        <td>Juan Gómez</td>
                        <td>01/03/2023</td>
                        <td>7:00:00</td>
                    </tr>
                    <tr>
                        <td>Ana Fernández</td>
                        <td>01/04/2023</td>
                        <td>7:00:00</td>
                    </tr>
                    <tr>
                        <td>Luis Martínez</td>
                        <td>01/05/2023</td>
                        <td>7:00:00</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="csv-section">
            <h3>Historial Laboral</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>fecha_inicio</th>
                        <th>fecha_fin</th>
                        <th>motivo_salida</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>09/26/2013</td>
                        <td>12/19/2020</td>
                        <td>Despido</td>
                    </tr>
                    <tr>
                        <td>05/02/2011</td>
                        <td></td>
                        <td></td>
                    </tr>
                    <tr>
                        <td>04/13/2020</td>
                        <td></td>
                        <td></td>
                    </tr>
                    <tr>
                        <td>10/14/2019</td>
                        <td>12/19/2020</td>
                        <td>Despido</td>
                    </tr>
                    <tr>
                        <td>06/23/2013</td>
                        <td></td>
                        <td></td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="csv-section">
            <h3>Historial Laboral Corregido</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>fecha_inicio</th>
                        <th>fecha_fin</th>
                        <th>motivo_salida</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>09/26/2013</td>
                        <td>12/19/2020</td>
                        <td>Despido</td>
                    </tr>
                    <tr>
                        <td>05/02/2011</td>
                        <td></td>
                        <td></td>
                    </tr>
                    <tr>
                        <td>04/13/2020</td>
                        <td></td>
                        <td></td>
                    </tr>
                    <tr>
                        <td>10/14/2019</td>
                        <td>12/19/2020</td>
                        <td>Despido</td>
                    </tr>
                    <tr>
                        <td>06/23/2013</td>
                        <td></td>
                        <td></td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="csv-section">
            <h3>Pagos</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>monto_pagado</th>
                        <th>fecha_pago</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>1000.00</td>
                        <td>12/19/2020</td>
                    </tr>
                    <tr>
                        <td>900.00</td>
                        <td>06/30/2025</td>
                    </tr>
                    <tr>
                        <td>900.00</td>
                        <td>06/30/2025</td>
                    </tr>
                    <tr>
                        <td>1000.00</td>
                        <td>12/19/2020</td>
                    </tr>
                    <tr>
                        <td>900.00</td>
                        <td>06/30/2025</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="csv-section">
            <h3>Quincenas</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>fecha_inicio</th>
                        <th>fecha_fin</th>
                        <th>total_horas</th>
                        <th>salario_calculado</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>09/26/2013</td>
                        <td>12/19/2020</td>
                        <td>2641</td>
                        <td>808.75</td>
                    </tr>
                    <tr>
                        <td>05/02/2011</td>
                        <td>06/30/2025</td>
                        <td>5173</td>
                        <td>734.75</td>
                    </tr>
                    <tr>
                        <td>04/13/2020</td>
                        <td>06/30/2025</td>
                        <td>1904</td>
                        <td>734.75</td>
                    </tr>
                    <tr>
                        <td>10/14/2019</td>
                        <td>12/19/2020</td>
                        <td>432</td>
                        <td>808.75</td>
                    </tr>
                    <tr>
                        <td>06/23/2013</td>
                        <td>06/30/2025</td>
                        <td>4390</td>
                        <td>734.75</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="csv-section">
            <h3>Resumen Quincenal</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>nombre</th>
                        <th>fecha_inicio</th>
                        <th>fecha_fin</th>
                        <th>total_horas</th>
                        <th>salario_calculado</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Carlos Pérez</td>
                        <td>09/26/2013</td>
                        <td>12/19/2020</td>
                        <td>2641</td>
                        <td>808.75</td>
                    </tr>
                    <tr>
                        <td>María Rodríguez</td>
                        <td>05/02/2011</td>
                        <td>06/30/2025</td>
                        <td>5173</td>
                        <td>734.75</td>
                    </tr>
                    <tr>
                        <td>Juan Gómez</td>
                        <td>04/13/2020</td>
                        <td>06/30/2025</td>
                        <td>1904</td>
                        <td>734.75</td>
                    </tr>
                    <tr>
                        <td>Ana Fernández</td>
                        <td>10/14/2019</td>
                        <td>12/19/2020</td>
                        <td>432</td>
                        <td>808.75</td>
                    </tr>
                    <tr>
                        <td>Luis Martínez</td>
                        <td>06/23/2013</td>
                        <td>06/30/2025</td>
                        <td>4390</td>
                        <td>734.75</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="csv-section">
            <h3>Rotaciones</h3>
            <table border="1">
                <thead>
                    <tr>
                        <th>semana</th>
                        <th>rol_asignado</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>09/23/2013</td>
                        <td>Administrador</td>
                    </tr>
                    <tr>
                        <td>05/02/2011</td>
                        <td>Supervisor</td>
                    </tr>
                    <tr>
                        <td>04/13/2020</td>
                        <td>Administrador</td>
                    </tr>
                    <tr>
                        <td>10/14/2019</td>
                        <td>Operador</td>
                    </tr>
                    <tr>
                        <td>06/17/2013</td>
                        <td>Administrador</td>
                    </tr>
                </tbody>
            </table>
        </div>
        <h2>Explicación del Código SQL</h2>
        <pre id="sqlExplanation"></pre>
    </div>

    <div id="salarioSection" class="hidden">
        <h2>Calculadora de Salario con Descuentos</h2>
        <label>Salario Bruto Mensual: <input type="number" id="salarioBruto" placeholder="Ej. 1000"></label><br>
        <button onclick="calcularSalario()">Calcular Salario Neto</button>
        <div id="resultadoSalario"></div>
    </div>

    <script>
        function login() {
            const user = document.getElementById("username").value;
            const pass = document.getElementById("password").value;
            if (user === "Lauris2025" && pass === "LauLau2025*") {
                document.getElementById("loginForm").classList.add("hidden");
                document.getElementById("dataSection").classList.remove("hidden");
                document.getElementById("salarioSection").classList.remove("hidden");
                loadSQLExplanation();
            } else {
                document.getElementById("errorMsg").innerText = "Usuario o contraseña incorrectos.";
            }
        }

        function loadSQLExplanation() {
            const explanation = `1. Eliminar vistas y tablas existentes para evitar duplicaciones.
2. Crear tablas fundamentales del sistema: trabajadores, asistencia, pagos, historial, quincenas y rotaciones.
3. Aplicar validaciones lógicas como fechas coherentes y chequear valores positivos.
4. Crear vistas que resumen información útil:
   - \"horas_por_dia\": calcula horas trabajadas por fecha.
   - \"resumen_quincenal\": une quincenas con datos de trabajadores.
   - \"estado_trabajadores\": muestra su estado laboral.
   - \"ausencias\": muestra fechas sin entrada registrada.
   - \"atrasos\": muestra entradas después de las 7:00 AM.`;
            document.getElementById("sqlExplanation").innerText = explanation;
        }

        function calcularSalario() {
            const bruto = parseFloat(document.getElementById("salarioBruto").value);
            if (isNaN(bruto) || bruto <= 0) {
                document.getElementById("resultadoSalario").innerText = "Por favor, ingrese un salario válido.";
                return;
            }
            const seguroSocial = bruto * 0.0975;
            const seguroEducativo = bruto * 0.0125;
            const totalDescuentos = seguroSocial + seguroEducativo;
            const neto = bruto - totalDescuentos;
            document.getElementById("resultadoSalario").innerHTML = `
      <p><strong>Seguro Social (9.75%):</strong> B/. ${seguroSocial.toFixed(2)}</p>
      <p><strong>Seguro Educativo (1.25%):</strong> B/. ${seguroEducativo.toFixed(2)}</p>
      <p><strong>Total Descuentos:</strong> B/. ${totalDescuentos.toFixed(2)}</p>
      <p><strong>Salario Neto:</strong> B/. ${neto.toFixed(2)}</p>
    `;
        }
    </script>

</body>

</html>
