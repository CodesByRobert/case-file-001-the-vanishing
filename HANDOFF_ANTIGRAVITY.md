# CASE FILE 001 — THE VANISHING
## Expediente maestro de continuidad para Gemini Antigravity
Fecha: 17 de noviembre de 2026
Repositorio: CodesByRobert/case-file-001-the-vanishing
Estado: Fase 1 pendiente de validación real. No iniciar Fase 2 todavía.

> Este documento consolida el contexto del proyecto, las decisiones del propietario, los requisitos narrativos y técnicos, el estado de Claude, la inspección de GitHub y los pendientes. No sustituye los fuentes: Antigravity debe leer el código y los JSON reales del repositorio.

# 1. INSTRUCCIÓN PRINCIPAL

Continúa el proyecto existente. NO lo reconstruyas desde cero, no lo conviertas en una demo, no rehagas la interfaz ni alteres la historia. La identidad visual ya está definida. La prioridad ahora es cerrar la ingeniería: Firebase, seguridad, sincronización multidispositivo, persistencia, reconexión y pruebas.

Antes de editar:
1. Inspecciona el repositorio privado, ramas y PR #1.
2. Lee completos: index.html, database.rules.json, datos-iniciales.json y LEEME-FASE1.md.
3. Compara main con firebase-config-integration.
4. Haz inventario de módulos y funciones existentes.
5. Conserva el bloque Base64 de imágenes intacto; no lo reformatees, regeneres ni sustituyas.
6. Conserva personajes, sobres, pistas, cronología, secretos, evidencias, giros y resolución.
7. Distingue implementado, probado, pendiente y no verificable.
8. Trabaja en rama separada, con cambios pequeños y reversibles. No fusiones PR ni cambies main sin autorización.
9. No publiques GitHub Pages ni hagas público el repositorio hasta auditar reglas y exposición de datos.
10. No avances Fase 2 hasta que el usuario apruebe Fase 1.

# 2. IDENTIDAD Y OBJETIVO

- Nombre: CASE FILE 001 — THE VANISHING.
- Expediente: CASO MM-21-114.
- Juego web ficticio de investigación criminal, inmersivo y multijugador.
- Cada participante tiene pantalla, rol, sobre privado e información propia; comparte evidencias, comunicaciones, tablero y estado de partida.
- Director no cuenta como agente.
- Mínimo 3 y máximo 8 agentes; predeterminado 6.
- Debe funcionar en iPhone/Safari, Android/Chrome y escritorio.
- Interfaz en español, con rótulos documentales en inglés cuando sean parte de la ambientación.
- Estética federal/policial, expediente institucional oscuro, documentos y carpetas, papel envejecido; fuentes visibles Courier Prime e Inter.
- La interfaz y organización visual ya están trabajadas. No rediseñar: solo corregir detalles funcionales/responsivos sin alterar la identidad.

# 3. CANON NARRATIVO — NO INVENTAR NI CAMBIAR

El expediente es MM-21-114. Referencias narrativas conocidas: N-17, PALISADE, MERIDIAN, KESTREL, hechos documentales de 2021, almacén 14, muestra de sangre, informe preliminar modificado, registro de radio, puerta de carga, cadena de custodia y discrepancia horaria 21:50 frente a 22:14.

No conviertas indicios en hechos confirmados. No afirmes que N-17 murió si los documentos no lo prueban. No atribuyas al FBI institucional una autorización que no está probada. El testigo de la furgoneta no identificó conductor ni ocupantes.

## Personajes P-01 a P-08 (el JSON es la fuente de verdad)

- P-01: consultoría externa/revisión forense. Conservó observación que contradice el informe; la muestra demuestra presencia de sangre, no muerte. No es culpable ni colaborador de PALISADE.
- P-02: agente de enlace, identidad operativa L-02; afiliación aparente Miami Metro y afiliación real vinculada a contratista de integridad relacionado con MERIDIAN. No es culpable principal ni tiene pruebas de muerte de N-17.
- P-03: investigador/a de campo de Miami Metro. Conoce omisión del anexo de control de puerta de carga; objetivo comparar 21:50 y 22:14. No conoce identidad de N-17 antes de la USB.
- P-04: enlace comunitario/a y auxiliar de entrevistas. Un testigo vio una furgoneta salir después del aseguramiento del perímetro; no identificó conductor ni ocupantes.
- P-05: analista documental independiente. Registro de radio: perímetro principal asegurado 21:50; no demuestra que salidas secundarias estuvieran cerradas. No tiene evidencia de autorización institucional del FBI.
- P-06: coordinador/a de enlace / operador reservado. Código KESTREL. Recibió el primer aviso anónimo que permitió reabrir el expediente; no conoce ubicación de N-17 y no es autor de conspiración. Frase especial se lee solo después de votar.
- P-07: apoyo documental para séptimo agente. Verifica códigos, fechas, cadena de custodia y coincidencias; no tiene secreto de culpabilidad ni pista imprescindible.
- P-08: apoyo investigativo para octavo agente. Ayuda con fechas, horas y cadena de custodia; no inventa pruebas ni tiene secreto de culpabilidad.

Leer íntegramente los sobres reales en datos-iniciales.json. No resumirlos en sustitución del archivo ni exponer el sobre de un agente a otro. P-07/P-08 son apoyo y no reemplazan a personajes ni se convierten en culpables.

# 4. PARTICIPANTES Y ASIGNACIÓN

- 3–8 agentes, Director aparte; seis por defecto.
- Código de invitación por partida.
- Elección de rol o asignación automática.
- Ningún rol puede ser ocupado por dos agentes; reserva atómica con transacción.
- P-07 y P-08 son apoyo para partidas de 7 y 8.
- Presets actuales observados en index.html:
  - 3: P-02, P-03, P-06
  - 4: P-02, P-03, P-05, P-06
  - 5: P-02, P-03, P-04, P-05, P-06
  - 6: P-01 a P-06
  - 7: P-01 a P-07
  - 8: P-01 a P-08
- Distribución de información para 3–5 está pendiente de validación narrativa (Claude dijo que se deja para Fase 3). Debe preservar pistas y solución sin revelar secretos ajenos.

# 5. FUNCIONES Y EXPERIENCIA REQUERIDAS

## Pantalla/conexión
- Pantalla CONECTAR A LA CENTRAL.
- Primer gesto explícito activa AudioContext y solicita Wake Lock cuando esté disponible.
- Indicador: conectado, sincronizando, reconectando, sin conexión.
- Fallback visual si audio/autoplay no funciona.
- Fallback e instrucciones si Wake Lock no existe.

## Acceso y navegación
- Agentes: autenticación anónima + código de invitación + nombre.
- Dirección: correo/contraseña Firebase Auth; autorización por UID en Firebase.
- Sin PIN en HTML ni autenticación basada solo en interfaz.
- Barra inferior de cinco pestañas: Operaciones, Evidencias, Agente, Comms, Conclusiones.
- Etiqueta superior fija de rol, ejemplo P-03 · MI ROL.

## Operaciones
- Cronómetro 90 minutos (5.400.000 ms), sincronizado por hora del servidor.
- Historial cronológico, filtros, estado de conexión, fase.
- Timer con startAt/endAt/estado/pausas y offset del servidor; cada móvil calcula restante. No depender de intervalos locales ni de un único móvil.

## Evidencias
- E-001 / FTG-10, E-002 / DVC-25, E-003 / MSG-60.
- Descripción, contexto, imagen/documento, modal/visor y preguntas orientadoras.
- Dirección desbloquea y redacciona en vivo; sincronización global.
- Preservar el expediente visual ya existente.

## Tablero colaborativo
- Conexiones de pistas/testimonios con SVG o equivalente.
- Sincronizado; registrar autoría si procede.
- No permitir que agentes modifiquen evidencia oficial.

## Agente
- Perfil, sobre privado, objetivos, checklist, libreta privada.
- Notas privadas por defecto; no usar localStorage como seguridad ni fuente de verdad compartida.

## Comunicaciones
- Bandeja, mensajes globales y privados, transmisiones, llamadas anónimas ramificadas, respuestas, transcripción y sincronización.
- Voz/síntesis en español con fallback.

## Conclusiones
- Línea de tiempo, voto secreto, justificación, cierre por Dirección, revelación, resolución oficial.
- Alerta final 10 minutos.
- Revelación especial P-06 solo después de votación y respetando el canon.

## Dirección
- Configurar 3–8 agentes, crear código, controlar fases/evidencias/timer.
- Ver jugadores y presencia, liberar roles, revisar comunicaciones autorizadas.
- Cerrar votación, reiniciar con confirmación y respaldo, consultar auditoría.
- Exclusividad de Dirección debe ser real, no una variable local.

# 6. MECÁNICAS DE INMERSIÓN SOLICITADAS

1. Luz ultravioleta/luz negra: mantener pulsado botón en fotos seleccionadas y revelar overlay forense separado. CSS filter no puede revelar píxeles/datos que no existen en la foto; crear overlay por imagen.
2. 2–3 cruces obligatorios de pistas entre dos agentes. Ejemplo conversado: placa de P-02 + código CCTV de P-05. Validar dos UIDs autenticados distintos, no dos códigos escritos.
3. Sabotaje de un uso, reversible/temporal y auditado, compatible con el personaje y el canon. Nunca borrar evidencia original ni conexiones.
4. Minijuego de radio: slider de frecuencia, 30 segundos, estática que disminuye al acertar; validación importante no solo cliente; fallback visual.
5. Informe final personalizado estilo periódico/expediente: basado en eventos reales, aciertos de voto, objetivos, decisiones, participación y engaños detectados. No inventar métricas.
6. Consecuencias por decisiones: pistas extra o testimonios contradictorios definidos y auditados, sin cambiar hechos canónicos.
7. Eventos sorpresa controlados por Dirección: filtración, interferencia, nuevo testigo, documento restringido; con efecto, duración, visibilidad y registro.

# 7. ARQUITECTURA ACORDADA

## Frontend/hosting
- Aplicación estática en index.html.
- GitHub Pages es opción de hosting, pero no es backend ni protege secretos.
- No migrar a React/Vite/Next ni añadir bundler sin autorización.
- Mantener el HTML existente y sus dependencias actuales.
- Repositorio indicado como privado por el usuario.

## Firebase
- Proyecto: case-file-001-the-vanishing.
- Plan visto: Spark.
- Realtime Database URL observada: https://case-file-001-the-vanishing-default-rtdb.firebaseio.com
- Región mostrada: us-central1.
- Authentication mostró Anónimo y Correo/contraseña habilitados.
- Aplicación web registrada: case-file-001-web.
- El firebaseConfig ya fue integrado en la rama del PR #1.
- La configuración web/client apiKey es pública; la seguridad depende de Authentication y Rules. Nunca incluir service-account/private keys/tokens/passwords en frontend.
- HTML usa Firebase JS SDK Compat 10.12.2 por CDN. Mantener Compat y no mezclar imports modulares sin migración completa.

## Base de datos
- datos-iniciales.json contiene admins y partidas/caso-001 con sobres P-01…P-08 y configuración.
- Usuario confirmó importación del JSON.
- La consola mostró admins y partidas/caso-001.
- El usuario añadió su UID de Auth bajo admins con boolean true.
- No copiar UID personal a HTML. Si se requiere, obtenerlo de Firebase Console.

## Seguridad
- Raíz .read/.write false.
- Miembro autenticado solo lee su sobre.
- Dirección puede leer los sobres/datos privados necesarios.
- Agentes no modifican estado global/evidencias/configuración.
- Validar identidad por UID y reglas Firebase, no ocultando UI.
- No confiar en validaciones cliente.
- No usar read/write true como arreglo.
- Revisar invitación, acceso a sobres, lectura masiva, escritura de rol, suplantación, presencia, historial, estado, evidencias, backups y reset.
- Registrar acciones privilegiadas de forma confiable.

### Restricción de Spark / backend
LEEME-FASE1.md dice que se usa Spark y no Cloud Functions. Por tanto, no asumir funciones backend disponibles. Resolver lock de Dirección, eventos confiables e historial con reglas/transacciones atómicas viables o documentar si se necesita otro backend/plan. Nunca afirmar que algo está protegido por servidor si solo lo controla JavaScript del cliente.

# 8. REPOSITORIO Y PULL REQUEST

Repo: https://github.com/CodesByRobert/case-file-001-the-vanishing
Usuario indicó que lo puso privado.
Archivos subidos:
- index.html
- database.rules.json
- datos-iniciales.json
- LEEME-FASE1.md

PR #1: https://github.com/CodesByRobert/case-file-001-the-vanishing/pull/1
Título: Integrar configuración web de Firebase en Fase 1
Rama: firebase-config-integration
Base: main
Snapshot inicial: abierto, 1 commit, 1 archivo cambiado (index.html), +10/-1. GitHub devolvió mergeable false/no confirmado; revisar estado actual.
Cambio: añade firebaseConfig real de case-file-001-web al HTML, mantiene Firebase Compat 10.12.2. Se indicó que Base64 y expediente se conservan. No fusionar automáticamente; revisar diff y probar primero.

# 9. INFORME DE CLAUDE — REPORTE, NO CERTIFICACIÓN

Claude dijo “Fase 1 lista, pero sin probar contra Firebase”. Entregó los cuatro archivos anteriores.
Afirmó haber implementado:
- CONECTAR A LA CENTRAL, audio y Wake Lock;
- login agentes con invitación y Dirección con correo/contraseña;
- elección/asignación de rol;
- etiqueta P-03 · MI ROL y cinco pestañas;
- operaciones con timer basado en servidor, historial y conexión;
- panel Dirección 3–8 agentes, invitación, timer, evidencias, liberar roles y reinicio con backup;
- sobres fuera del HTML en Firebase;
- Base64 intacto y expediente en Evidencias.
Claude reportó pruebas de simulador: sin errores en su entorno, páginas dibujan, panel y sobre P-06 se comportan, frase de revelación no está en HTML.
Claude reconoció que no probó Firebase real, varios celulares, iPhone ni Android.
Limitaciones admitidas:
1. lock único de Dirección controlado por app, no reglas;
2. historial de cambios de fase depende del celular Dirección;
3. redistribución 3–5 pendiente;
4. libreta, transmisiones y votación para fases posteriores.
Todo esto es reporte de Claude y debe verificarse independientemente.

# 10. REVISIÓN PRELIMINAR DE RULES

El JSON actual tiene raíz denegada, acceso admin a privado, inscripción de miembros condicionada al código, lectura de config/estado/evidencias para miembros y admins, jugadores, presencia, historial, sobres y respaldos.
No es auditoría/certificación de seguridad. Probar:
- que código de invitación no se pueda leer/exfiltrar;
- P-03 no lee P-06/P-01 ni toda la colección sobres;
- agente no cambia estado/evidencias/config;
- agente no puede modificar UID/rol ajeno;
- dos claims simultáneos del mismo rol: solo uno;
- no admin no accede a funciones Dirección;
- historial no se falsifica ni depende solo de teléfono Dirección;
- reset/backup solo Dirección;
- validación de estructura/tipo/longitud;
- todos los intentos prohibidos devuelven permission_denied.
No abrir reglas para hacer funcionar la app.

# 11. SINCRONIZACIÓN Y ROBUSTEZ

- RTDB fuente compartida para timer, pausas, fase, evidencias, mensajes, llamadas, presencia, tablero, votos e historial.
- .info/connected y onDisconnect para presencia con cuidado; desconexión temporal no debe liberar rol.
- Reserva atómica de rol con transacción.
- Reconexion recupera identidad/rol/estado.
- ServerValue.TIMESTAMP y serverTimeOffset.
- Timer por startAt/endAt/status/pauses.
- Idempotencia y protección doble clic.
- Eventos importantes en auditoría.
- Reset con confirmación, backup y recuperación.
- Secretos no se guardan en localStorage como mecanismo de seguridad.
- Evitar listeners duplicados.

# 12. COMPATIBILIDAD

Probar iPhone Safari, Android Chrome y escritorio Chrome.
Revisar safe areas, viewport, scroll, portada, modales, barra inferior, controles táctiles, Wake Lock, retorno desde segundo plano, AudioContext con gesto, síntesis, reconexión, refresco y persistencia. No prometer autoplay, vibración o Wake Lock universal.

# 13. FASES

**Fase 1 — Base/Firebase:** conexión, Auth, roles/miembros, invitación, reglas de sobres, presencia, estado, timer compartido, panel Dirección, historial, reconexión. Código reportado; Firebase real y pruebas multidispositivo pendientes. Cerrar antes de continuar.

**Fase 2 — Evidencias/tablero:** E-001/FTG-10, E-002/DVC-25, E-003/MSG-60, documentos, imágenes, modales, preguntas, desbloqueo, redacciones, tablero SVG colaborativo.

**Fase 3 — Agente/secretos:** sobres privados, perfiles, libreta, checklist, distribución 3–5, roles 7–8, cruces entre agentes, UV, sabotaje reversible, descifrado y privacidad.

**Fase 4 — Comunicaciones:** bandeja, mensajes globales/privados, transmisiones, voz en español, llamadas ramificadas, respuestas, transcripción y sync.

**Fase 5 — Conclusión:** timeline, votos secretos, justificaciones, cierre/revelación, resolución, alerta 10 minutos, panel completo, informe individual, exportación y reset seguro.

# 14. PRUEBAS DE ACEPTACIÓN FASE 1

| Prueba | Esperado |
|---|---|
| Dirección login | UID autorizado se reconoce como admin |
| Agente anónimo | entra al flujo de invitación |
| Código incorrecto | rechazado |
| Código correcto | miembro registrado |
| Dos agentes reclaman mismo rol | solo uno lo obtiene |
| P-03 lee su sobre | permitido |
| P-03 lee P-06 | permission_denied |
| P-03 lee colección sobres | denegado |
| Agente modifica estado/evidencias | denegado |
| Agente simula Dirección | denegado |
| Timer inicia/pausa/reanuda | todos coinciden ±1 s |
| Se pierde internet | muestra reconexión |
| Vuelve internet | recupera rol sin duplicarse |
| Dirección cierra navegador | eventos críticos no se pierden |
| Dos sesiones Dirección | control exclusivo explícito y seguro |
| Reset | confirmación + backup |
| No autorizado lee privado | denegado |

Guardar resultados reproducibles, capturas y pasos de prueba.

# 15. PROHIBICIONES / ERRORES A EVITAR

No reconstruir desde cero; no rediseñar; no tocar Base64; no cambiar canon ni sobres; no inventar culpables; no afirmar muerte de N-17 sin evidencia; no poner sobres privados en HTML público; no poner credenciales de servicio en cliente; no confiar solo en validación cliente; no abrir Rules; no hacer depender timer/historial de un solo teléfono; no borrar evidencia para sabotaje; no usar CSS como revelación mágica; no fingir dos agentes con dos códigos; no introducir bundlers/migraciones sin aprobación; no publicar antes de auditar; no fusionar PR sin aprobación; no iniciar fase siguiente porque una IA diga que está lista.

# 16. FORMA DE TRABAJO PARA ANTIGRAVITY

1. Confirmar acceso al repo privado.
2. Leer cuatro archivos y revisar PR.
3. Entregar diagnóstico: ramas, arquitectura, módulos, estado del PR, riesgos, implementado/probado/pendiente.
4. No editar antes del diagnóstico.
5. Proponer plan mínimo y reversible para cerrar Fase 1.
6. Implementar en rama de trabajo autorizada, no main directamente.
7. Probar Firebase real con identidades y dispositivos diferentes.
8. Entregar archivos cambiados, razón, pruebas y resultados, pendientes y pasos simples para el usuario.
9. Esperar aprobación para Fase 2.

# 17. MENSAJE INICIAL PARA ANTIGRAVITY

Actúa como ingeniero principal de CASE FILE 001 — THE VANISHING. Lee este expediente y audita el repositorio privado CodesByRobert/case-file-001-the-vanishing, todos los archivos, ramas y PR #1. No reconstruyas, no rediseñes, no cambies historia ni sobres. Conserva Base64. Tu primera tarea es diagnosticar y cerrar Fase 1: Firebase Auth/RTDB, reglas, sobres privados, invitación, reserva atómica de roles, presencia, reconexión, timer compartido, historial y Dirección. Distingue lo implementado de lo reportado por Claude; no afirmes que Firebase funciona hasta probarlo en el proyecto real con UIDs distintos y varios dispositivos. No fusiones PR ni empieces Fase 2 sin aprobación. Primero entrega diagnóstico, riesgos y plan pequeño y reversible; después espera confirmación. Los detalles canónicos están en datos-iniciales.json y el expediente original.

# 18. PREFERENCIAS DEL PROPIETARIO

- Continuar desde el código real ya existente; no empezar de cero.
- No rediseñar la interfaz ya establecida.
- Priorizar funcionamiento técnico, seguridad, sincronización y móvil.
- Español claro y pasos concretos.
- 3–8 agentes más Dirección.
- Mantener HTML actual y evitar bundlers/dependencias de compilación sin aprobación.
- Firebase Realtime Database elegida.
- Usuario usará Claude/Antigravity para implementar y ChatGPT para revisión y apoyo.
- No pedir volver a subir a Claude el HTML que ya tenía; Antigravity debe inspeccionar el repositorio.

# 19. ESTADO AL 17/11/2026

**Confirmado por usuario/inspección:**
- Repo CodesByRobert/case-file-001-the-vanishing; usuario dijo que es privado.
- Cuatro archivos subidos.
- Proyecto Firebase creado; Authentication mostró Anónimo y correo/contraseña habilitados.
- App web case-file-001-web registrada.
- JSON inicial importado según usuario.
- Consola mostró admins y partidas/caso-001.
- UID del usuario agregado bajo admins con valor true.
- PR #1 creado en firebase-config-integration.
- Se inspeccionaron LEEME-FASE1.md, database.rules.json, datos-iniciales.json y comienzo de index.html en esa rama.

**Reportado por Claude, no verificado independientemente:** funciones de Fase 1 y pruebas de simulador.

**Pendiente crítico:** auditar reglas reales; probar sobres y lectura masiva; probar acceso Dirección y agentes; invitación; atomicidad de roles; exclusividad Dirección; sincronización; historial confiable; timer; reconexión; iPhone/Android; revisar PR #1. No iniciar Fase 2.

— Fin del expediente maestro —
