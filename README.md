## Ответ на задания ##

- (на 4 балла):
\*
в logs.txt логи добавления единицы (curl -fsS -X POST http://127.0.0.1:8080/increment несколько раз)
\*

- (на 6 баллов): 
\*
toadandahalf@l-surveillance-device:~/projects/idol/app$ curl -fsS -X POST http://127.0.0.1:8080/increment
{"greeting": "Hello, Docker!", "count": 6, "hostname": "5d4248c853e7", "storage": "sqlite"}toadandahalf@l-surveillance-device:~/projects/idol/app$ sudo docker compose down
[+] down 2/2
 ✔ Container app-app-app-1 Removed                                                                           10.2s
 ✔ Network app_default     Removed                                                                            0.1s
toadandahalf@l-surveillance-device:~/projects/idol/app$ sudo docker compose up -d
[+] up 2/2
 ✔ Network app_default     Created                                                                            0.0s
 ✔ Container app-app-app-1 Started                                                                            0.1s
toadandahalf@l-surveillance-device:~/projects/idol/app$ curl -fsS -X POST http://127.0.0.1:8080/increment
{"greeting": "Hello, Docker!", "count": 7, "hostname": "6516a5150be1", "storage": "sqlite"}toadandahalf@l-surveillance-device:~/projects/idol/app$ 
\*
- (настройки compose.yaml):
\*
services:
  app-app:
    build: .
    ports:
      - 8080:${PORT}
    environment:
      GREETING: ${GREETING}
      STORAGE: ${STORAGE}
      PORT: ${PORT}
      DATA_FILE: ${DATA_FILE}
    volumes:
      - sqlite_data:/data
volumes:
  sqlite_data:
\*
