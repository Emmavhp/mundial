<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>El Mundialito - Sistema de Gestión de Torneos</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.css">
    <style>
    .celda-editable {
        background-color: #f8f9fa;
        border: 1px solid #ddd;
        padding: 5px;
    }
    .celda-editable:focus {
        background-color: #fff;
        border: 1px solid #80bdff;
        outline: 0;
        box-shadow: 0 0 0 0.2rem rgba(0,123,255,.25);
    }
        :root {
            --primary-color: #0056b3;
            --primary-dark: #004494;
            --secondary-color: #f8f9fa;
            --accent-color: #28a745;
            --accent-dark: #218838;
            --danger-color: #dc3545;
            --danger-dark: #c82333;
            --warning-color: #ffc107;
            --warning-dark: #e0a800;
            --info-color: #17a2b8;
            --info-dark: #138496;
            --text-color: #343a40;
            --border-color: #dee2e6;
            --light-gray: #f5f5f5;
            --gray: #6c757d;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: var(--light-gray);
            color: var(--text-color);
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            background-color: var(--primary-color);
            color: white;
            padding: 15px 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo i {
            font-size: 28px;
        }
        
        .logo h1 {
            font-size: 24px;
            font-weight: 600;
        }
        
        nav ul {
            display: flex;
            list-style: none;
            gap: 20px;
        }
        
        nav a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s;
            padding: 8px 15px;
            border-radius: 4px;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        nav a:hover {
            background-color: rgba(255,255,255,0.1);
            transform: translateY(-2px);
        }
        
        nav a i {
            font-size: 16px;
        }
        
        .card {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            margin-bottom: 20px;
            overflow: hidden;
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .card:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .card-header {
            background-color: var(--secondary-color);
            padding: 15px 20px;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .card-title {
            font-size: 18px;
            font-weight: 600;
            margin: 0;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .card-body {
            padding: 20px;
        }
        
        .btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
            padding: 8px 16px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 500;
            transition: all 0.3s;
            text-decoration: none;
        }
        
        .btn:hover {
            background-color: var(--primary-dark);
            transform: translateY(-2px);
            box-shadow: 0 3px 6px rgba(0,0,0,0.1);
        }
        
        .btn-success {
            background-color: var(--accent-color);
        }
        
        .btn-success:hover {
            background-color: var(--accent-dark);
        }
        
        .btn-danger {
            background-color: var(--danger-color);
        }
        
        .btn-danger:hover {
            background-color: var(--danger-dark);
        }
        
        .btn-warning {
            background-color: var(--warning-color);
            color: var(--text-color);
        }
        
        .btn-warning:hover {
            background-color: var(--warning-dark);
        }
        
        .btn-info {
            background-color: var(--info-color);
        }
        
        .btn-info:hover {
            background-color: var(--info-dark);
        }
        
        .btn-sm {
            padding: 5px 10px;
            font-size: 12px;
        }
        
        .table-responsive {
            overflow-x: auto;
            border-radius: 4px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.05);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            background-color: white;
        }
        
        table th, table td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid var(--border-color);
        }
        
        table th {
            background-color: var(--secondary-color);
            font-weight: 600;
            color: var(--text-color);
            position: sticky;
            top: 0;
        }
        
        table tbody tr:hover {
            background-color: rgba(0,0,0,0.02);
        }
        
        table tbody tr:last-child td {
            border-bottom: none;
        }
        
        .actions {
            display: flex;
            gap: 5px;
            justify-content: center;
        }
        
        .flag-container {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .flag {
            font-size: 20px;
        }
        
        .login-container {
            max-width: 400px;
            margin: 80px auto;
        }
        
        .form-group {
            margin-bottom: 15px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: 500;
            color: var(--text-color);
        }
        
        .form-control {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            font-size: 14px;
            transition: border-color 0.3s, box-shadow 0.3s;
        }
        
        .form-control:focus {
            border-color: var(--primary-color);
            outline: none;
            box-shadow: 0 0 0 3px rgba(0, 86, 179, 0.1);
        }
        
        .form-row {
            display: flex;
            gap: 15px;
            margin-bottom: 15px;
        }
        
        .form-row .form-group {
            flex: 1;
            margin-bottom: 0;
        }
        
        .tab-container {
            margin-top: 20px;
        }
        
        .tabs {
            display: flex;
            border-bottom: 1px solid var(--border-color);
            margin-bottom: 10px;
            overflow-x: auto;
            gap: 5px;
        }
        
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            background-color: var(--secondary-color);
            border: 1px solid var(--border-color);
            border-bottom: none;
            border-radius: 5px 5px 0 0;
            font-weight: 500;
            transition: all 0.3s;
            white-space: nowrap;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .tab:hover {
            background-color: white;
            border-bottom: 1px solid white;
            margin-bottom: -1px;
        }
        
        .tab.active {
            background-color: white;
            border-bottom: 1px solid white;
            margin-bottom: -1px;
            color: var(--primary-color);
        }
        
        .tab-content {
            display: none;
            border-radius: 0 0 8px 8px;
        }
        
        .tab-content.active {
            display: block;
            animation: fadeIn 0.3s ease-in-out;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        .match-card {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            margin-bottom: 15px;
            background-color: white;
            transition: all 0.3s;
        }
        
        .match-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.08);
        }
        
        .team {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 120px;
        }
        
        .team-flag {
            font-size: 32px;
            margin-bottom: 10px;
        }
        
        .score {
            font-size: 24px;
            font-weight: bold;
            padding: 0 20px;
            color: var(--text-color);
        }
        
        .match-info {
            text-align: center;
        }
        
        .match-date {
            color: var(--gray);
            margin: 8px 0;
        }
        
        .export-btn {
            margin: 20px 0;
            display: flex;
            justify-content: flex-end;
        }
        
        .status-badge {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 50px;
            font-size: 12px;
            font-weight: 500;
        }
        
        .status-played {
            background-color: #e6f7ee;
            color: var(--accent-color);
        }
        
        .status-pending {
            background-color: #fff3cd;
            color: #856404;
        }
        
        .management-options {
            display: flex;
            gap: 10px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            overflow-y: auto;
            padding: 20px;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 8px;
            max-width: 600px;
            margin: 50px auto;
            position: relative;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
            animation: modalFadeIn 0.3s;
        }
        
        @keyframes modalFadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .modal-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--border-color);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-title {
            font-size: 18px;
            font-weight: 600;
            margin: 0;
        }
        
        .close-modal {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--gray);
            transition: color 0.3s;
        }
        
        .close-modal:hover {
            color: var(--danger-color);
        }
        
        .modal-body {
            padding: 20px;
        }
        
        .modal-footer {
            padding: 15px 20px;
            border-top: 1px solid var(--border-color);
            display: flex;
            justify-content: flex-end;
            gap: 10px;
        }
        
        .dashboard-stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .stat-card {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            display: flex;
            flex-direction: column;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        
        .stat-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }
        
        .stat-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: white;
        }
        
        .stat-icon.blue {
            background-color: var(--primary-color);
        }
        
        .stat-icon.green {
            background-color: var(--accent-color);
        }
        
        .stat-icon.yellow {
            background-color: var(--warning-color);
        }
        
        .stat-icon.red {
            background-color: var(--danger-color);
        }
        
        .stat-value {
            font-size: 28px;
            font-weight: 700;
            margin-top: 5px;
        }
        
        .stat-label {
            font-size: 14px;
            color: var(--gray);
            margin-bottom: 5px;
        }
        
        .loading {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(255,255,255,0.8);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 2000;
        }
        
        .spinner {
            width: 50px;
            height: 50px;
            border: 5px solid var(--secondary-color);
            border-top: 5px solid var(--primary-color);
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }
        
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        
        .form-section {
            border: 1px solid var(--border-color);
            border-radius: 8px;
            padding: 15px;
            margin-bottom: 20px;
        }
        
        .form-section-title {
            font-weight: 600;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .tooltip {
            position: relative;
            display: inline-block;
            cursor: pointer;
        }
        
        .tooltip .tooltiptext {
            visibility: hidden;
            width: 200px;
            background-color: #333;
            color: #fff;
            text-align: center;
            border-radius: 6px;
            padding: 5px;
            position: absolute;
            z-index: 1;
            bottom: 125%;
            left: 50%;
            margin-left: -100px;
            opacity: 0;
            transition: opacity 0.3s;
        }
        
        .tooltip:hover .tooltiptext {
            visibility: visible;
            opacity: 1;
        }
        
        .search-container {
            margin-bottom: 20px;
        }
        
        .search-box {
            width: 100%;
            padding: 10px 15px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            font-size: 14px;
            transition: all 0.3s;
        }
        
        .search-box:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(0,86,179,0.1);
            outline: none;
        }
        
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 15px;
            }
            
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }
            
            .match-card {
                flex-direction: column;
                gap: 15px;
            }
            
            .team {
                width: 100%;
                flex-direction: row;
                justify-content: space-between;
            }
            
            .form-row {
                flex-direction: column;
                gap: 15px;
            }
            
            .form-row .form-group {
                margin-bottom: 0;
            }
            
            .dashboard-stats {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="container header-content">
            <div class="logo">
                <i class="fas fa-futbol"></i>
                <h1>El Mundialito</h1>
            </div>
            <nav>
                <ul>
                    <li><a href="#" onclick="showTab('dashboard')"><i class="fas fa-chart-line"></i> Dashboard</a></li>
                    <li><a href="#" onclick="showTab('standings')"><i class="fas fa-trophy"></i> Clasificación</a></li>
                    <li><a href="#" onclick="showTab('matches')"><i class="fas fa-calendar-alt"></i> Partidos</a></li>
                    <li><a href="#" onclick="showTab('players')"><i class="fas fa-users"></i> Jugadores</a></li>
                    <li><a href="#" onclick="showTab('teams')"><i class="fas fa-shield-alt"></i> Equipos</a></li>
                </ul>
            </nav>
        </div>
    </header>
    
    <div class="container">
        <div id="login-section" style="display: none;">
            <div class="login-container card">
                <div class="card-header">
                    <h2 class="card-title"><i class="fas fa-sign-in-alt"></i> Iniciar Sesión</h2>
                </div>
                <div class="card-body">
                    <form id="login-form">
                        <div class="form-group">
                            <label for="username">Usuario:</label>
                            <input type="text" id="username" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="password">Contraseña:</label>
                            <input type="password" id="password" class="form-control" required>
                        </div>
                        <button type="submit" class="btn btn-success"><i class="fas fa-sign-in-alt"></i> Ingresar</button>
                    </form>
                </div>
            </div>
        </div>
        
                
            <div class="tab-container">
                <div class="tabs">
                    <div class="tab active" id="dashboard-tab" onclick="showTab('dashboard')">
                        <i class="fas fa-chart-line"></i> Dashboard
                    </div>
                    <div class="tab" id="standings-tab" onclick="showTab('standings')">
                        <i class="fas fa-trophy"></i> Clasificación
                    </div>
                    <div class="tab" id="matches-tab" onclick="showTab('matches')">
                        <i class="fas fa-calendar-alt"></i> Partidos
                    </div>
                    <div class="tab" id="players-tab" onclick="showTab('players')">
                        <i class="fas fa-users"></i> Jugadores
                    </div>
                    <div class="tab" id="teams-tab" onclick="showTab('teams')">
                        <i class="fas fa-shield-alt"></i> Equipos
                    </div>
                </div>
                
                <div id="dashboard" class="tab-content active">
                    <div class="dashboard-stats">
                        <div class="stat-card">
                            <div class="stat-header">
                                <div>
                                    <div class="stat-label">Equipos</div>
                                    <div class="stat-value" id="teams-count">12</div>
                                </div>
                                <div class="stat-icon blue">
                                    <i class="fas fa-shield-alt"></i>
                                </div>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-header">
                                <div>
                                    <div class="stat-label">Partidos</div>
                                    <div class="stat-value" id="matches-count">6</div>
                                </div>
                                <div class="stat-icon green">
                                    <i class="fas fa-futbol"></i>
                                </div>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-header">
                                <div>
                                    <div class="stat-label">Goles</div>
                                    <div class="stat-value" id="goals-count">15</div>
                                </div>
                                <div class="stat-icon yellow">
                                    <i class="fas fa-bullseye"></i>
                                </div>
                            </div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-header">
                                <div>
                                    <div class="stat-label">Jugadores</div>
                                    <div class="stat-value" id="players-count">14</div>
                                </div>
                                <div class="stat-icon red">
                                    <i class="fas fa-user"></i>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="card">
                        <div class="card-header">
                            <h2 class="card-title"><i class="fas fa-calendar-check"></i> Próximos Partidos</h2>
                        </div>
                        <div class="card-body">
                            <div id="upcoming-matches-container">
                                <!-- Datos dinámicos -->
                            </div>
                        </div>
                    </div>
                    
                    <div class="card">
                        <div class="card-header">
                            <h2 class="card-title"><i class="fas fa-sort-amount-down"></i> Top Goleadores</h2>
                        </div>
                        <div class="card-body">
                            <div class="table-responsive">
                                <table id="top-scorers-table">
                                    <thead>
                                        <tr>
                                            <th>Pos</th>
                                            <th>Jugador</th>
                                            <th>Equipo</th>
                                            <th>Goles</th>
                                        </tr>
                                    </thead>
                                    <tbody id="top-scorers-body">
                                        <!-- Datos dinámicos -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div id="standings" class="tab-content">
                    <div class="card">
                        <div class="card-header">
                            <h2 class="card-title"><i class="fas fa-trophy"></i> Tabla de Clasificación</h2>
                        </div>
                        <div class="card-body">
                            <div class="table-responsive">
                                <table id="standings-table">
                                    <thead>
                                        <tr>
                                            <th>Pos</th>
                                            <th>Equipo</th>
                                            <th>PJ</th>
                                            <th>PG</th>
                                            <th>PE</th>
                                            <th>PP</th>
                                            <th>GF</th>
                                            <th>GC</th>
                                            <th>DIF</th>
                                            <th>PTS</th>
                                        </tr>
                                    </thead>
                                    <tbody id="standings-body">
                                        <!-- Datos dinámicos -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div id="matches" class="tab-content">
                    <div class="card">
                        <div class="card-header">
                            <h2 class="card-title"><i class="fas fa-calendar-alt"></i> Partidos</h2>
                                                   </div>
                        <div class="card-body">
                            <div class="search-container">
                                <input type="text" id="match-search" class="search-box" placeholder="Buscar partidos..." onkeyup="searchMatches()">
                            </div>
                            <div id="matches-container">
                                <!-- Datos dinámicos -->
                            </div>
                        </div>
                    </div>
                </div>
                
                <div id="players" class="tab-content">
                    <div class="card">
                        <div class="card-header">
                            <h2 class="card-title"><i class="fas fa-users"></i> Jugadores</h2>
                                                   </div>
                        <div class="card-body">
                            <div class="search-container">
                                <div class="form-row">
                                    <div class="form-group">
                                        <input type="text" id="player-search" class="search-box" placeholder="Buscar jugadores..." onkeyup="searchPlayers()">
                                    </div>
                                    <div class="form-group">
                                        <select id="team-filter" class="form-control" onchange="filterPlayersByTeam()">
                                            <option value="all">Todos los equipos</option>
                                            <!-- Opciones de equipos dinámicas -->
                                        </select>
                                    </div>
                                </div>
                            </div>
                            <div class="table-responsive">
                                <table id="players-table">
                                    <thead>
                                        <tr>
                                            <th>Dorsal</th>
                                            <th>Nombre</th>
                                            <th>Equipo</th>
                                            <th>Goles</th>
                                            </tr>
                                    </thead>
                                    <tbody id="players-body">
                                        <!-- Datos dinámicos -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div id="teams" class="tab-content">
                    <div class="card">
                        <div class="card-header">
                            <h2 class="card-title"><i class="fas fa-shield-alt"></i> Equipos</h2>
                                                    </div>
                        <div class="card-body">
                            <div class="search-container">
                                <input type="text" id="team-search" class="search-box" placeholder="Buscar equipos..." onkeyup="searchTeams()">
                            </div>
                           <div class="table-responsive">
                                <table id="teams-table">
                                    <thead>
                                        <tr>
                                            <th>Nombre</th>
                                            <th>País</th>
                                            <th>Jugadores</th>
                                            
                                        </tr>
                                    </thead>
                                    <tbody id="teams-body">
                                        <!-- Datos dinámicos -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Modal para añadir equipo -->
    <div id="add-team-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title"><i class="fas fa-plus-circle"></i> Añadir Nuevo Equipo</h3>
                <button class="close-modal" onclick="closeModal('add-team-modal')">&times;</button>
            </div>
            <div class="modal-body">
                <form id="add-team-form">
                    <div class="form-group">
                        <label for="team-name">Nombre del Equipo:</label>
                        <input type="text" id="team-name" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="team-country">País:</label>
                        <input type="text" id="team-country" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label for="team-flag">Bandera (Emoji):</label>
                        <input type="text" id="team-flag" class="form-control" placeholder="🇪🇸">
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-danger" onclick="closeModal('add-team-modal')">Cancelar</button>
                <button class="btn btn-success" onclick="addTeam()">Guardar</button>
            </div>
        </div>
    </div>
    
    <!-- Modal para añadir jugador -->
    <div id="add-player-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title"><i class="fas fa-plus-circle"></i> Añadir Nuevo Jugador</h3>
                <button class="close-modal" onclick="closeModal('add-player-modal')">&times;</button>
            </div>
            <div class="modal-body">
                <form id="add-player-form">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="player-name">Nombre:</label>
                            <input type="text" id="player-name" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="player-number">Dorsal:</label>
                            <input type="number" id="player-number" class="form-control" min="1" max="99" required>
                        </div>
                    </div>
                    <div class="form-group">
                        <label for="player-team">Equipo:</label>
                        <select id="player-team" class="form-control" required>
                            <!-- Opciones de equipos dinámicas -->
                        </select>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-danger" onclick="closeModal('add-player-modal')">Cancelar</button>
                <button class="btn btn-success" onclick="addPlayer()">Guardar</button>
            </div>
        </div>
    </div>
    
    <!-- Modal para añadir partido -->
    <div id="add-match-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title"><i class="fas fa-plus-circle"></i> Añadir Nuevo Partido</h3>
                <button class="close-modal" onclick="closeModal('add-match-modal')">&times;</button>
            </div>
            <div class="modal-body">
                <form id="add-match-form">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="match-home-team">Equipo Local:</label>
                            <select id="match-home-team" class="form-control" required>
                                <!-- Opciones de equipos dinámicas -->
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="match-away-team">Equipo Visitante:</label>
                            <select id="match-away-team" class="form-control" required>
                                <!-- Opciones de equipos dinámicas -->
                            </select>
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label for="match-date">Fecha:</label>
                            <input type="date" id="match-date" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="match-time">Hora:</label>
                            <input type="time" id="match-time" class="form-control" required>
                        </div>
                    </div>
                    <div class="form-section">
                        <div class="form-section-title">
                            <i class="fas fa-futbol"></i> Resultado
                            <div class="tooltip">
                                <i class="fas fa-info-circle"></i>
                                <span class="tooltiptext">Dejar en blanco si el partido aún no se ha jugado</span>
                            </div>
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="match-home-goals">Goles Local:</label>
                                <input type="number" id="match-home-goals" class="form-control" min="0">
                            </div>
                            <div class="form-group">
                                <label for="match-away-goals">Goles Visitante:</label>
                                <input type="number" id="match-away-goals" class="form-control" min="0">
                            </div>
                        </div>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-danger" onclick="closeModal('add-match-modal')">Cancelar</button>
                <button class="btn btn-success" onclick="addMatch()">Guardar</button>
            </div>
        </div>
    </div>
    
    <!-- Modal para editar partido -->
    <div id="edit-match-modal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 class="modal-title"><i class="fas fa-edit"></i> Editar Partido</h3>
                <button class="close-modal" onclick="closeModal('edit-match-modal')">&times;</button>
            </div>
            <div class="modal-body">
                <form id="edit-match-form">
                    <input type="hidden" id="edit-match-id">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="edit-match-home-team">Equipo Local:</label>
                            <select id="edit-match-home-team" class="form-control" required>
                                <!-- Opciones de equipos dinámicas -->
                            </select>
                        </div>
                        <div class="form-group">
                            <label for="edit-match-away-team">Equipo Visitante:</label>
                            <select id="edit-match-away-team" class="form-control" required>
                                <!-- Opciones de equipos dinámicas -->
                            </select>
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <label for="edit-match-date">Fecha:</label>
                            <input type="date" id="edit-match-date" class="form-control" required>
                        </div>
                        <div class="form-group">
                            <label for="edit-match-time">Hora:</label>
                            <input type="time" id="edit-match-time" class="form-control" required>
                        </div>
                    </div>
                    <div class="form-section">
                        <div class="form-section-title">
                            <i class="fas fa-futbol"></i> Resultado
                        </div>
                        <div class="form-row">
                            <div class="form-group">
                                <label for="edit-match-home-goals">Goles Local:</label>
                                <input type="number" id="edit-match-home-goals" class="form-control" min="0">
                            </div>
                            <div class="form-group">
                                <label for="edit-match-away-goals">Goles Visitante:</label>
                                <input type="number" id="edit-match-away-goals" class="form-control" min="0">
                            </div>
                        </div>
                    </div>
                </form>
            </div>
            <div class="modal-footer">
                <button class="btn btn-danger" onclick="closeModal('edit-match-modal')">Cancelar</button>
                <button class="btn btn-success" onclick="updateMatch()">Guardar Cambios</button>
            </div>
        </div>
    </div>
    
    <!-- Indicador de carga -->
    <div class="loading" id="loading" style="display: none;">
        <div class="spinner"></div>
    </div>
    
    <!-- Scripts -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/toastr.min.js"></script>
    <script>
        // Datos de ejemplo
        let teams = [
            { id: 1, name: 'España', country: 'España', flag: '🇪🇸' },
            { id: 2, name: 'Brasil', country: 'Brasil', flag: '🇧🇷' },
            { id: 3, name: 'Argentina', country: 'Argentina', flag: '🇦🇷' },
            { id: 4, name: 'Alemania', country: 'Alemania', flag: '🇩🇪' },
            { id: 5, name: 'Francia', country: 'Francia', flag: '🇫🇷' },
            { id: 6, name: 'Portugal', country: 'Portugal', flag: '🇵🇹' },
            { id: 7, name: 'Inglaterra', country: 'Inglaterra', flag: '🏴󠁧󠁢󠁥󠁮󠁧󠁿' },
            { id: 8, name: 'Italia', country: 'Italia', flag: '🇮🇹' }
        ];
        
        let players = [
            { id: 1, name: 'Lionel Messi', number: 10, teamId: 3, goals: 5 },
            { id: 2, name: 'Cristiano Ronaldo', number: 7, teamId: 6, goals: 4 },
            { id: 3, name: 'Neymar Jr.', number: 10, teamId: 2, goals: 3 },
            { id: 4, name: 'Kylian Mbappé', number: 9, teamId: 5, goals: 3 },
            { id: 5, name: 'Álvaro Morata', number: 7, teamId: 1, goals: 2 },
            { id: 6, name: 'Harry Kane', number: 9, teamId: 7, goals: 2 },
            { id: 7, name: 'Pedri', number: 8, teamId: 1, goals: 1 },
            { id: 8, name: 'Vinicius Jr.', number: 20, teamId: 2, goals: 1 },
            { id: 9, name: 'Thomas Müller', number: 13, teamId: 4, goals: 1 },
            { id: 10, name: 'Ciro Immobile', number: 17, teamId: 8, goals: 1 },
            { id: 11, name: 'João Félix', number: 11, teamId: 6, goals: 1 },
            { id: 12, name: 'Lautaro Martínez', number: 22, teamId: 3, goals: 0 },
            { id: 13, name: 'Phil Foden', number: 10, teamId: 7, goals: 0 },
            { id: 14, name: 'Manuel Neuer', number: 1, teamId: 4, goals: 0 }
        ];
        
        let matches = [
            { id: 1, homeTeamId: 1, awayTeamId: 2, homeGoals: 2, awayGoals: 1, date: '2023-07-10', time: '20:00', played: true },
            { id: 2, homeTeamId: 3, awayTeamId: 4, homeGoals: 3, awayGoals: 2, date: '2023-07-11', time: '18:00', played: true },
            { id: 3, homeTeamId: 5, awayTeamId: 6, homeGoals: 1, awayGoals: 1, date: '2023-07-12', time: '19:30', played: true },
            { id: 4, homeTeamId: 7, awayTeamId: 8, homeGoals: 0, awayGoals: 0, date: '2023-07-13', time: '21:00', played: true },
            { id: 5, homeTeamId: 1, awayTeamId: 3, homeGoals: null, awayGoals: null, date: '2023-07-20', time: '20:00', played: false },
            { id: 6, homeTeamId: 5, awayTeamId: 7, homeGoals: null, awayGoals: null, date: '2023-07-21', time: '18:30', played: false }
        ];
        
        // Funciones de utilidad
        function getTeamById(id) {
            return teams.find(team => team.id === id);
        }
        
        function getPlayersByTeamId(teamId) {
            return players.filter(player => player.teamId === teamId);
        }
        
        // Inicialización
        document.addEventListener('DOMContentLoaded', function() {
            loadData();
            showTab('dashboard');
            
            // Configuración de toastr
            toastr.options = {
                "closeButton": true,
                "positionClass": "toast-top-right",
                "timeOut": "3000"
            };
        });
        
        function loadData() {
            showLoading();
            
            // Simulamos una carga de datos
            setTimeout(() => {
                updateDashboard();
                populateStandings();
                populateMatches();
                populateTeams();
                populatePlayers();
                populateTeamDropdowns();
                hideLoading();
            }, 500);
        }
        
        function showLoading() {
            document.getElementById('loading').style.display = 'flex';
        }
        
        function hideLoading() {
            document.getElementById('loading').style.display = 'none';
        }
        
        function showTab(tabId) {
            // Ocultar todos los contenidos
            const contents = document.querySelectorAll('.tab-content');
            contents.forEach(content => {
                content.classList.remove('active');
            });
            
            // Desactivar todos los tabs
            const tabs = document.querySelectorAll('.tab');
            tabs.forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Mostrar el contenido seleccionado
            document.getElementById(tabId).classList.add('active');
            
            // Activar el tab seleccionado
            document.getElementById(tabId + '-tab').classList.add('active');
        }
        
        function openModal(modalId) {
            document.getElementById(modalId).style.display = 'block';
        }
        
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }
        
        // Funciones del Dashboard
        function updateDashboard() {
            // Actualizar contadores
            document.getElementById('teams-count').textContent = teams.length;
            document.getElementById('matches-count').textContent = matches.length;
            
            let totalGoals = matches.reduce((total, match) => {
                if (match.played) {
                    return total + match.homeGoals + match.awayGoals;
                }
                return total;
            }, 0);
            document.getElementById('goals-count').textContent = totalGoals;
            document.getElementById('players-count').textContent = players.length;
            
            // Próximos partidos
            const upcomingMatches = matches.filter(match => !match.played)
                .sort((a, b) => new Date(a.date + 'T' + a.time) - new Date(b.date + 'T' + b.time))
                .slice(0, 3);
            
            let matchesHTML = '';
            upcomingMatches.forEach(match => {
                const homeTeam = getTeamById(match.homeTeamId);
                const awayTeam = getTeamById(match.awayTeamId);
                
                const matchDate = new Date(match.date + 'T' + match.time);
                const formattedDate = matchDate.toLocaleDateString('es-ES', { 
                    weekday: 'long', 
                    year: 'numeric', 
                    month: 'long', 
                    day: 'numeric' 
                });
                const formattedTime = matchDate.toLocaleTimeString('es-ES', { 
                    hour: '2-digit', 
                    minute: '2-digit' 
                });
                
                matchesHTML += `
                    <div class="match-card">
                        <div class="team">
                            <div class="team-flag">${homeTeam.flag}</div>
                            <div>${homeTeam.name}</div>
                        </div>
                        <div class="match-info">
                            <div class="status-badge status-pending">Pendiente</div>
                            <div class="match-date">${formattedDate} - ${formattedTime}</div>
                        </div>
                        <div class="team">
                            <div class="team-flag">${awayTeam.flag}</div>
                            <div>${awayTeam.name}</div>
                        </div>
                    </div>
                `;
            });
            
            if (upcomingMatches.length === 0) {
                matchesHTML = '<p>No hay próximos partidos programados.</p>';
            }
            
            document.getElementById('upcoming-matches-container').innerHTML = matchesHTML;
            
            // Top goleadores
            const topScorers = [...players]
                .sort((a, b) => b.goals - a.goals)
                .slice(0, 5);
            
            let scorersHTML = '';
            topScorers.forEach((player, index) => {
                const team = getTeamById(player.teamId);
                scorersHTML += `
                    <tr>
                        <td>${index + 1}</td>
                        <td>${player.name}</td>
                        <td><div class="flag-container"><span class="flag">${team.flag}</span> ${team.name}</div></td>
                        <td>${player.goals}</td>
                    </tr>
                `;
            });
            
            document.getElementById('top-scorers-body').innerHTML = scorersHTML;
        }
        
        // Funciones de la Clasificación
        function populateStandings() {
            // Calcular estadísticas
            const standings = teams.map(team => {
                const teamMatches = matches.filter(match => 
                    (match.homeTeamId === team.id || match.awayTeamId === team.id) && match.played
                );
                
                let played = teamMatches.length;
                let won = 0;
                let drawn = 0;
                let lost = 0;
                let goalsFor = 0;
                let goalsAgainst = 0;
                
                teamMatches.forEach(match => {
                    if (match.homeTeamId === team.id) {
                        goalsFor += match.homeGoals;
                        goalsAgainst += match.awayGoals;
                        
                        if (match.homeGoals > match.awayGoals) won++;
                        else if (match.homeGoals < match.awayGoals) lost++;
                        else drawn++;
                    } else {
                        goalsFor += match.awayGoals;
                        goalsAgainst += match.homeGoals;
                        
                        if (match.awayGoals > match.homeGoals) won++;
                        else if (match.awayGoals < match.homeGoals) lost++;
                        else drawn++;
                    }
                });
                
                const points = (won * 3) + drawn;
                const goalDifference = goalsFor - goalsAgainst;
                
                return {
                    ...team,
                    played,
                    won,
                    drawn,
                    lost,
                    goalsFor,
                    goalsAgainst,
                    goalDifference,
                    points
                };
            });
            
            // Ordenar por puntos y diferencia de goles
            standings.sort((a, b) => {
                if (a.points !== b.points) return b.points - a.points;
                if (a.goalDifference !== b.goalDifference) return b.goalDifference - a.goalDifference;
                return b.goalsFor - a.goalsFor;
            });
            
            // Generar HTML
            let standingsHTML = '';
            standings.forEach((team, index) => {
                standingsHTML += `
                    <tr>
                        <td>${index + 1}</td>
                        <td><div class="flag-container"><span class="flag">${team.flag}</span> ${team.name}</div></td>
                        <td>${team.played}</td>
                        <td>${team.won}</td>
                        <td>${team.drawn}</td>
                        <td>${team.lost}</td>
                        <td>${team.goalsFor}</td>
                        <td>${team.goalsAgainst}</td>
                        <td>${team.goalDifference}</td>
                        <td><strong>${team.points}</strong></td>
                    </tr>
                `;
            });
            
            document.getElementById('standings-body').innerHTML = standingsHTML;
        }
        
        // Funciones de Partidos
        function populateMatches() {
            // Ordenar partidos por fecha
            const sortedMatches = [...matches].sort((a, b) => {
                const dateA = new Date(a.date + 'T' + a.time);
                const dateB = new Date(b.date + 'T' + b.time);
                return dateA - dateB;
            });
            
            let matchesHTML = '';
            sortedMatches.forEach(match => {
                const homeTeam = getTeamById(match.homeTeamId);
                const awayTeam = getTeamById(match.awayTeamId);
                
                const matchDate = new Date(match.date + 'T' + match.time);
                const formattedDate = matchDate.toLocaleDateString('es-ES', { 
                    weekday: 'long', 
                    year: 'numeric', 
                    month: 'long', 
                    day: 'numeric' 
                });
                const formattedTime = matchDate.toLocaleTimeString('es-ES', { 
                    hour: '2-digit', 
                    minute: '2-digit' 
                });
                
                const scoreDisplay = match.played ?
                    `${match.homeGoals} - ${match.awayGoals}` :
                    'vs';
                
                const statusBadge = match.played ?
                    '<div class="status-badge status-played">Jugado</div>' :
                    '<div class="status-badge status-pending">Pendiente</div>';
                
                matchesHTML += `
                    <div class="match-card" data-id="${match.id}">
                        <div class="team">
                            <div class="team-flag">${homeTeam.flag}</div>
                            <div>${homeTeam.name}</div>
                        </div>
                        <div class="match-info">
                            ${statusBadge}
                            <div class="score">${scoreDisplay}</div>
                            <div class="match-date">${formattedDate} - ${formattedTime}</div>
                            <div class="actions">
                                                            </div>
                        </div>
                        <div class="team">
                            <div class="team-flag">${awayTeam.flag}</div>
                            <div>${awayTeam.name}</div>
                        </div>
                    </div>
                `;
            });
            
            if (matches.length === 0) {
                matchesHTML = '<p>No hay partidos programados.</p>';
            }
            
            document.getElementById('matches-container').innerHTML = matchesHTML;
        }
        
        function searchMatches() {
            const searchTerm = document.getElementById('match-search').value.toLowerCase();
            const matchCards = document.querySelectorAll('.match-card');
            
            matchCards.forEach(card => {
                const matchId = card.getAttribute('data-id');
                const match = matches.find(m => m.id === parseInt(matchId));
                const homeTeam = getTeamById(match.homeTeamId);
                const awayTeam = getTeamById(match.awayTeamId);
                
                const matchText = `${homeTeam.name} ${awayTeam.name}`.toLowerCase();
                
                if (matchText.includes(searchTerm)) {
                    card.style.display = 'flex';
                } else {
                    card.style.display = 'none';
                }
            });
        }
        
        function addMatch() {
            const homeTeamId = parseInt(document.getElementById('match-home-team').value);
            const awayTeamId = parseInt(document.getElementById('match-away-team').value);
            const date = document.getElementById('match-date').value;
            const time = document.getElementById('match-time').value;
            const homeGoals = document.getElementById('match-home-goals').value;
            const awayGoals = document.getElementById('match-away-goals').value;
            
            if (homeTeamId === awayTeamId) {
                toastr.error('Un equipo no puede jugar contra sí mismo');
                return;
            }
            
            const newMatch = {
                id: matches.length + 1,
                homeTeamId,
                awayTeamId,
                date,
                time,
                homeGoals: homeGoals === '' ? null : parseInt(homeGoals),
                awayGoals: awayGoals === '' ? null : parseInt(awayGoals),
                played: homeGoals !== '' && awayGoals !== ''
            };
            
            matches.push(newMatch);
            closeModal('add-match-modal');
            
            // Limpiar formulario
            document.getElementById('add-match-form').reset();
            
            loadData();
            toastr.success('Partido añadido correctamente');
        }
        
        function editMatch(matchId) {
            const match = matches.find(m => m.id === matchId);
            if (!match) return;
            
            document.getElementById('edit-match-id').value = match.id;
            document.getElementById('edit-match-home-team').value = match.homeTeamId;
            document.getElementById('edit-match-away-team').value = match.awayTeamId;
            document.getElementById('edit-match-date').value = match.date;
            document.getElementById('edit-match-time').value = match.time;
            
            if (match.played) {
                document.getElementById('edit-match-home-goals').value = match.homeGoals;
                document.getElementById('edit-match-away-goals').value = match.awayGoals;
            } else {
                document.getElementById('edit-match-home-goals').value = '';
                document.getElementById('edit-match-away-goals').value = '';
            }
            
            openModal('edit-match-modal');
        }
        
        function updateMatch() {
            const matchId = parseInt(document.getElementById('edit-match-id').value);
            const homeTeamId = parseInt(document.getElementById('edit-match-home-team').value);
            const awayTeamId = parseInt(document.getElementById('edit-match-away-team').value);
            const date = document.getElementById('edit-match-date').value;
            const time = document.getElementById('edit-match-time').value;
            const homeGoals = document.getElementById('edit-match-home-goals').value;
            const awayGoals = document.getElementById('edit-match-away-goals').value;
            
            if (homeTeamId === awayTeamId) {
                toastr.error('Un equipo no puede jugar contra sí mismo');
                return;
            }
            
            const matchIndex = matches.findIndex(m => m.id === matchId);
            if (matchIndex === -1) return;
            
            matches[matchIndex] = {
                ...matches[matchIndex],
                homeTeamId,
                awayTeamId,
                date,
                time,
                homeGoals: homeGoals === '' ? null : parseInt(homeGoals),
                awayGoals: awayGoals === '' ? null : parseInt(awayGoals),
                played: homeGoals !== '' && awayGoals !== ''
           };
            
            closeModal('edit-match-modal');
            loadData();
            toastr.success('Partido actualizado correctamente');
        }
        
        function deleteMatch(matchId) {
            if (confirm('¿Estás seguro de eliminar este partido?')) {
                const matchIndex = matches.findIndex(m => m.id === matchId);
                if (matchIndex === -1) return;
                
                matches.splice(matchIndex, 1);
                loadData();
                toastr.success('Partido eliminado correctamente');
            }
        }
        
        // Funciones de Jugadores
        function populatePlayers() {
            let playersHTML = '';
            players.forEach(player => {
                const team = getTeamById(player.teamId);
                playersHTML += `
                    <tr data-id="${player.id}" data-team="${player.teamId}">
                        <td>${player.number}</td>
                        <td>${player.name}</td>
                        <td><div class="flag-container"><span class="flag">${team.flag}</span> ${team.name}</div></td>
                        <td>${player.goals}</td>
                                       `;
            });
            
            document.getElementById('players-body').innerHTML = playersHTML;
        }
        
        function searchPlayers() {
            const searchTerm = document.getElementById('player-search').value.toLowerCase();
            const teamFilter = document.getElementById('team-filter').value;
            
            const playerRows = document.querySelectorAll('#players-body tr');
            
            playerRows.forEach(row => {
                const playerName = row.cells[1].textContent.toLowerCase();
                const teamId = parseInt(row.getAttribute('data-team'));
                
                const nameMatch = playerName.includes(searchTerm);
                const teamMatch = teamFilter === 'all' || teamId === parseInt(teamFilter);
                
                if (nameMatch && teamMatch) {
                    row.style.display = '';
                } else {
                    row.style.display = 'none';
                }
            });
        }
        
        function filterPlayersByTeam() {
            searchPlayers();
        }
        
        function addPlayer() {
            const name = document.getElementById('player-name').value;
            const number = parseInt(document.getElementById('player-number').value);
            const teamId = parseInt(document.getElementById('player-team').value);
            
            const newPlayer = {
                id: players.length + 1,
                name,
                number,
                teamId,
                goals: 0
            };
            
            players.push(newPlayer);
            closeModal('add-player-modal');
            
            // Limpiar formulario
            document.getElementById('add-player-form').reset();
            
            loadData();
            toastr.success('Jugador añadido correctamente');
        }
        
        function editPlayer(playerId) {
            // Implementar la edición de jugadores
            toastr.info('Funcionalidad en desarrollo');
        }
        
        function deletePlayer(playerId) {
            if (confirm('¿Estás seguro de eliminar este jugador?')) {
                const playerIndex = players.findIndex(p => p.id === playerId);
                if (playerIndex === -1) return;
                
                players.splice(playerIndex, 1);
                loadData();
                toastr.success('Jugador eliminado correctamente');
            }
        }
        
        // Funciones de Equipos
        function populateTeams() {
            let teamsHTML = '';
            teams.forEach(team => {
                const teamPlayers = getPlayersByTeamId(team.id);
                teamsHTML += `
                    <tr>
                        <td>${team.name}</td>
                        <td><div class="flag-container"><span class="flag">${team.flag}</span> ${team.country}</div></td>
                        <td>${teamPlayers.length}</td>
                        <td class="actions">
                                                   </td>
                    </tr>
                `;
            });
            
            document.getElementById('teams-body').innerHTML = teamsHTML;
        }
        
        function searchTeams() {
            const searchTerm = document.getElementById('team-search').value.toLowerCase();
            const teamRows = document.querySelectorAll('#teams-body tr');
            
            teamRows.forEach(row => {
                const teamName = row.cells[0].textContent.toLowerCase();
                const teamCountry = row.cells[1].textContent.toLowerCase();
                
                if (teamName.includes(searchTerm) || teamCountry.includes(searchTerm)) {
                    row.style.display = '';
                } else {
                    row.style.display = 'none';
                }
            });
        }
        
        function addTeam() {
            const name = document.getElementById('team-name').value;
            const country = document.getElementById('team-country').value;
            const flag = document.getElementById('team-flag').value || '🏳️';
            
            const newTeam = {
                id: teams.length + 1,
                name,
                country,
                flag
            };
            
            teams.push(newTeam);
            closeModal('add-team-modal');
            
            // Limpiar formulario
            document.getElementById('add-team-form').reset();
            
            loadData();
            toastr.success('Equipo añadido correctamente');
        }
        
        function editTeam(teamId) {
            // Implementar la edición de equipos
            toastr.info('Funcionalidad en desarrollo');
        }
        
        function deleteTeam(teamId) {
            // Verificar si hay jugadores o partidos asociados
            const hasPlayers = players.some(player => player.teamId === teamId);
            const hasMatches = matches.some(match => 
                match.homeTeamId === teamId || match.awayTeamId === teamId
            );
            
            if (hasPlayers || hasMatches) {
                toastr.error('No se puede eliminar el equipo porque tiene jugadores o partidos asociados');
                return;
            }
            
            if (confirm('¿Estás seguro de eliminar este equipo?')) {
                const teamIndex = teams.findIndex(t => t.id === teamId);
                if (teamIndex === -1) return;
                
                teams.splice(teamIndex, 1);
                loadData();
                toastr.success('Equipo eliminado correctamente');
            }
        }
        
        // Funciones de soporte
        function populateTeamDropdowns() {
            // Dropdown para filtro de jugadores
            let teamFilterOptions = '<option value="all">Todos los equipos</option>';
            teams.forEach(team => {
                teamFilterOptions += `<option value="${team.id}">${team.name}</option>`;
            });
            document.getElementById('team-filter').innerHTML = teamFilterOptions;
            
            // Dropdown para añadir jugador
            let playerTeamOptions = '';
            teams.forEach(team => {
                playerTeamOptions += `<option value="${team.id}">${team.name}</option>`;
            });
            document.getElementById('player-team').innerHTML = playerTeamOptions;
            
            // Dropdowns para añadir partido
            let matchTeamOptions = '';
            teams.forEach(team => {
                matchTeamOptions += `<option value="${team.id}">${team.flag} ${team.name}</option>`;
            });
            document.getElementById('match-home-team').innerHTML = matchTeamOptions;
            document.getElementById('match-away-team').innerHTML = matchTeamOptions;
            document.getElementById('edit-match-home-team').innerHTML = matchTeamOptions;
            document.getElementById('edit-match-away-team').innerHTML = matchTeamOptions;
        }
        
        function exportToExcel() {
            toastr.info('Exportando datos a Excel...');
            
            // Simulación de exportación
            setTimeout(() => {
                toastr.success('Datos exportados correctamente');
            }, 1000);
        }

function exportToExcel() {
    // Seleccionar la tabla de clasificaciones
    var table = document.getElementById('standings-table');
    
    // Convertir la tabla a una hoja de cálculo
    var ws = XLSX.utils.table_to_sheet(table);
    
    // Crear un nuevo libro de trabajo
    var wb = XLSX.utils.book_new();
    
    // Añadir la hoja al libro
    XLSX.utils.book_append_sheet(wb, ws, "Clasificación");
    
    // Generar el archivo y descargarlo
    XLSX.writeFile(wb, 'Tabla_de_Clasificacion.xlsx');
}

// Variable para controlar si estamos en modo edición
let editModeActive = false;

function toggleEditMode() {
    editModeActive = !editModeActive;
    const btn = document.querySelector('[onclick="toggleEditMode()"]');
    const filas = document.querySelectorAll('#standings-body tr');
    
    if (editModeActive) {
        // Activar modo edición
        btn.innerHTML = '<i class="fas fa-save"></i> Guardar Cambios';
        btn.classList.add('btn-success');
        
        // Hacer las celdas editables
        filas.forEach(fila => {
            const celdas = fila.querySelectorAll('td');
            
            // Empezamos desde 2 para no hacer editables la posición
            // (asumiendo que la primera columna es Pos)
            for (let i = 2; i < celdas.length; i++) {
                const valor = celdas[i].textContent;
                celdas[i].setAttribute('contenteditable', 'true');
                celdas[i].classList.add('celda-editable');
            }
        });
    } else {
        // Desactivar modo edición
        btn.innerHTML = '<i class="fas fa-edit"></i> Editar Clasificaciones';
        btn.classList.remove('btn-success');
        
        // Hacer las celdas no editables y guardar cambios
        filas.forEach(fila => {
            const celdas = fila.querySelectorAll('td');
            
            for (let i = 2; i < celdas.length; i++) {
                celdas[i].removeAttribute('contenteditable');
                celdas[i].classList.remove('celda-editable');
            }
        });
        
        // Recalcular posiciones basadas en puntos
        recalcularClasificacion();
        
        // Aquí podrías añadir código para guardar los cambios en tu base de datos
        // saveToDatabase();
    }
}

function recalcularClasificacion() {
    // Obtener todas las filas
    const filas = Array.from(document.querySelectorAll('#standings-body tr'));
    
    // Extraer datos y ordenar por puntos (última columna)
    filas.sort((a, b) => {
        const puntosA = parseInt(a.querySelectorAll('td')[9].textContent);
        const puntosB = parseInt(b.querySelectorAll('td')[9].textContent);
        return puntosB - puntosA; // Orden descendente por puntos
    });
    
    // Actualizar posiciones y reordenar la tabla
    const tbody = document.getElementById('standings-body');
    tbody.innerHTML = '';
    
    filas.forEach((fila, index) => {
        fila.querySelectorAll('td')[0].textContent = index + 1;
        tbody.appendChild(fila);
    });
}

    </script>
<script src="https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js"></script>
</body>
</html>
