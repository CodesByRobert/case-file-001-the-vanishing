# CASE FILE 001 — Fase 1: configuración (todo se puede hacer desde el celular)

Archivos principales: `index.html` y `database.rules.json`. El archivo `datos-iniciales.json` fue retirado del repositorio por contener información privada de los personajes.

## A. Firebase (console.firebase.google.com, con tu cuenta de Google)
1. **Crear proyecto** (puedes desactivar Analytics). Plan **Spark (gratis)**; no se usan Cloud Functions.
2. **Authentication → Método de acceso**: activa **Anónimo** y **Correo/contraseña**.
3. **Authentication → Usuarios → Agregar usuario**: crea la cuenta de Dirección (tu correo y una contraseña larga). Copia el **UID** que aparece.
4. **Realtime Database → Crear base de datos** (modo bloqueado).
5. Pestaña **Reglas**: pega todo el contenido de `database.rules.json` y publica.
6. **No importes `datos-iniciales.json`**: ese archivo ya no forma parte del proyecto y no debe volver a publicarse porque contenía sobres privados. La aplicación utiliza la ruta `partidas/caso-001` de Realtime Database. No reemplaces ni importes datos sobre una base que ya tenga una partida.
7. En **Datos**, agrega a mano en la raíz: `admins` → `<TU UID>` = `true` (booleano). Este paso habilita la cuenta de Dirección; conserva exactamente el UID de la cuenta creada en Authentication.
8. **Configuración del proyecto → Tus apps → Web**: copia `apiKey`, `authDomain`, `databaseURL`, `projectId`, `appId`.
9. **Authentication → Configuración → Dominios autorizados**: agrega `TUUSUARIO.github.io`.

## B. index.html
Abre `index.html` y pega tus datos en el bloque `firebaseConfig` (está comentado, cerca del inicio del script). No toques el bloque `ASSETS`.

## C. GitHub Pages
Repositorio nuevo (público) → **Add file → Upload files** → sube `index.html` → **Settings → Pages** → rama `main`, carpeta `/ (root)`. Tu link será `https://TUUSUARIO.github.io/NOMBRE-REPO/`.

## D. Datos privados y seguridad\n- Los sobres de personajes (`sobres/P-01` a `sobres/P-08`) contienen información que no debe publicarse ni compartirse entre jugadores.\n- No guardes sobres, secretos, claves ni datos privados en archivos del repositorio público, capturas o mensajes compartidos.\n- Los datos privados deben cargarse únicamente en la ubicación protegida de Firebase y sus permisos deben comprobarse con las reglas antes de iniciar una partida.\n- Si la base ya contiene información, no la reemplaces con una importación general. Haz primero una copia de seguridad.\n\n## E. Uso
- **Dirección**: entra con tu correo/contraseña → elige cuántos agentes → **NUEVO CÓDIGO** → comparte link y código.
- **Agentes**: abren el link → CONECTAR A LA CENTRAL → código (y nombre) → eligen personaje o "asignar automáticamente".

## Pruebas SIN hacer (necesitan tu proyecto Firebase y varios celulares)
1. Dos celulares eligen el mismo personaje al mismo tiempo: solo uno debe entrar.
2. Un agente intenta leer `sobres/P-0X` de otro (desde la consola del navegador): debe dar "permission denied".
3. Un agente intenta escribir `estado` o `evidencias`: debe fallar.
4. Código de invitación incorrecto: no debe poder entrar.
5. Apagar los datos de un celular y reconectar: debe volver a "conectado" y conservar su personaje.
6. Dos sesiones de Dirección: la segunda debe ver el aviso y "TOMAR CONTROL".
7. Pausa/reanudar: los cronómetros de todos los celulares deben coincidir (±1 s).
