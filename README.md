# Скачивание образа PostgreSQ
docker pull postgres
# запустить контейнер PostgreSQL, пробросив Volume для сохранения данных
docker run --name pg -d -v /home/vasa/data:/data/pg  -e POSTGRES_PASSWORD=password  postgres:latest
# Удалите контейнер, не трогая ранее созданный Volume
docker rm -f pg
# Проверьте, что данные не потеряны
ls  -la /home/vasa/data
# Переместите содержимое папки в другую директорию
mv /home/vasa/data/. /home/vasa/v2/data
# Запустите новый контейнер PostgreSQL, указав новый путь к данным
docker run --name pg -d -v /home/vasa/v2/data:/data/pg  -e POSTGRES_PASSWORD=password  postgres:latest 
