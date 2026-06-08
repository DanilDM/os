## 1 Запуск контейнера
```bash
dan ~ $ sudo docker run -d \
  --name my-http-server \
  -p 8080:8080 \
  python:3.12-slim \
  python -m http.server 8080
Unable to find image 'python:3.12-slim' locally
3.12-slim: Pulling from library/python
07342fe545e6: Pull complete 
e113665b194b: Pull complete 
4a9dde5cdde1: Pull complete 
5b4d6ff92fc4: Pull complete 
e182f7d16de2: Download complete 
3f0547a81222: Download complete 
Digest: sha256:090ba77e2958f6af52a5341f788b50b032dd4ca28377d2893dcf1ecbdfdfe203
Status: Downloaded newer image for python:3.12-slim
b5ba8a0dd4de179f2a50f6fbc71ca8b28f87b88fa463de73684a47c840159753
dan ~ $ sudo docker ps
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS                                         NAMES
b5ba8a0dd4de   python:3.12-slim   "python -m http.serv…"   30 seconds ago   Up 29 seconds   0.0.0.0:8080->8080/tcp, [::]:8080->8080/tcp   my-http-server
dan ~ $ curl http://localhost:8080
<!DOCTYPE HTML>
<html lang="en">
<head>
<meta charset="utf-8">
...
```

## 2 Аналіз процесу
```bash
dan ~ $ sudo docker exec -it my-http-server sh
# cat /proc/1/cmdline
python-mhttp.server8080
```
У контейнері процес, який запускається командою CMD, ENTRYPOINT або командою після назви образу в docker run, стає головним процесом контейнера.

## 3 Завершення контейнера
```bash
dan ~ $ sudo docker stop my-http-server
my-http-server
```
- Docker надсилає SIGTERM.
- Чекає приблизно 10 секунд.
- Якщо процес не завершився — надсилає SIGKILL.

## 4 Перегляд логів
```bash
dan ~ $ sudo docker logs my-http-server
172.17.0.1 - - [08/Jun/2026 12:22:47] "GET / HTTP/1.1" 200 -
```
Docker збирає все, що процес PID 1 записує у stdout та stderr. У нашому випадку Python HTTP-сервер друкує повідомлення про HTTP-запити у stdout.
