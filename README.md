royecto educativo de mapeo colaborativo desarrollado por el Prof. René L. Martinez del espaco Tecnologias Digitales y Computacionales, para estudiantes del CEIJA N° 4 SAN FRANCISCO. 
Permite registrar, geolocalizar y documentar puntos de interés del entorno local en tiempo real.

📌 ¿Qué es este proyecto?
Este es un mapa interactivo colaborativo diseñado para que grupos de estudiantes puedan:
Ubicar puntos de interés de su ciudad en un mapa digital.
Agregar información descriptiva detallada sobre cada lugar.
Subir fotos propias para ilustrar los puntos cargados.
Incorporar videos de YouTube relacionados con el lugar.
Identificar quién realizó cada aporte mediante nombre y apellido.
Visualizar en tiempo real los aportes del resto del grupo.
El proyecto fue pensado para el trabajo de campo en la ciudad de San Francisco, Córdoba, Argentina, pero puede adaptarse fácilmente a cualquier otra localidad.
🎯 Público objetivo
Docentes que buscan herramientas digitales para trabajar cartografía, geografía local, historia o ciencias sociales.
Estudiantes (grupos de hasta 20 personas) que realizan relevamiento de información sobre su entorno inmediato.
Instituciones educativas que desean digitalizar proyectos de investigación territorial.
🚀 Cómo acceder y usar el mapa
Para estudiantes (usuarios finales)
Abrir el link del mapa en cualquier navegador (Chrome, Firefox, Safari, Edge).
Ingresar nombre y apellido en la pantalla de bienvenida. Este dato queda guardado en el dispositivo, por lo que no es necesario volver a escribirlo en futuras visitas.
Explorar el mapa: hacer zoom, moverse por la ciudad y ver los puntos cargados por el grupo.
Agregar un punto:
Clic en el botón "Agregar punto".
Clic en el lugar exacto del mapa.
Completar los datos: nombre del lugar, rubro, descripción ampliada.
(Opcional) Subir hasta 3 fotos desde el dispositivo.
(Opcional) Pegar un link de YouTube.
Guardar. El punto aparecerá al instante para todos los usuarios conectados.
Editar un punto existente: hacer clic en el marcador y luego en "Editar". Se puede modificar cualquier campo, incluyendo el autor.
💡 Tip: Las fotos se redimensionan automáticamente para optimizar la carga y el almacenamiento.

⚙️ Configuración técnica (para docentes / administradores)
Este proyecto es una aplicación web de una sola página (SPA) que utiliza Firebase como backend. Requiere una configuración mínima antes de ponerlo en línea.
1. Requisitos previos
Una cuenta de Google (gratuita).
Acceso a Firebase Console.
Un servicio de hosting gratuito como GitHub Pages, Netlify o Vercel.
2. Crear el proyecto en Firebase
Ir a Firebase Console y crear un nuevo proyecto.
Dentro del proyecto, agregar una aplicación Web.
Copiar el objeto de configuración (firebaseConfig). Tendrá una forma similar a esta:
const firebaseConfig = {
  apiKey: "TU_API_KEY",
  authDomain: "tu-proyecto.firebaseapp.com",
  databaseURL: "https://tu-proyecto-default-rtdb.firebaseio.com",
  projectId: "tu-proyecto",
  storageBucket: "tu-proyecto.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef123456"
};
3. Activar los servicios necesarios
Realtime Database: ir a "Build > Realtime Database" y crear la base de datos. En las reglas de seguridad, iniciar en modo prueba (permite lectura/escritura durante 30 días; ideal para proyectos educativos cortos).
Authentication: ir a "Build > Authentication" y habilitar el proveedor Anónimo. Esto permite que los estudiantes interactúen sin necesidad de crear cuentas.
4. Configurar el archivo
Abrir el archivo mapa-colaborativo-san-francisco.html y reemplazar el objeto firebaseConfig de ejemplo por el que copiaste desde Firebase Console.
5. Publicar en línea
Subir el archivo a un servicio de hosting. Algunas opciones gratuitas:
Servicio
URL
Notas
GitHub Pages
pages.github.com
Ideal si ya usás GitHub. Solo subir el archivo a un repositorio público.
Netlify
netlify.com
Arrastrar y soltar el archivo. URL propia al instante.
Vercel
vercel.com
Muy rápido para archivos estáticos.
Una vez publicado, compartir el link generado con los estudiantes.
🛠️ Características técnicas
Frontend: HTML5, CSS3 y JavaScript vanilla (sin frameworks).
Mapa: Leaflet.js con capa base de OpenStreetMap.
Backend y sincronización: Firebase Realtime Database (sincronización en tiempo real).
Autenticación: Firebase Anonymous Auth.
Imágenes: procesamiento en el navegador (redimensionado automático a 800px, compresión optimizada) y almacenamiento en base64 dentro de la base de datos.
Videos: embebido nativo de YouTube mediante iframe.
Responsive: diseño adaptable a celulares, tablets y computadoras.
Sin servidor propio: toda la infraestructura corre sobre Firebase (plan Spark gratuito).
📁 Estructura del repositorio
.
├── mapa-colaborativo-san-francisco.html   # Aplicación completa (HTML + CSS + JS + Firebase)
├── README.md                              # Este documento
└── (opcional) assets/                     # Imágenes o recursos adicionales
El proyecto está contenido en un único archivo HTML para facilitar su distribución y despliegue. No requiere instalación de dependencias ni compilación.

💰 Costos y limitaciones
Este proyecto utiliza el plan Spark (gratuito) de Firebase, que incluye:
100 conexiones simultáneas (suficiente para grupos de hasta 20 estudiantes).
1 GB de datos descargados por mes.
Almacenamiento en Realtime Database limitado (las imágenes se guardan en base64 dentro de la DB).
Consideraciones importantes:
Las imágenes se almacenan directamente en la base de datos en formato base64. Esto funciona bien para proyectos con pocos usuarios y pocas fotos. Para escalabilidad mayor, se recomendaría migrar a Firebase Storage.
El modo prueba de la base de datos permite acceso abierto por 30 días. Para proyectos prolongados, se deben ajustar las reglas de seguridad.
El límite del plan gratuito es más que suficiente para una experiencia educativa de duración estándar (1 a 3 meses).
🔒 Privacidad y datos
Los estudiantes ingresan únicamente nombre y apellido (sin correo ni datos personales sensibles).
La autenticación es anónima; Firebase genera un ID único por sesión.
Los datos almacenados pertenecen al proyecto Firebase del docente/a administrador/a.
Se recomienda borrar la base de datos al finalizar el proyecto educativo.
❓ Preguntas frecuentes
¿Puedo usar este mapa en otra ciudad?
Sí. Solo tenés que cambiar las coordenadas iniciales del mapa dentro del archivo HTML (buscar center y zoom en la configuración de Leaflet).
¿Los estudiantes necesitan crear una cuenta?
No. La autenticación es anónima. Solo se pide nombre y apellido para identificar los aportes.
¿Se pueden subir videos directamente desde el celular?
No. Los videos se agregan mediante un link de YouTube. Esto evita problemas de almacenamiento y formato.
¿Qué pasa si un estudiante cierra el navegador?
Sus aportes ya están guardados en la base de datos. Al volver a entrar, solo debe ingresar su nombre nuevamente.
¿Puedo limitar quién edita un punto?
En la versión actual, cualquier usuario puede editar cualquier punto. Esto fomenta la colaboración y la corrección entre pares. Si se requiere control de permisos, se debe adaptar el código.
👨‍🏫 Créditos y autoría
Desarrollado para: Instituciones educativas de San Francisco, Córdoba, Argentina.
Propósito: Apoyo a la enseña
