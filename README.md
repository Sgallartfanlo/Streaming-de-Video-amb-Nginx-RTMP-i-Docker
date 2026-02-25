# 📡 Servidor de Streaming Adaptatiu (Nginx-RTMP + HLS)

Aquest projecte implementa un servidor de streaming de vídeo utilitzant **Docker**, **Nginx-RTMP** i **FFmpeg** per realitzar transcodificació en temps real. Permet rebre un senyal RTMP i distribuir-lo mitjançant el protocol HLS amb múltiples qualitats (Streaming Adaptatiu).

## 🚀 Característiques
* **Entrada:** Protocol RTMP (ideal per a OBS Studio o FFmpeg).
* **Transcoding:** Generació de variants a 1080p, 720p i 480p en temps real.
* **Sortida:** Protocol HLS (HTTP Live Streaming) compatible amb navegadors web.
* **Reproductor Web:** Inclou una interfície amb Video.js i selector de qualitat manual.

## 🛠️ Requisits previs
* **Docker** i **Docker Compose** instal·lats[cite: 13].
* **OBS Studio** (per a l'emissió)[cite: 15].

## 📂 Estructura del projecte
```text
streaming-video-sergigallart/
├── config/
│   └── nginx.conf      # Configuració del servidor Nginx i FFmpeg
├── html/
│   └── index.html      # Reproductor web personalitzat
├── hls/                # Carpetes per als segments .ts i .m3u8 (auto-generat)
└── docker-compose.yml  # Definició del contenidor

```
## ⚙️ Desplegament del servidor

1. **Clonar el repositori:**
```bash
git clone [https://github.com/Sgallartfanlo/Streaming-de-V-deo-amb-Nginx-RTMP-i-Docker.git](https://github.com/Sgallartfanlo/Streaming-de-V-deo-amb-Nginx-RTMP-i-Docker.git)
cd Streaming-de-V-deo-amb-Nginx-RTMP-i-Docker

```


2. **Aixecar el contenidor:**
```bash
docker-compose up -d

```



*Això activarà el servidor RTMP al port 1935 i el servidor web al port 8080*.



## 📽️ Com emetre (OBS Studio)

1. Ves a **Configuració > Emissió** a OBS.


2. Tria **Servei: Personalitzat**.


3. Introdueix les dades:
*   **Servidor:** `rtmp://localhost:1935/live` 


*   **Clau d'emissió:** `sergigallart` (o la teva clau personalitzada) 


4. Fes clic a **Iniciar emissió**.


## 📺 Visualització

* **Navegador Web:** Obre `http://localhost:8080` per veure el reproductor amb selector de qualitat.


* **VLC Media Player:** Obre el flux de xarxa `http://localhost:8080/hls/sergigallart.m3u8`.


* **Estadístiques:** Consulta l'estat del servidor a `http://localhost:8080/stat`.



## ⚠️ Notes sobre el Transcoding

S'utilitza el preset de FFmpeg **`superfast`** per optimitzar l'ús de la CPU durant la codificació simultània de les tres qualitats.

Projecte realitzat per **Sergi Gallart** per a l'assignatura de Serveis de Xarxa i Internet.

