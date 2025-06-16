<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Índice de Riesgo Social</title>
    <!-- CORRECCIÓN: URLs actualizadas para compatibilidad con GitHub Pages -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js@3.9.1/dist/chart.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background: linear-gradient(135deg, #e0eafc, #cfdef3);
            padding: 40px 20px;
            color: #333;
            min-height: 100vh;
        }

        .container {
            max-width: 960px;
            margin: 40px auto;
            background: rgba(255, 255, 255, 0.9);
            padding: 30px;
            border-radius: 16px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
        }

        h2 {
            color: #2c3e50;
            text-align: center;
            margin-bottom: 30px;
        }

        label {
            display: block;
            margin-top: 15px;
            font-weight: 500;
            color: #34495e;
        }

        input[type="number"],
        select {
            width: 100%;
            padding: 12px;
            border-radius: 8px;
            border: 1px solid #ccc;
            margin-top: 8px;
            font-size: 1em;
            box-sizing: border-box;
            background: #f8f9fa;
        }

        .button-group {
            display: flex;
            gap: 15px;
            margin-top: 25px;
            justify-content: center;
            flex-wrap: wrap;
        }

        button {
            background-color: #3498db;
            color: white;
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            flex-grow: 1;
            max-width: 250px;
        }

        button:hover {
            background-color: #2980b9;
            transform: translateY(-2px);
        }

        button:active {
            transform: translateY(0);
        }

        #irsChartContainer {
            display: none;
            margin-top: 30px;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        canvas {
            max-height: 400px;
            display: block;
        }

        #recomendacion {
            margin-top: 30px;
            padding: 20px;
            border-left: 6px solid;
            border-radius: 10px;
            line-height: 1.6;
            font-size: 1.1em;
            display: none;
        }

        #recomendacion.low {
            background: #ecf9ec;
            border-color: #2e7d32;
            color: #2e7d32;
        }

        #recomendacion.medium {
            background: #fffbe6;
            border-color: #fdd835;
            color: #fbc02d;
        }

        #recomendacion.high {
            background: #ffebe6;
            border-color: #e74c3c;
            color: #e74c3c;
        }

        #alertaRoja {
            margin-top: 25px;
            font-weight: bold;
            color: #c0392b;
            font-size: 1.4em;
            display: none;
            text-align: center;
            padding: 15px;
            background-color: #fdeded;
            border-radius: 10px;
            border: 2px solid #e74c3c;
        }

        table {
            width: 100%;
            margin-top: 30px;
            border-collapse: collapse;
            background: #fff;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            display: none;
        }

        th,
        td {
            border: 1px solid #eee;
            padding: 15px;
            text-align: left;
            vertical-align: middle;
        }

        th {
            background-color: #3498db;
            color: white;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        tr:nth-child(even) {
            background-color: #f8f8f8;
        }

        .hidden {
            display: none !important;
        }

        .loading {
            display: none;
            text-align: center;
            padding: 20px;
            color: #3498db;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Calculadora de Índice de Riesgo Social (IRS)</h2>

        <form id="irsForm">
            <label for="ingresos">Ingresos Mensuales Netos ($):</label>
            <input type="number" id="ingresos" step="0.01" min="0" required placeholder="Ej: 1500.00">

            <label for="gastos">Gastos Mensuales Totales ($):</label>
            <input type="number" id="gastos" step="0.01" min="0" required placeholder="Ej: 1200.00">

            <label for="dependientes">Número de Dependientes (ej. hijos, adultos mayores):</label>
            <input type="number" id="dependientes" min="0" required value="0">

            <label for="tipoVivienda">Tipo de Vivienda:</label>
            <select id="tipoVivienda" required>
                <option value="propia">Propia (Pagada)</option>
                <option value="hipoteca">Propia (Con Hipoteca)</option>
                <option value="alquilada">Alquilada</option>
                <option value="prestada">Prestada / Familiar</option>
            </select>

            <div class="button-group">
                <button type="submit">Calcular IRS</button>
                <button type="button" id="cargarExcelBtn">Cargar Datos desde Excel</button>
                <input type="file" id="excelFileInput" accept=".xlsx, .xls" class="hidden">
            </div>
        </form>

        <div class="loading" id="cargando">Cargando datos...</div>

        <div id="irsChartContainer">
            <canvas id="irsChart"></canvas>
        </div>

        <div id="recomendacion">
            <strong>Recomendación:</strong> <span id="recomendacionTexto"></span>
        </div>

        <div id="alertaRoja">
            ¡ATENCIÓN! Tu Índice de Riesgo Social es ALTO. Se recomienda buscar asesoría financiera urgente.
        </div>

        <div id="detalleGastos" class="hidden">
            <h3>Detalle de Gastos</h3>
            <p>Aquí podrías ver un desglose más detallado de tus gastos si se proporcionaran más categorías en el formulario o el archivo Excel.</p>
        </div>

        <table id="gastosTabla" class="hidden">
            <thead>
                <tr>
                    <th>Concepto</th>
                    <th>Monto</th>
                </tr>
            </thead>
            <tbody id="gastosTableBody">
                </tbody>
        </table>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            // --- Elementos del DOM ---
            const irsForm = document.getElementById('irsForm');
            const ingresosInput = document.getElementById('ingresos');
            const gastosInput = document.getElementById('gastos');
            const dependientesInput = document.getElementById('dependientes');
            const tipoViviendaSelect = document.getElementById('tipoVivienda');
            const cargandoDiv = document.getElementById('cargando');

            // Elementos de resultado
            const recomendacionDiv = document.getElementById('recomendacion');
            const recomendacionTexto = document.getElementById('recomendacionTexto');
            const alertaRojaDiv = document.getElementById('alertaRoja');
            const detalleGastosDiv = document.getElementById('detalleGastos');
            const gastosTabla = document.getElementById('gastosTabla');
            const gastosTableBody = document.getElementById('gastosTableBody');

            // Botones y manejo de archivos
            const cargarExcelBtn = document.getElementById('cargarExcelBtn');
            const excelFileInput = document.getElementById('excelFileInput');

            let myChart = null; // Variable para la instancia del gráfico

            // --- Función para Inicializar o Actualizar el Gráfico ---
            function updateChart(irsScore) {
                const irsChartCanvas = document.getElementById('irsChart');
                const irsChartContainer = document.getElementById('irsChartContainer');
                
                // Mostrar contenedor del gráfico
                irsChartContainer.style.display = 'block';

                if (!irsChartCanvas) {
                    console.error("Error: El elemento canvas con ID 'irsChart' no se encontró.");
                    return;
                }

                const ctx = irsChartCanvas.getContext('2d');

                if (myChart) {
                    // Actualizar un gráfico existente
                    myChart.data.datasets[0].data[0] = irsScore;
                    // Cambiar color según el riesgo
                    let color;
                    if (irsScore < 20) {
                        color = 'rgba(46, 178, 107, 0.7)'; // Verde para riesgo bajo
                    } else if (irsScore < 50) {
                        color = 'rgba(255, 193, 7, 0.7)'; // Amarillo para riesgo medio
                    } else {
                        color = 'rgba(231, 76, 60, 0.7)'; // Rojo para riesgo alto
                    }
                    myChart.data.datasets[0].backgroundColor[0] = color;
                    myChart.update();
                } else {
                    // Destruir gráfico existente si hay uno
                    if (Chart.getChart(irsChartCanvas)) {
                        Chart.getChart(irsChartCanvas).destroy();
                    }
                    
                    // Inicializar un nuevo gráfico
                    myChart = new Chart(ctx, {
                        type: 'bar',
                        data: {
                            labels: ['Índice de Riesgo Social'],
                            datasets: [{
                                label: 'IRS',
                                data: [irsScore],
                                backgroundColor: ['rgba(54, 162, 235, 0.6)'],
                                borderColor: ['rgba(54, 162, 235, 1)'],
                                borderWidth: 1
                            }]
                        },
                        options: {
                            responsive: true,
                            maintainAspectRatio: false,
                            scales: {
                                y: {
                                    beginAtZero: true,
                                    max: 100,
                                    ticks: {
                                        callback: function(value) {
                                            return value + '%';
                                        }
                                    }
                                }
                            },
                            plugins: {
                                legend: {
                                    display: false
                                },
                                title: {
                                    display: true,
                                    text: 'Valor del Índice de Riesgo Social (IRS)',
                                    font: {
                                        size: 16
                                    }
                                },
                                tooltip: {
                                    callbacks: {
                                        label: function(context) {
                                            return `Riesgo: ${context.parsed.y}%`;
                                        }
                                    }
                                }
                            }
                        }
                    });
                }
            }

            // --- Función Principal de Cálculo del IRS ---
            function calcularIRS(event) {
                event.preventDefault();

                // Validación mejorada
                if (!ingresosInput.value.trim() || !gastosInput.value.trim()) {
                    alert('Por favor, completa todos los campos obligatorios.');
                    return;
                }

                const ingresos = parseFloat(ingresosInput.value);
                const gastos = parseFloat(gastosInput.value);
                const dependientes = parseInt(dependientesInput.value);
                const tipoVivienda = tipoViviendaSelect.value;

                // Validaciones básicas
                if (isNaN(ingresos) {
                    alert('Ingresos no válidos. Por favor ingresa un número válido.');
                    ingresosInput.focus();
                    return;
                }
                
                if (isNaN(gastos)) {
                    alert('Gastos no válidos. Por favor ingresa un número válido.');
                    gastosInput.focus();
                    return;
                }
                
                if (isNaN(dependientes)) {
                    alert('Número de dependientes no válido. Por favor ingresa un número entero.');
                    dependientesInput.focus();
                    return;
                }

                let irs = 0;

                // 1. Componente de Ingresos vs. Gastos
                if (ingresos === 0) {
                    irs += 50;
                } else if (gastos > ingresos) {
                    irs += 40;
                } else {
                    const ratioGastoIngreso = gastos / ingresos;
                    if (ratioGastoIngreso >= 0.8) {
                        irs += 25;
                    } else if (ratioGastoIngreso >= 0.6) {
                        irs += 10;
                    }
                }

                // 2. Componente de Dependientes
                irs += dependientes * 5;

                // 3. Componente de Tipo de Vivienda
                switch (tipoVivienda) {
                    case 'alquilada':
                        irs += 15;
                        break;
                    case 'hipoteca':
                        irs += 10;
                        break;
                    case 'prestada':
                        irs += 5;
                        break;
                }

                // Limitar el IRS a un máximo de 100
                irs = Math.min(irs, 100);

                // Mostrar Resultados
                updateChart(irs);
                mostrarRecomendaciones(irs);
            }

            // --- Función para Mostrar Recomendaciones ---
            function mostrarRecomendaciones(irs) {
                recomendacionDiv.style.display = 'block';
                alertaRojaDiv.style.display = 'none';
                recomendacionDiv.className = 'recomendacion';

                let textoRecomendacion = '';
                if (irs < 20) {
                    textoRecomendacion = 'Tu índice de riesgo social es BAJO. ¡Felicidades! Mantén una buena gestión de tus finanzas y considera ahorrar e invertir para el futuro.';
                    recomendacionDiv.classList.add('low');
                } else if (irs < 50) {
                    textoRecomendacion = 'Tu índice de riesgo social es MEDIO. Es aconsejable revisar tus gastos y posiblemente buscar formas de aumentar tus ingresos o reducir dependencias para mejorar tu estabilidad.';
                    recomendacionDiv.classList.add('medium');
                } else {
                    textoRecomendacion = 'Tu índice de riesgo social es ALTO. Es urgente que revises tu situación financiera. Busca asesoría profesional, evalúa tus gastos, y considera opciones para generar más ingresos o acceder a apoyos sociales.';
                    alertaRojaDiv.style.display = 'block';
                    recomendacionDiv.classList.add('high');
                }
                recomendacionTexto.textContent = textoRecomendacion;
            }

            // --- Funcionalidad de Carga de Excel ---
            cargarExcelBtn.addEventListener('click', () => {
                excelFileInput.click();
            });

            excelFileInput.addEventListener('change', (event) => {
                const file = event.target.files[0];
                if (!file) return;

                cargandoDiv.style.display = 'block';
                
                const reader = new FileReader();
                reader.onload = (e) => {
                    try {
                        const data = new Uint8Array(e.target.result);
                        const workbook = XLSX.read(data, { type: 'array' });
                        
                        if (workbook.SheetNames.length === 0) {
                            throw new Error('El archivo no contiene hojas');
                        }
                        
                        const firstSheetName = workbook.SheetNames[0];
                        const worksheet = workbook.Sheets[firstSheetName];
                        const json = XLSX.utils.sheet_to_json(worksheet);
                        
                        if (json.length === 0) {
                            throw new Error('La hoja de cálculo está vacía');
                        }
                        
                        const row = json[0];

                        // Poblar formulario
                        if (row.Ingresos !== undefined) ingresosInput.value = row.Ingresos;
                        if (row.Gastos !== undefined) gastosInput.value = row.Gastos;
                        if (row.Dependientes !== undefined) dependientesInput.value = row.Dependientes;
                        
                        if (row.Tipo_Vivienda !== undefined) {
                            const viviendaValue = String(row.Tipo_Vivienda).toLowerCase();
                            if (['propia', 'hipoteca', 'alquilada', 'prestada'].includes(viviendaValue)) {
                                tipoViviendaSelect.value = viviendaValue;
                            }
                        }

                        // Mostrar gastos detallados
                        gastosTableBody.innerHTML = '';
                        let hasDetailedExpenses = false;
                        
                        for (const key in row) {
                            if (!['Ingresos', 'Gastos', 'Dependientes', 'Tipo_Vivienda'].includes(key) && 
                                row[key] !== null && row[key] !== '') {
                                const tr = document.createElement('tr');
                                tr.innerHTML = `<td>${key}</td><td>$${parseFloat(row[key]).toFixed(2)}</td>`;
                                gastosTableBody.appendChild(tr);
                                hasDetailedExpenses = true;
                            }
                        }

                        gastosTabla.style.display = hasDetailedExpenses ? 'table' : 'none';
                        detalleGastosDiv.style.display = hasDetailedExpenses ? 'block' : 'none';
                        
                        alert('Datos cargados correctamente. Haz clic en "Calcular IRS" para ver resultados.');
                    } catch (error) {
                        console.error('Error al procesar Excel:', error);
                        alert(`Error al procesar el archivo: ${error.message}`);
                    } finally {
                        cargandoDiv.style.display = 'none';
                        excelFileInput.value = '';
                    }
                };
                
                reader.onerror = (error) => {
                    console.error('Error al leer archivo:', error);
                    alert('Error al leer el archivo. Asegúrate de que es un Excel válido.');
                    cargandoDiv.style.display = 'none';
                    excelFileInput.value = '';
                };
                
                reader.readAsArrayBuffer(file);
            });

            // --- Event Listeners ---
            irsForm.addEventListener('submit', calcularIRS);
        });
    </script>
</body>
</html>
