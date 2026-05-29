# 🧙‍♂️ Codex Arcanum | Plataforma EdTech B2B

![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)
![Firebase](https://img.shields.io/badge/firebase-%23039BE5.svg?style=for-the-badge&logo=firebase)

**[🚀 Ver Demo en Vivo (Netlify)](https://codexarcanum.netlify.app/)**

Codex Arcanum es una plataforma SaaS (Software as a Service) orientada al sector educativo (B2B). Su objetivo es gamificar la enseñanza de Lógica Computacional y JavaScript para estudiantes de preparatoria mediante mecánicas de RPG, mientras provee un panel administrativo automatizado para los profesores.

## 🎯 El Problema y la Solución
* **El Problema:** La enseñanza tradicional de programación suele tener altas tasas de deserción por falta de interactividad. Además, la evaluación de código y lógica supone una carga administrativa masiva para el docente.
* **La Solución:** Un entorno gamificado donde el estudiante aprende superando "calabozos lógicos", conectado a un Dashboard en la nube que califica, grafica y exporta el rendimiento del grupo en tiempo real.

## ✨ Características Principales
1. **Flujo de Autenticación Completo:** Registro e inicio de sesión seguros mediante Firebase Auth.
2. **Sistema de Guardado en la Nube:** Progreso del jugador, inventario (runas) y nivel almacenados en Cloud Firestore.
3. **Motor de Evaluación Inteligente:** El `examen.html` valida lógica de código mediante normalización de strings (tolerancia a espacios y comillas) para evitar frustración en el usuario.
4. **Dashboard Administrativo (RBAC):** Panel exclusivo para maestros protegido por validación de roles. Muestra métricas en tiempo real y permite exportar reportes a CSV.
5. **UI/UX Temática:** Diseño responsivo *Dark Mode* con estética RPG, tipografías premium y Glassmorphism.

## 🔒 Arquitectura de Seguridad implementada
Para evitar el concepto *"Never trust the client"* y proteger la integridad académica, el sistema cuenta con:
* **Restricción de Dominio (API Keys):** Llaves de Google Cloud restringidas por HTTP Referrers.
* **Firestore Security Rules:** 
  * Los estudiantes solo tienen permisos de escritura sobre su propio `UID`.
  * **Regla Anti-Trampas:** El nodo de `calificacionExamen` solo permite operaciones `update` si el valor actual es `"Pendiente"`. Si un estudiante intenta inyectar código malicioso por consola (F12) para modificar su calificación tras haber hecho el examen, el backend rechaza la petición.
  * Lectura global restringida a un listado de correos autorizados en el Backend (Rol de Maestro).

## 🛠️ Stack Tecnológico
* **Frontend:** Vanilla HTML5, CSS3 avanzado (CSS Variables, Grid, Flexbox, Animations) y JavaScript (ES6+ Modules).
* **Backend (BaaS):** Firebase Authentication & Cloud Firestore.
* **Hosting:** Netlify (CI/CD Deploy).

## 📸 Capturas de Pantalla
* `![Login](./screenshots/login.jpeg)` - Pantalla de Acceso.
* `![Game](./screenshots/game.jpeg)` - Interfaz del Juego y Consola.
* `![Dashboard](./screenshots/dashboard.jpeg)` - Panel B2B del Profesor.
