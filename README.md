# Control-Reparaciones-Gama
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Control de Reparaciones</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 5px;
            font-size: 14px;
        }

        .container {
            max-width: 100%;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 15px;
            text-align: center;
        }

        .logo {
            width: 50px;
            height: 50px;
            margin: 0 auto 8px;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
        }

        .header h1 {
            font-size: 20px;
            margin-bottom: 3px;
        }

        .header p {
            opacity: 0.9;
            font-size: 12px;
        }

        .main-content {
            padding: 15px;
        }

        .tabs {
            display: flex;
            background: #f8f9fa;
            border-radius: 10px;
            margin-bottom: 15px;
            overflow: hidden;
        }

        .tab {
            flex: 1;
            padding: 12px 8px;
            text-align: center;
            background: transparent;
            border: none;
            cursor: pointer;
            font-size: 12px;
            font-weight: 500;
            transition: all 0.3s;
            color: #666;
        }

        .tab.active {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .form-section {
            background: #f8f9fa;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 15px;
            border: 2px solid #e9ecef;
        }

        .form-section h2 {
            color: #2c3e50;
            margin-bottom: 12px;
            font-size: 16px;
        }

        .form-group {
            margin-bottom: 12px;
        }

        .form-group label {
            display: block;
            margin-bottom: 4px;
            color: #555;
            font-weight: 500;
            font-size: 12px;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 10px;
            border: 2px solid #ddd;
            border-radius: 8px;
            font-size: 14px;
            transition: border-color 0.3s;
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            outline: none;
            border-color: #667eea;
        }

        .form-group textarea {
            height: 70px;
            resize: vertical;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
        }

        .btn {
            padding: 10px 15px;
            border: none;
            border-radius: 8px;
            font-size: 12px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
            margin: 3px;
            text-align: center;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
        }

        .btn-primary {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
        }

        .btn-success {
            background: linear-gradient(135deg, #56ab2f, #a8e6cf);
            color: white;
        }

        .btn-warning {
            background: linear-gradient(135deg, #f093fb, #f5576c);
            color: white;
        }

        .btn-danger {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
        }

        .btn-secondary {
            background: linear-gradient(135deg, #74b9ff, #0984e3);
            color: white;
        }

        .btn-info {
            background: linear-gradient(135deg, #00cec9, #55a3ff);
            color: white;
        }

        .btn:active {
            transform: scale(0.98);
        }

        .button-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 8px;
            margin-bottom: 10px;
        }

        .search-box {
            position: relative;
            margin-bottom: 15px;
        }

        .search-box input {
            width: 100%;
            padding: 12px 15px 12px 40px;
            border: 2px solid #ddd;
            border-radius: 25px;
            font-size: 14px;
            background: white;
        }

        .search-icon {
            position: absolute;
            left: 12px;
            top: 50%;
            transform: translateY(-50%);
            color: #666;
            font-size: 16px;
        }

        .client-item, .repair-item {
            background: white;
            border: 2px solid #e9ecef;
            border-radius: 10px;
            padding: 12px;
            margin-bottom: 10px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.05);
        }

        .client-header, .repair-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
        }

        .client-name, .repair-title {
            font-weight: bold;
            color: #2c3e50;
            font-size: 14px;
        }

        .repair-cost {
            color: #27ae60;
            font-weight: bold;
            font-size: 16px;
        }

        .client-details, .repair-details {
            color: #666;
            line-height: 1.4;
            font-size: 12px;
        }

        .client-actions, .repair-actions {
            margin-top: 8px;
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 5px;
        }

        .empty-state {
            text-align: center;
            padding: 30px 15px;
            color: #666;
        }

        .empty-state svg {
            width: 60px;
            height: 60px;
            margin-bottom: 15px;
            opacity: 0.5;
        }

        .status-badge {
            display: inline-block;
            padding: 3px 8px;
            border-radius: 12px;
            font-size: 10px;
            font-weight: 500;
            margin-left: 5px;
        }

        .status-pendiente {
            background: #fff3cd;
            color: #856404;
        }

        .status-en-proceso {
            background: #d4edda;
            color: #155724;
        }

        .status-completado {
            background: #d1ecf1;
            color: #0c5460;
        }

        .image-preview {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
            gap: 8px;
            margin-top: 8px;
        }

        .image-item {
            position: relative;
            border-radius: 8px;
            overflow: hidden;
            aspect-ratio: 1;
        }

        .image-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .image-delete {
            position: absolute;
            top: 2px;
            right: 2px;
            background: rgba(255, 0, 0, 0.8);
            color: white;
            border: none;
            border-radius: 50%;
            width: 20px;
            height: 20px;
            font-size: 12px;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .hidden {
            display: none !important;
        }

        .delivery-info {
            background: #e8f4fd;
            padding: 8px;
            border-radius: 6px;
            margin-top: 5px;
            border-left: 4px solid #007bff;
        }

        .overdue {
            background: #ffebee;
            border-left-color: #f44336;
        }

        .coming-soon {
            background: #fff3e0;
            border-left-color: #ff9800;
        }

        @media (max-width: 480px) {
            .form-row {
                grid-template-columns: 1fr;
            }
            
            .button-group {
                grid-template-columns: 1fr;
            }
            
            .client-actions, .repair-actions {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="logo">🔧</div>
            <h1>Control de Reparaciones</h1>
            <p>Gestiona tus servicios de reparación</p>
        </div>

        <div class="main-content">
            <!-- Pestañas -->
            <div class="tabs">
                <button class="tab active" onclick="showTab('repairs')">🔧 Reparaciones</button>
                <button class="tab" onclick="showTab('clients')">👥 Clientes</button>
                <button class="tab" onclick="showTab('backup')">💾 Respaldo</button>
            </div>

            <!-- Pestaña Reparaciones -->
            <div id="repairs-tab" class="tab-content active">
                <div class="form-section">
                    <h2 id="form-title">➕ Agregar Reparación</h2>
                    <form id="repair-form">
                        <div class="form-row">
                            <div class="form-group">
                                <label for="cliente">👤 Cliente</label>
                                <input type="text" id="cliente" name="cliente" required list="clients-list">
                                <datalist id="clients-list"></datalist>
                            </div>
                            <div class="form-group">
                                <label for="contacto">📱 Contacto</label>
                                <input type="text" id="contacto" name="contacto" placeholder="Teléfono o email">
                            </div>
                        </div>
                        
                        <div class="form-row">
                            <div class="form-group">
                                <label for="modelo">📱 Modelo/Equipo</label>
                                <input type="text" id="modelo" name="modelo" required>
                            </div>
                            <div class="form-group">
                                <label for="costo">💰 Costo ($)</label>
                                <input type="number" id="costo" name="costo" step="0.01" min="0">
                            </div>
                        </div>

                        <div class="form-row">
                            <div class="form-group">
                                <label for="reparacion">🔧 Tipo de Reparación</label>
                                <input type="text" id="reparacion" name="reparacion" required>
                            </div>
                            <div class="form-group">
                                <label for="estado">📊 Estado</label>
                                <select id="estado" name="estado">
                                    <option value="pendiente">⏳ Pendiente</option>
                                    <option value="en-proceso">🔄 En Proceso</option>
                                    <option value="completado">✅ Completado</option>
                                </select>
                            </div>
                        </div>

                        <div class="form-group">
                            <label for="fecha-entrega">📅 Fecha de Entrega</label>
                            <input type="date" id="fecha-entrega" name="fecha-entrega">
                        </div>

                        <div class="form-group">
                            <label for="observaciones">📝 Observaciones</label>
                            <textarea id="observaciones" name="observaciones" placeholder="Detalles adicionales, problemas encontrados, etc."></textarea>
                        </div>

                        <div class="form-group">
                            <label>📸 Imágenes</label>
                            <input type="file" id="image-input" accept="image/*" multiple style="display: none;" onchange="handleImageUpload(event)">
                            <button type="button" class="btn btn-info" onclick="document.getElementById('image-input').click()">
                                📷 Agregar Fotos
                            </button>
                            <div id="image-preview" class="image-preview"></div>
                        </div>

                        <div class="button-group">
                            <button type="submit" class="btn btn-primary">
                                <span id="btn-text">💾 Guardar</span>
                            </button>
                            <button type="button" class="btn btn-secondary" id="btn-cancel" onclick="cancelEdit()" style="display: none;">
                                ❌ Cancelar
                            </button>
                        </div>
                    </form>
                </div>

                <!-- Buscador de Reparaciones -->
                <div class="search-box">
                    <span class="search-icon">🔍</span>
                    <input type="text" id="repair-search" placeholder="Buscar reparación por cliente..." onkeyup="searchRepairs()">
                </div>

                <!-- Lista de Reparaciones -->
                <div id="repairs-container">
                    <div class="empty-state">
                        <svg viewBox="0 0 24 24" fill="currentColor">
                            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                        </svg>
                        <p>No hay reparaciones registradas.<br>Agrega tu primera reparación.</p>
                    </div>
                </div>
            </div>

            <!-- Pestaña Clientes -->
            <div id="clients-tab" class="tab-content">
                <!-- Buscador de Clientes -->
                <div class="search-box">
                    <span class="search-icon">🔍</span>
                    <input type="text" id="client-search" placeholder="Buscar cliente..." onkeyup="searchClients()">
                </div>

                <!-- Lista de Clientes -->
                <div id="clients-container">
                    <div class="empty-state">
                        <svg viewBox="0 0 24 24" fill="currentColor">
                            <path d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/>
                        </svg>
                        <p>No hay clientes registrados.<br>Los clientes aparecerán automáticamente al crear reparaciones.</p>
                    </div>
                </div>
            </div>

            <!-- Pestaña Respaldo -->
            <div id="backup-tab" class="tab-content">
                <div class="form-section">
                    <h2>💾 Gestión de Datos</h2>
                    <div class="button-group">
                        <button class="btn btn-success" onclick="exportData()">
                            📥 Descargar Respaldo
                        </button>
                        <button class="btn btn-warning" onclick="importData()">
                            📤 Restaurar Respaldo
                        </button>
                    </div>
                    <div class="button-group">
                        <button class="btn btn-danger" onclick="clearAllData()">
                            🗑️ Borrar Todo
                        </button>
                    </div>
                    <input type="file" id="file-input" accept=".json" style="display: none;" onchange="handleFileImport(event)">
                </div>
            </div>
        </div>
    </div>

    <script>
        let repairs = [];
        let clients = [];
        let editingIndex = -1;
        let currentImages = [];

        // Cargar datos al iniciar
        window.onload = function() {
            loadData();
            displayRepairs();
            displayClients();
            updateClientsDatalist();
        };

        // Cambiar pestañas
        function showTab(tabName) {
            // Ocultar todos los contenidos
            document.querySelectorAll('.tab-content').forEach(content => {
                content.classList.remove('active');
            });
            
            // Ocultar todas las pestañas activas
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
            });
            
            // Mostrar contenido y pestaña seleccionada
            document.getElementById(tabName + '-tab').classList.add('active');
            event.target.classList.add('active');
        }

        // Manejar envío del formulario
        document.getElementById('repair-form').addEventListener('submit', function(e) {
            e.preventDefault();
            saveRepair();
        });

        function saveRepair() {
            const formData = new FormData(document.getElementById('repair-form'));
            const clientName = formData.get('cliente').trim();
            const clientContact = formData.get('contacto').trim();
            
            // Actualizar o agregar cliente
            updateClientsList(clientName, clientContact);
            
            const repair = {
                id: editingIndex >= 0 ? repairs[editingIndex].id : Date.now(),
                cliente: clientName,
                contacto: clientContact,
                modelo: formData.get('modelo'),
                reparacion: formData.get('reparacion'),
                costo: parseFloat(formData.get('costo')) || 0,
                estado: formData.get('estado'),
                fechaEntrega: formData.get('fecha-entrega'),
                observaciones: formData.get('observaciones'),
                fecha: editingIndex >= 0 ? repairs[editingIndex].fecha : new Date().toLocaleDateString(),
                imagenes: [...currentImages]
            };

            if (editingIndex >= 0) {
                repairs[editingIndex] = repair;
                editingIndex = -1;
                document.getElementById('form-title').textContent = '➕ Agregar Reparación';
                document.getElementById('btn-text').textContent = '💾 Guardar';
                document.getElementById('btn-cancel').style.display = 'none';
            } else {
                repairs.push(repair);
            }

            saveData();
            displayRepairs();
            displayClients();
            updateClientsDatalist();
            document.getElementById('repair-form').reset();
            currentImages = [];
            document.getElementById('image-preview').innerHTML = '';
        }

        function updateClientsList(name, contact) {
            if (!name) return;
            
            const existingClient = clients.find(c => c.name.toLowerCase() === name.toLowerCase());
            if (existingClient) {
                if (contact && contact !== existingClient.contact) {
                    existingClient.contact = contact;
                }
                existingClient.lastRepair = new Date().toLocaleDateString();
                existingClient.repairCount = (existingClient.repairCount || 0) + 1;
            } else {
                clients.push({
                    name: name,
                    contact: contact || '',
                    firstSeen: new Date().toLocaleDateString(),
                    lastRepair: new Date().toLocaleDateString(),
                    repairCount: 1
                });
            }
            
            // Ordenar clientes alfabéticamente
            clients.sort((a, b) => a.name.localeCompare(b.name));
        }

        function updateClientsDatalist() {
            const datalist = document.getElementById('clients-list');
            datalist.innerHTML = clients.map(client => 
                `<option value="${client.name}">${client.name} - ${client.contact}</option>`
            ).join('');
        }

        function displayRepairs() {
            const container = document.getElementById('repairs-container');
            const searchTerm = document.getElementById('repair-search').value.toLowerCase();
            
            let filteredRepairs = repairs;
            if (searchTerm) {
                filteredRepairs = repairs.filter(repair => 
                    repair.cliente.toLowerCase().includes(searchTerm) ||
                    repair.modelo.toLowerCase().includes(searchTerm) ||
                    repair.reparacion.toLowerCase().includes(searchTerm)
                );
            }
            
            if (filteredRepairs.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <svg viewBox="0 0 24 24" fill="currentColor">
                            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                        </svg>
                        <p>${searchTerm ? 'No se encontraron reparaciones' : 'No hay reparaciones registradas'}<br>${searchTerm ? 'Intenta con otro término de búsqueda' : 'Agrega tu primera reparación'}</p>
                    </div>
                `;
                return;
            }

            container.innerHTML = filteredRepairs.map((repair, originalIndex) => {
                const actualIndex = repairs.findIndex(r => r.id === repair.id);
                const deliveryStatus = getDeliveryStatus(repair.fechaEntrega);
                
                return `
                    <div class="repair-item">
                        <div class="repair-header">
                            <div class="repair-title">👤 ${repair.cliente} - 📱 ${repair.modelo}</div>
                            <div class="repair-cost">$${repair.costo.toFixed(2)}</div>
                        </div>
                        <div class="repair-details">
                            <p><strong>📱 Contacto:</strong> ${repair.contacto}</p>
                            <p><strong>🔧 Reparación:</strong> ${repair.reparacion}</p>
                            <p><strong>📊 Estado:</strong> <span class="status-badge status-${repair.estado}">${getStatusText(repair.estado)}</span></p>
                            <p><strong>📅 Fecha:</strong> ${repair.fecha}</p>
                            ${repair.fechaEntrega ? `<div class="delivery-info ${deliveryStatus.class}"><strong>📅 Entrega:</strong> ${repair.fechaEntrega} ${deliveryStatus.text}</div>` : ''}
                            ${repair.observaciones ? `<p><strong>📝 Observaciones:</strong> ${repair.observaciones}</p>` : ''}
                            ${repair.imagenes && repair.imagenes.length > 0 ? `
                                <div class="image-preview">
                                    ${repair.imagenes.map(img => `
                                        <div class="image-item">
                                            <img src="${img}" alt="Imagen" onclick="viewImage('${img}')">
                                        </div>
                                    `).join('')}
                                </div>
                            ` : ''}
                        </div>
                        <div class="repair-actions">
                            <button class="btn btn-primary" onclick="editRepair(${actualIndex})">✏️ Editar</button>
                            <button class="btn btn-danger" onclick="deleteRepair(${actualIndex})">🗑️ Eliminar</button>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function displayClients() {
            const container = document.getElementById('clients-container');
            const searchTerm = document.getElementById('client-search').value.toLowerCase();
            
            let filteredClients = clients;
            if (searchTerm) {
                filteredClients = clients.filter(client => 
                    client.name.toLowerCase().includes(searchTerm) ||
                    client.contact.toLowerCase().includes(searchTerm)
                );
            }
            
            if (filteredClients.length === 0) {
                container.innerHTML = `
                    <div class="empty-state">
                        <svg viewBox="0 0 24 24" fill="currentColor">
                            <path d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z"/>
                        </svg>
                        <p>${searchTerm ? 'No se encontraron clientes' : 'No hay clientes registrados'}<br>${searchTerm ? 'Intenta con otro nombre' : 'Los clientes aparecerán automáticamente'}</p>
                    </div>
                `;
                return;
            }

            container.innerHTML = filteredClients.map(client => `
                <div class="client-item">
                    <div class="client-header">
                        <div class="client-name">👤 ${client.name}</div>
                        <div style="font-size: 12px; color: #666;">${client.repairCount} reparaciones</div>
                    </div>
                    <div class="client-details">
                        <p><strong>📱 Contacto:</strong> ${client.contact || 'No registrado'}</p>
                        <p><strong>📅 Primera visita:</strong> ${client.firstSeen}</p>
                        <p><strong>📅 Última reparación:</strong> ${client.lastRepair}</p>
                    </div>
                    <div class="client-actions">
                        <button class="btn btn-primary" onclick="viewClientRepairs('${client.name}')">🔧 Ver Reparaciones</button>
                        <button class="btn btn-secondary" onclick="newRepairForClient('${client.name}', '${client.contact}')">➕ Nueva Reparación</button>
                    </div>
                </div>
            `).join('');
        }

        function getStatusText(status) {
            const statusMap = {
                'pendiente': '⏳ Pendiente',
                'en-proceso': '🔄 En Proceso',
                'completado': '✅ Completado'
            };
            return statusMap[status] || status;
        }

        function getDeliveryStatus(fechaEntrega) {
            if (!fechaEntrega) return { class: '', text: '' };
            
            const today = new Date();
            const deliveryDate = new Date(fechaEntrega);
            const diffTime = deliveryDate - today;
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
            
            if (diffDays < 0) {
                return { class: 'overdue', text: `(${Math.abs(diffDays)} días atrasado)` };
            } else if (diffDays <= 3) {
                return { class: 'coming-soon', text: `(${diffDays} días restantes)` };
            } else {
                return { class: '', text: `(${diffDays} días restantes)` };
            }
        }

        function handleImageUpload(event) {
            const files = Array.from(event.target.files);
            files.forEach(file => {
                if (file.type.startsWith('image/')) {
                    const reader = new FileReader();
                    reader.onload = function(e) {
                        currentImages.push(e.target.result);
                        displayImagePreview();
                    };
                    reader.readAsDataURL(file);
                }
            });
        }

        function displayImagePreview() {
            const container = document.getElementById('image-preview');
            container.innerHTML = currentImages.map((img, index) => `
                <div class="image-item">
                    <img src="${img}" alt="Vista previa">
                    <button class="image-delete" onclick="removeImage(${index})" type="button">×</button>
                </div>
            `).join('');
        }

        function removeImage(index) {
            currentImages.splice(index, 1);
            displayImagePreview();
        }

        function viewImage(imageSrc) {
            const modal = document.createElement('div');
            modal.style.cssText = `
                position: fixed; top: 0; left: 0; width: 100%; height: 100%; 
                background: rgba(0,0,0,0.9); z-index: 1000; display: flex; 
                align-items: center; justify-content: center; padding: 20px;
            `;
            modal.innerHTML = `
                <img src="${imageSrc}" style="max-width: 100%; max-height: 100%; object-fit: contain;">
                <button onclick="this.parentElement.remove()"
