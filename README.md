# pur2025fmeduy
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PUR 2025 - FmedUy</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-blue: #0056b3;
            --light-blue: #e6f0ff;
            --white: #ffffff;
            --light-gray: #f5f5f5;
            --border-color: #ddd;
            --text-dark: #333;
            --text-light: #666;
            --success: #28a745;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f9f9f9;
            color: var(--text-dark);
            line-height: 1.6;
        }
        
        .app-container {
            max-width: 100%;
            margin: 0 auto;
            background: var(--white);
            min-height: 100vh;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
        }
        
        .header {
            background: var(--primary-blue);
            color: var(--white);
            padding: 15px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .logo-container {
            display: flex;
            align-items: center;
        }
        
        .logo {
            width: 40px;
            height: 40px;
            background: var(--white);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 10px;
            font-weight: bold;
            color: var(--primary-blue);
        }
        
        .app-title {
            font-size: 18px;
            font-weight: 600;
        }
        
        .user-actions {
            display: flex;
            gap: 15px;
        }
        
        .user-actions button {
            background: none;
            border: none;
            color: var(--white);
            font-size: 16px;
            cursor: pointer;
        }
        
        .main-content {
            display: flex;
            flex-direction: column;
            padding: 20px;
        }
        
        .calendar-nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .month-year {
            font-size: 20px;
            font-weight: 600;
            color: var(--primary-blue);
        }
        
        .nav-buttons {
            display: flex;
            gap: 10px;
        }
        
        .nav-btn {
            background: var(--light-blue);
            border: none;
            width: 35px;
            height: 35px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary-blue);
            cursor: pointer;
        }
        
        .weekdays {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            text-align: center;
            font-weight: 600;
            margin-bottom: 10px;
            color: var(--text-light);
        }
        
        .calendar-grid {
            display: grid;
            grid-template-columns: repeat(7, 1fr);
            gap: 8px;
        }
        
        .calendar-day {
            min-height: 100px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 8px;
            background: var(--white);
            position: relative;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .calendar-day:hover {
            background: var(--light-blue);
        }
        
        .day-number {
            position: absolute;
            top: 8px;
            right: 8px;
            font-size: 14px;
            font-weight: 600;
        }
        
        .today {
            background: var(--light-blue);
            border: 2px solid var(--primary-blue);
        }
        
        .task-indicator {
            width: 100%;
            margin-top: 20px;
        }
        
        .task-item {
            font-size: 12px;
            padding: 4px;
            background: #f0f7ff;
            border-left: 3px solid var(--primary-blue);
            margin-bottom: 4px;
            border-radius: 3px;
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
        }
        
        .add-task-btn {
            position: fixed;
            bottom: 30px;
            right: 30px;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: var(--primary-blue);
            color: var(--white);
            border: none;
            font-size: 24px;
            cursor: pointer;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }
        
        .modal-content {
            background: var(--white);
            width: 90%;
            max-width: 500px;
            border-radius: 12px;
            padding: 25px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.15);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .modal-title {
            font-size: 20px;
            color: var(--primary-blue);
            font-weight: 600;
        }
        
        .close-btn {
            background: none;
            border: none;
            font-size: 22px;
            cursor: pointer;
            color: var(--text-light);
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
        }
        
        .form-control {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border-color);
            border-radius: 6px;
            font-size: 16px;
        }
        
        .form-actions {
            display: flex;
            justify-content: flex-end;
            gap: 10px;
            margin-top: 20px;
        }
        
        .btn {
            padding: 10px 20px;
            border-radius: 6px;
            border: none;
            font-size: 16px;
            cursor: pointer;
            font-weight: 500;
        }
        
        .btn-primary {
            background: var(--primary-blue);
            color: var(--white);
        }
        
        .btn-secondary {
            background: var(--light-gray);
            color: var(--text-dark);
        }
        
        .file-attachment {
            display: flex;
            align-items: center;
            margin-top: 10px;
            padding: 8px;
            background: var(--light-gray);
            border-radius: 6px;
        }
        
        .file-attachment i {
            margin-right: 10px;
            color: var(--primary-blue);
        }
        
        .reminder-indicator {
            position: absolute;
            bottom: 8px;
            left: 8px;
            color: var(--success);
            font-size: 12px;
        }
        
        .empty-day {
            border: none;
            background: transparent;
            cursor: default;
        }
        
        .empty-day:hover {
            background: transparent;
        }
        
        @media (max-width: 768px) {
            .calendar-day {
                min-height: 80px;
            }
            
            .task-item {
                font-size: 11px;
            }
        }
    </style>
</head>
<body>
    <div class="app-container">
        <header class="header">
            <div class="logo-container">
                <div class="logo">FM</div>
                <h1 class="app-title">PUR 2025 - FmedUy</h1>
            </div>
            <div class="user-actions">
                <button title="Buscar"><i class="fas fa-search"></i></button>
                <button title="Configuración"><i class="fas fa-cog"></i></button>
            </div>
        </header>
        
        <main class="main-content">
            <div class="calendar-nav">
                <div class="month-year">Agosto 2025</div>
                <div class="nav-buttons">
                    <button class="nav-btn"><i class="fas fa-chevron-left"></i></button>
                    <button class="nav-btn">Hoy</button>
                    <button class="nav-btn"><i class="fas fa-chevron-right"></i></button>
                </div>
            </div>
            
            <div class="weekdays">
                <div>Dom</div>
                <div>Lun</div>
                <div>Mar</div>
                <div>Mié</div>
                <div>Jue</div>
                <div>Vie</div>
                <div>Sáb</div>
            </div>
            
            <div class="calendar-grid">
                <!-- Días vacíos para alinear el primer día -->
                <div class="calendar-day empty-day"></div>
                <div class="calendar-day empty-day"></div>
                <div class="calendar-day empty-day"></div>
                <div class="calendar-day empty-day"></div>
                
                <!-- Días del mes -->
                <div class="calendar-day today">
                    <span class="day-number">1</span>
                    <div class="task-indicator">
                        <div class="task-item">Reunión de planificación</div>
                        <div class="task-item">Entrega de informe</div>
                    </div>
                    <div class="reminder-indicator">
                        <i class="fas fa-bell"></i>
                    </div>
                </div>
                <div class="calendar-day">
                    <span class="day-number">2</span>
                </div>
                <div class="calendar-day">
                    <span class="day-number">3</span>
                </div>
                
                <!-- Más días... -->
                <div class="calendar-day">
                    <span class="day-number">4</span>
                    <div class="task-indicator">
                        <div class="task-item">Presentación de avances</div>
                    </div>
                </div>
                <div class="calendar-day">
                    <span class="day-number">5</span>
                </div>
                <div class="calendar-day">
                    <span class="day-number">6</span>
                    <div class="task-indicator">
                        <div class="task-item">Revisión de documentos</div>
                    </div>
                    <div class="reminder-indicator">
                        <i class="fas fa-bell"></i>
                    </div>
                </div>
                <div class="calendar-day">
                    <span class="day-number">7</span>
                </div>
                
                <!-- Segunda semana -->
                <div class="calendar-day">
                    <span class="day-number">8</span>
                </div>
                <div class="calendar-day">
                    <span class="day-number">9</span>
                    <div class="task-indicator">
                        <div class="task-item">Entrega de resultados</div>
                    </div>
                </div>
                <div class="calendar-day">
                    <span class="day-number">10</span>
                </div>
                <div class="calendar-day">
                    <span class="day-number">11</span>
                    <div class="task-indicator">
                        <div class="task-item">Seminario de investigación</div>
                    </div>
                    <div class="reminder-indicator">
                        <i class="fas fa-bell"></i>
                    </div>
                </div>
                <div class="calendar-day">
                    <span class="day-number">12</span>
                </div>
                <div class="calendar-day">
                    <span class="day-number">13</span>
                </div>
                <div class="calendar-day">
                    <span class="day-number">14</span>
                    <div class="task-indicator">
                        <div class="task-item">Cierre de proyecto</div>
                    </div>
                </div>
                
                <!-- Más días... (simulados) -->
                <!-- En una aplicación real, estos días se generarían dinámicamente -->
            </div>
            
            <button class="add-task-btn" id="addTaskBtn">
                <i class="fas fa-plus"></i>
            </button>
        </main>
    </div>
    
    <!-- Modal para agregar/editar tarea -->
    <div class="modal" id="taskModal">
        <div class="modal-content">
            <div class="modal-header">
                <h2 class="modal-title">Nueva Tarea</h2>
                <button class="close-btn">&times;</button>
            </div>
            <form id="taskForm">
                <div class="form-group">
                    <label for="taskTitle">Título de la tarea</label>
                    <input type="text" id="taskTitle" class="form-control" placeholder="Ingrese el título">
                </div>
                <div class="form-group">
                    <label for="taskDate">Fecha</label>
                    <input type="date" id="taskDate" class="form-control">
                </div>
                <div class="form-group">
                    <label for="taskDescription">Descripción</label>
                    <textarea id="taskDescription" class="form-control" rows="3" placeholder="Agregar detalles"></textarea>
                </div>
                <div class="form-group">
                    <label for="taskLink">Enlace web</label>
                    <input type="url" id="taskLink" class="form-control" placeholder="https://ejemplo.com">
                </div>
                <div class="form-group">
                    <label>Archivo adjunto</label>
                    <input type="file" id="taskFile" class="form-control">
                    <div class="file-attachment">
                        <i class="fas fa-file-pdf"></i>
                        <span>Informe.pdf</span>
                    </div>
                </div>
                <div class="form-group">
                    <label for="taskReminder">Recordatorio</label>
                    <input type="datetime-local" id="taskReminder" class="form-control">
                </div>
                <div class="form-actions">
                    <button type="button" class="btn btn-secondary">Cancelar</button>
                    <button type="submit" class="btn btn-primary">Guardar</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // Funcionalidad básica para demostración
        document.addEventListener('DOMContentLoaded', function() {
            const addTaskBtn = document.getElementById('addTaskBtn');
            const taskModal = document.getElementById('taskModal');
            const closeBtn = document.querySelector('.close-btn');
            const cancelBtn = document.querySelector('.btn-secondary');
            
            // Abrir modal
            addTaskBtn.addEventListener('click', function() {
                taskModal.style.display = 'flex';
            });
            
            // Cerrar modal
            function closeModal() {
                taskModal.style.display = 'none';
            }
            
            closeBtn.addEventListener('click', closeModal);
            cancelBtn.addEventListener('click', closeModal);
            
            // Cerrar modal al hacer clic fuera del contenido
            taskModal.addEventListener('click', function(e) {
                if (e.target === taskModal) {
                    closeModal();
                }
            });
            
            // Enviar formulario
            document.getElementById('taskForm').addEventListener('submit', function(e) {
                e.preventDefault();
                alert('Tarea guardada exitosamente');
                closeModal();
            });
            
            // Simular clics en días del calendario
            const calendarDays = document.querySelectorAll('.calendar-day:not(.empty-day)');
            calendarDays.forEach(day => {
                day.addEventListener('click', function() {
                    const dayNumber = this.querySelector('.day-number').textContent;
                    alert(`Has seleccionado el día ${dayNumber} de Agosto`);
                });
            });
        });
    </script>
</body>
</html>
