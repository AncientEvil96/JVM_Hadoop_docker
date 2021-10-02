# JVM_Hadoop

Находясь в той же директории, где расположен Dockerfile:
docker build -t img-hdp-hadoop .
Поднимаем новый контейнер из образа:
docker run -it --name gbhdp \
-p 50090:50090 \
-p 50075:50075 \
-p 50070:50070 \
-p 8042:8042 \
-p 8088:8088 \
-p 8888:8888 \
-p 4040:4040 \
-p 4044:4044 \
--hostname localhost \
img-hdp-hadoop
СБОРКА ОБРАЗА
1. Скачаем датасет ppkm_sentiment, размеченный эмоциональной окраской отзывов
индонезийской компании PPKM
2. Поместим его в контейнер:
# docker cp archive.zip gbhdp:/home/hduser
3. Распакуем:
$ unzip archive.zip -d ppkm
$ rm archive.zip
4. Копируем директорию в hdfs:
$ hdfs dfs -put ppkm /user/hduser/
5. Проверим, что файлы в hdfs:
$ hdfs dfs -ls /user/hduser/ppkm
