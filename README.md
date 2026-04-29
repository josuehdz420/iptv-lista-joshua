📺 IPTV Lista Fútbol — Joshua
> Lista M3U personal de canales de fútbol y deportes, organizada por tipo de fuente y estabilidad de conexión.
---
📋 Tabla de contenido
Descripción general
Contenido de la lista
Grupos de canales
Estructura del archivo M3U
Requisitos según grupo
Cómo usar la lista
AceStream — Guía de configuración
Reproductores recomendados
Diferencias entre grupos
Preguntas frecuentes
Aviso legal
---
📖 Descripción general
Este repositorio contiene el archivo `Lista_Fut.m3u`, una lista de reproducción en formato M3U orientada exclusivamente a canales de fútbol y deportes. Incluye canales como DAZN, Movistar Deportes, ESPN, Fox Sports, LaLiga TV, Champions League y más.
La lista está dividida en cuatro grupos según el tipo de tecnología de streaming y la estabilidad esperada de cada fuente, lo que facilita elegir la mejor opción disponible en cada momento.
Incluye enlace a una guía EPG (Electronic Program Guide) para visualizar la programación de los canales en reproductores compatibles.
---
📊 Contenido de la lista
Grupo	Tecnología	Canales	Estabilidad
AceStream	P2P (infohash)	21	⭐⭐⭐⭐ Alta (en vivo)
AceStream Legacy	P2P (id + pid)	24	⭐⭐⭐⭐ Alta (en vivo)
Inestables	Xtream Codes HTTP	19	⭐⭐ Baja
Medio Estables	Xtream Codes HTTP	22	⭐⭐⭐ Media
Total de entradas: 86 canales
---
📡 Grupos de canales
🟢 AceStream (Motor Ace — Infohash)
Canales transmitidos a través del motor AceStream usando el parámetro `infohash`. Este es el método más moderno y directo de AceStream.
Canal
DAZN LaLiga
DAZN 1 / DAZN 2 / DAZN 3 / DAZN 4
Movistar Deportes HD (×6)
Movistar Golf HD
Movistar LaLiga (×4)
Movistar Champions (×4)
Formato de URL:
```
http://127.0.0.1:6878/ace/getstream?infohash=<HASH>
```
---
🟡 AceStream Legacy (Motor Ace — ID + PID)
Canales AceStream que usan el parámetro combinado `id` + `pid` (formato más antiguo, aún funcional). Algunos también admiten `infohash` como alternativa.
Canales incluidos: ESPN 1, Real Madrid TV, TNT Sports Premium, Ligue 1 (×2), La 1, La 2, Win Sports, DAZN LaLiga (×5), Movistar LaLiga (×4), Movistar Champions (×4).
Formatos de URL:
```
http://127.0.0.1:6878/ace/getstream?id=<ID>&pid=<PID>
http://127.0.0.1:6878/ace/getstream?infohash=<HASH>
```
---
🔴 Inestables (Xtream Codes — infinitisurl.com)
Canales servidos mediante protocolo Xtream Codes desde el servidor `infinitisurl.com:8080`. Clasificados como inestables porque la disponibilidad del servidor es impredecible.
Canales incluidos: Canal 4 SV, DAZN LaLiga (×2), Movistar Plus, Movistar LaLiga, Sky LaLiga, ESPN (×3), ESPN Channel (×2), DAZN 1 HD, DAZN 1–3, Movistar Champions (×2), Movistar Vamos, La 1.
Formato de URL:
```
http://infinitisurl.com:8080/<usuario>/<clave>/<id-canal>
```
---
🟠 Medio Estables (Xtream Codes — live.zapping.life)
Canales desde el servidor `live.zapping.life:8080`, con mayor estabilidad que el grupo anterior pero sin garantía de disponibilidad continua.
Canales incluidos: Canal 4 SV, ESPN (×5), ESPN Channel, ESPN Deportes, Fox Deportes, Fox Sports, Win Sports (×2), Movistar Vamos, La 1, Movistar Deportes, DAZN 1–2, Movistar LaLiga (×6).
Formato de URL:
```
http://live.zapping.life:8080/<usuario>/<clave>/<id-canal>
```
---
🧩 Estructura del archivo M3U
El archivo `Lista_Fut.m3u` sigue el estándar extendido EXTM3U:
```m3u
#EXTM3U url-tvg="http://epg.one/epg2.xml.gz"

#EXTINF:-1 group-title="NombreGrupo",Nombre del Canal
http://url-del-stream
```
Cabecera
```m3u
#EXTM3U url-tvg="http://epg.one/epg2.xml.gz"
```
`#EXTM3U` — declara el archivo como lista M3U extendida.
`url-tvg` — enlace a la guía de programación electrónica (EPG) en formato XML comprimido (gzip), servida desde `epg.one`. Compatible con reproductores como Kodi, TiviMate e IPTV Smarters.
Entrada de canal
Cada canal se define con exactamente dos líneas:
```m3u
#EXTINF:<duración> <atributos>,<Nombre del Canal>
<URL del stream>
```
Campo	Valor en esta lista	Descripción
`duración`	`-1`	Duración indefinida (stream en vivo)
`group-title`	`"AceStream"`, `"Inestables"`, etc.	Grupo/categoría del canal en el reproductor
`Nombre del Canal`	`DAZN 1`, `ESPN`, etc.	Nombre visible en el reproductor
URL	`http://127.0.0.1:6878/...` o `http://servidor:8080/...`	Dirección del stream
Ejemplo completo de una entrada
```m3u
#EXTINF:-1 group-title="AceStream",DAZN LaLiga
http://127.0.0.1:6878/ace/getstream?infohash=8a25653a2f774f4ae1062d38a30dcd714d304a3a
```
---
⚙️ Requisitos según grupo
Para canales AceStream y AceStream Legacy
Requisito	Descripción
AceStream Engine	Debe estar instalado y ejecutándose en el equipo local
Puerto local	El motor escucha en `127.0.0.1:6878` por defecto
Sistema operativo	Windows, Linux o Android
Conexión	Buena velocidad de subida y bajada (red P2P)
Reproductor	Cualquier reproductor M3U/IPTV
> ⚠️ Las URLs de AceStream apuntan a `127.0.0.1` (localhost). El motor AceStream debe correr **en el mismo dispositivo** donde se reproduce la lista. No funcionan directamente desde otros dispositivos de la red.
---
Para canales Inestables y Medio Estables
Requisito	Descripción
Acceso al servidor	Las credenciales ya están embebidas en la URL
Conexión a internet	Sin restricciones en el puerto `8080`
Reproductor	Cualquier reproductor compatible con streams HTTP/HLS
Software adicional	Ninguno — no requiere AceStream
> ℹ️ Si tu ISP bloquea el puerto **8080**, estas fuentes no funcionarán. Verifica con tu proveedor de internet.
---
▶️ Cómo usar la lista
Opción A — Cargar desde archivo local
Descarga el archivo `Lista_Fut.m3u` desde este repositorio.
Ábrelo directamente con tu reproductor IPTV favorito (VLC, Kodi, TiviMate, etc.).
El reproductor detectará automáticamente los grupos y canales.
Opción B — Cargar desde URL raw de GitHub
Ve al archivo `Lista_Fut.m3u` en GitHub.
Haz clic en el botón Raw.
Copia la URL resultante:
```
   https://raw.githubusercontent.com/tu-usuario/iptv-lista-joshua/main/Lista_Fut.m3u
   ```
Pégala en tu reproductor IPTV como fuente de lista M3U remota.
> ✅ Esta opción permite recibir actualizaciones automáticas cada vez que el archivo cambie en el repositorio, sin tener que volver a descargarlo manualmente.
Opción C — Clonar el repositorio
```bash
git clone https://github.com/tu-usuario/iptv-lista-joshua.git
```
Luego carga el archivo `Lista_Fut.m3u` desde la carpeta clonada en tu reproductor.
---
🔧 AceStream — Guía de configuración
Los grupos AceStream y AceStream Legacy requieren el motor AceStream activo en el dispositivo.
Windows
Descarga AceStream Engine desde acestream.org.
Instala y ejecuta. El motor aparecerá minimizado en la barra de tareas.
El motor escucha automáticamente en `http://127.0.0.1:6878`.
Abre tu reproductor M3U, carga la lista y los canales AceStream funcionarán.
Linux
```bash
# Instalar desde repositorio oficial (Debian/Ubuntu)
sudo apt install acestream-engine

# O mediante pip
pip3 install acestream-engine

# Iniciar el motor
acestream-engine
```
Android
Instala Ace Stream Media desde Google Play o APK oficial.
Abre la app y deja que el motor se inicie en segundo plano.
Usa TiviMate o IPTV Smarters para cargar la lista `Lista_Fut.m3u`.
Verificar que el motor está activo
Abre en tu navegador mientras el motor esté corriendo:
```
http://127.0.0.1:6878/webui/app/
```
Si ves la interfaz web de AceStream, el motor está activo. Si el navegador no responde, el motor no está corriendo.
Diferencia entre AceStream normal y Legacy
Parámetro	AceStream (moderno)	AceStream Legacy
URL	`?infohash=<hash>`	`?id=<id>&pid=<pid>`
Identificador	Hash SHA-1 del contenido	ID de canal + ID de proveedor
Compatibilidad	Versiones recientes	Versiones antiguas y recientes
Funcionamiento real	Igual	Igual
Ambos grupos funcionan de la misma manera con el motor activo. La diferencia es puramente técnica según cómo fue registrado el canal en la red P2P de AceStream.
---
📱 Reproductores recomendados
PC — Windows / Linux / macOS
Reproductor	M3U	EPG	AceStream	Notas
VLC	✅	❌	✅*	Gratuito. Usar Abrir URL
Kodi	✅	✅	✅**	Con addon PVR IPTV Simple
MPV	✅	❌	✅*	Liviano, por línea de comandos
*El motor AceStream debe estar corriendo; VLC/MPV reciben el stream como HTTP local desde `127.0.0.1:6878`.
**Requiere addon AceStream para Kodi además del motor.
Android / Android TV
Reproductor	M3U	EPG	AceStream	Notas
TiviMate	✅	✅	✅*	El mejor para Android TV
IPTV Smarters Pro	✅	✅	✅*	Popular en móvil y TV box
GSE Smart IPTV	✅	✅	❌	Solo canales HTTP
Ace Stream Media	✅	❌	✅	App oficial, todo en uno
iOS / Apple TV
Reproductor	M3U	EPG	AceStream	Notas
IPTV Smarters	✅	✅	❌	Solo canales HTTP
GSE Smart IPTV	✅	✅	❌	Solo canales HTTP
> ℹ️ AceStream **no tiene soporte oficial para iOS/iPadOS ni Apple TV**. En esos dispositivos solo funcionarán los grupos Inestables y Medio Estables.
---
🔍 Diferencias entre grupos
Esta tabla resume cuándo conviene usar cada grupo:
Situación	Grupo recomendado
Tienes AceStream instalado	AceStream (primera opción siempre)
AceStream funciona pero el canal no carga	AceStream Legacy (alternativa directa)
No tienes AceStream y quieres algo rápido	Medio Estables
Medio Estables falla o está caído	Inestables (último recurso)
Estás en iOS / Apple TV	Medio Estables o Inestables
Necesitas máxima calidad de imagen	AceStream (sin recompresión de servidor)
¿Por qué AceStream puede ser mejor que los streams HTTP?
Los canales AceStream funcionan sobre una red P2P descentralizada (similar a BitTorrent):
No dependen de un servidor central que pueda caerse o bloquearse.
La calidad es la original del canal, sin recompresión.
Son más resistentes a bloqueos por parte de los ISP.
La desventaja es que requieren el motor instalado localmente y un tiempo de buffering inicial mientras la red P2P localiza peers suficientes. Fuera de horarios de partidos o eventos, puede que no haya peers activos y el canal no cargue.
¿Por qué los grupos HTTP fallan con frecuencia?
Los grupos Inestables y Medio Estables dependen de servidores IPTV de terceros que pueden:
Caerse o reiniciar sin previo aviso.
Rotar sus URLs o credenciales periódicamente.
Ser bloqueados por ISP o por los titulares de derechos.
Tener límite de conexiones simultáneas.
---
❓ Preguntas frecuentes
¿Por qué los canales AceStream tardan en cargar?
Es normal. AceStream necesita conectarse a la red P2P y encontrar peers activos. Espera entre 30 segundos y 2 minutos. Cuantos más espectadores activos tenga el stream, más rápido conectará.
¿Los canales funcionan las 24 horas?
Los canales AceStream solo están disponibles cuando hay alguien transmitiendo o recompartiendo el stream en la red. Fuera de horarios de partidos importantes, es probable que no haya stream activo. Los canales HTTP dependen del servidor de terceros.
¿Puedo reproducir la lista desde otro dispositivo de mi red?
Las URLs de AceStream apuntan a `127.0.0.1` (el propio equipo). Para usarlas desde otro dispositivo de la red, deberías instalar y correr AceStream en ese dispositivo también. Los canales HTTP (Inestables y Medio Estables) sí pueden reproducirse desde cualquier dispositivo sin problema.
¿El EPG funciona en todos los reproductores?
La guía EPG (`http://epg.one/epg2.xml.gz`) solo funciona en reproductores que admiten el atributo TVG, como Kodi, TiviMate e IPTV Smarters. VLC no muestra EPG. Además, para que la guía se asocie correctamente a cada canal, los canales deberían incluir el atributo `tvg-id`, que actualmente no está definido en esta lista.
¿Puedo editar la lista para añadir o quitar canales?
Sí. El archivo `.m3u` es texto plano. Puedes abrirlo con cualquier editor de texto (Notepad, VS Code, Notepad++, etc.) y modificar, agregar o eliminar entradas respetando el formato de dos líneas por canal:
```m3u
#EXTINF:-1 group-title="Grupo",Nombre del Canal
http://url-del-stream
```
¿Cómo sé si un canal está activo antes de abrirlo?
Para canales AceStream, no hay forma directa de saberlo desde el reproductor sin intentar abrirlo. Para canales HTTP, puedes pegar la URL directamente en VLC o en el navegador para comprobar si responde.
---
⚖️ Aviso legal
> Esta lista es de uso **estrictamente personal**. Los streams referenciados en este archivo pertenecen a terceros. El autor de este repositorio no aloja, retransmite ni distribuye ningún contenido audiovisual protegido por derechos de autor.
> El uso de listas IPTV para acceder a contenido sin la correspondiente licencia puede estar sujeto a restricciones legales según la legislación de cada país. El usuario es el único responsable del uso que haga de esta lista y de verificar que dicho uso es legal en su jurisdicción.
> Este repositorio tiene fines exclusivamente educativos y de documentación técnica del formato M3U y los protocolos de streaming P2P y Xtream Codes.
---
Última actualización de la lista: Abril 2026