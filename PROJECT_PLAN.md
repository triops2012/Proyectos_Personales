# Proyecto: Gestión de Proyectos Unipersonales

## 1. Introducción

Este documento describe el plan inicial para el desarrollo de un sistema de "Gestión de Proyectos Unipersonales". El objetivo principal es proporcionar una herramienta robusta e intuitiva para que los usuarios individuales puedan organizar eficazmente sus proyectos, tareas, hábitos y rutinas, mejorando su productividad y ofreciendo insights sobre su rendimiento. El sistema se centrará en módulos clave como la gestión de proyectos y tareas, un dashboard de productividad, visualizaciones interactivas, automatización inteligente y análisis de rendimiento.

## 2. Arquitectura General

El sistema seguirá una arquitectura cliente-servidor, con un frontend interactivo (probablemente SPA) y un backend RESTful. Se utilizará una base de datos relacional para el almacenamiento de datos. Los módulos se estructurarán lógicamente para garantizar la escalabilidad y mantenibilidad.

-   **Frontend**: Interfaz de usuario para la interacción del usuario.
-   **Backend**: Lógica de negocio, servicios de datos, APIs y automatización.
-   **Base de Datos**: Almacenamiento persistente de toda la información del usuario y del proyecto.
-   **Servicios Compartidos**: Utilidades y helpers que pueden ser usados tanto por el frontend como el backend.

## 3. Características Detalladas y Archivos Asociados

A continuación, se detallan las características seleccionadas para la fase inicial del proyecto, junto con los archivos clave para su implementación.

### 3.1. Project Core Management (Gestión Central de Proyectos)

**Descripción**: Este módulo es la base para la creación, definición y gestión de proyectos. Permite a los usuarios establecer nombres, descripciones, tipos (personal, trabajo, familiar), duraciones, fechas de inicio/fin, y definir hitos clave.

**Archivos:**
*   `src/backend/models/project.js`
*   `src/backend/services/projectService.js`
*   `src/backend/controllers/projectController.js`
*   `src/backend/routes/projectRoutes.js`
*   `src/database/migrations/001_create_projects_table.js`
*   `src/frontend/store/modules/projects.js`

### 3.2. Task and List Management (Gestión de Tareas y Listas)

**Descripción**: Permite la creación detallada de tareas con atributos como título, descripción, tiempo estimado y prioridad. Soporta la subdivisión de tareas en sub-tareas y diferentes tipos de listas (secuenciales, concurrentes, de compra), además de tareas recurrentes.

**Archivos:**
*   `src/backend/models/task.js`
*   `src/backend/models/subtask.js`
*   `src/backend/models/list.js`
*   `src/backend/services/taskService.js`
*   `src/backend/controllers/taskController.js`
*   `src/backend/routes/taskRoutes.js`
*   `src/database/migrations/002_create_tasks_table.js`
*   `src/database/migrations/003_create_subtasks_table.js`
*   `src/database/migrations/004_create_lists_table.js`
*   `src/frontend/store/modules/tasks.js`

### 3.3. Intelligent Prioritization & Alerts (Priorización Inteligente y Alertas)

**Descripción**: Este módulo implementa la priorización automática de tareas basándose en su urgencia y criticidad, y gestiona la entrega de alertas y recordatorios inteligentes y personalizados para mantener al usuario informado.

**Archivos:**
*   `src/backend/services/automationService.js`
*   `src/backend/utils/priorityAlgorithm.js`
*   `src/backend/utils/notificationService.js`
*   `src/backend/cron/taskScheduler.js`
*   `src/database/migrations/006_create_alerts_table.js`
*   `src/backend/models/alert.js`
*   `src/frontend/store/modules/alerts.js`

### 3.4. Central Productivity Dashboard (Dashboard Central de Productividad)

**Descripción**: El epicentro del flujo de trabajo del usuario. Ofrece un calendario inteligente que muestra las tareas activas, una sección "Mi Día" para enfocar las actividades diarias, y funcionalidad para gestionar y seguir hábitos y rutinas.

**Archivos:**
*   `src/frontend/views/DashboardView.vue`
*   `src/frontend/components/dashboard/CalendarWidget.vue`
*   `src/frontend/components/dashboard/MyDaySection.vue`
*   `src/frontend/components/dashboard/HabitTracker.vue`
*   `src/frontend/store/modules/dashboard.js`
*   `src/backend/services/habitService.js`
*   `src/backend/controllers/habitController.js`
*   `src/backend/routes/habitRoutes.js`
*   `src/database/migrations/005_create_habits_table.js`
*   `src/shared/utils/dateUtils.js`

### 3.5. Visual Project Tracking (Seguimiento Visual de Proyectos)

**Descripción**: Proporciona herramientas visuales interactivas para el seguimiento del progreso del proyecto, incluyendo tableros Kanban para la gestión de tareas por estado y diagramas de Gantt para la visualización de la línea de tiempo y dependencias.

**Archivos:**
*   `src/frontend/views/ProjectDetailView.vue`
*   `src/frontend/components/project/KanbanBoard.vue`
*   `src/frontend/components/project/GanttChart.vue`
*   `src/frontend/components/project/MilestoneTracker.vue`
*   `src/frontend/store/modules/projectVisuals.js`
*   `src/shared/utils/ganttUtils.js`
*   `src/frontend/assets/styles/kanban.css`

### 3.6. Performance Reporting & Analytics (Reportes y Análisis de Rendimiento)

**Descripción**: Este módulo genera informes y estadísticas sobre la productividad del usuario, el tiempo dedicado a proyectos y tareas, y proporciona acceso a un historial de proyectos completados para obtener información valiosa sobre la gestión del tiempo y el rendimiento.

**Archivos:**
*   `src/frontend/views/AnalyticsView.vue`
*   `src/frontend/components/analytics/ProductivityChart.vue`
*   `src/frontend/components/analytics/TaskStats.vue`
*   `src/frontend/components/analytics/ProjectHistory.vue`
*   `src/backend/services/reportService.js`
*   `src/backend/controllers/reportController.js`
*   `src/backend/routes/reportRoutes.js`
*   `src/shared/utils/chartDataFormatter.js`

## 4. Tecnologías Propuestas (Ejemplo)

-   **Backend**: Node.js (Express.js o NestJS)
-   **Frontend**: Vue.js (o React/Angular)
-   **Base de Datos**: PostgreSQL (o MySQL)
-   **ORMS**: Sequelize (para Node.js)
-   **Estilos**: CSS/SCSS con un framework como TailwindCSS o Bootstrap
-   **Despliegue**: Docker, Nginx

## 5. Próximos Pasos

1.  Configuración del entorno de desarrollo.
2.  Diseño detallado de la base de datos (esquemas y relaciones).
3.  Implementación de la autenticación de usuarios (no incluida en las features actuales).
4.  Desarrollo iterativo de cada característica, siguiendo las dependencias establecidas.
5.  Pruebas unitarias, de integración y end-to-end.
6.  Despliegue y monitoreo continuo.