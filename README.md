# final_project_5_taxi
Итоговый проект №5, курс Data Engineer 
Клиенты и счета (Такси)
**Цель проекта**: на основе данных поездок такси в городе Нью-Йорк построить таблицу-отчет(далее – parquet) с информормацией каждого дня, в которую входят:
 * процент поездок по количеству человек в машине (5 групп пассажиров)
 * Самая дорогая поездка для каждой группы пассажиров
 * Самая дешевая поездка для каждой группы пассажиров

**Дополнительно**: Провести аналитику и построить график на тему "как пройденное расстояние и количество пассажиров влияет на размер чаевых"

**Стек проекта**
 * Git
 * Scala v. 2.11.12
 * Spark v. 2.4.0
 * Docker
 * Образ JupyterLab со Spark: JupyterLab v 2.1.4 - Spark v 2.4.0 ( GitHab URL – https://github.com/cluster-apps-on-docker/spark-standalone-cluster-on-docker )
 * Draw.io
 * PowerPoint – для выполнения презентации

**Структура проекта** <br>
final_project_5_taxi<br>
&emsp;-notebooks <br>
&emsp;&emsp;-Taxi_analysis.ipynb <br>
&emsp;-results <br>
&emsp;&emsp;-graph 1.png <br>
&emsp;&emsp;-graph 2.png <br>
&emsp;&emsp;-graph 3.png <br>
&emsp;&emsp;-parquet.csv <br>
&emsp;&emsp;-result.parquet <br>
&emsp;-scala <br>
&emsp;&emsp;-Project_5.scala <br>
&emsp;-LICENCE <br>
&emsp;-README.md <br>
&emsp;-project_taxi.pdf <br>
&emsp;-project-schema.svg <br>
&emsp; docker-compose.yml <br>


**Комментарий по структуре проекта**
1) В папке notebooks находятся ноутбуки выполнения задач проекта:
 * Taxi_analysis.ipynb - задание по аналитике данных
2) В папке results находится parquet в формате "csv" и "parquet"
3) В папке scala находится код, написанный на Scala, для получения parquet и сохранения результата в папку results/
4) LICENCE - лицензия, используемая в git репозитории проекта
5) README.md - детальное описание проекта
6) project_taxi.pdf - презентация в "pdf" формате
7) project-schema.svg - схема проекта
8) docker-compose.yml - Docker Compose используется для одновременного управления несколькими контейнерами, входящими в состав приложения

**Руководство по использованию проекта**
 * Данные поездок Taxi могут быть скачаны по ссылке: https://disk.yandex.ru/d/DKeoopbGH1Ttuw
 * Файлы формата "ipynb" могут быть открыты в JupyterNotebook или Google Colab (также дополнительно приложена ссылка на образ докера, в котором уже есть JupyterLab и Spark и имеются нужные настройки).
 *   1) Запустите кластер командой " docker-compose up ", файл docker-compos прикреплён в структуре проекта проекта
![image](https://github.com/Akua-D/final_project_5_taxi/assets/144109716/bf4aef45-6c61-44d2-8f9e-dbd88b19b2b2)
 *   2) Запустите код с помощью предоставленной тетрадки Jupyter
![image](https://github.com/Akua-D/final_project_5_taxi/assets/144109716/cc607f37-54e7-4d20-86b8-81c248b97f00)
![image](https://github.com/Akua-D/final_project_5_taxi/assets/144109716/60aed37d-2dff-4dd2-8ab5-dc0c451d632c)
![image](https://github.com/Akua-D/final_project_5_taxi/assets/144109716/b1038baf-7d11-43be-ad08-244d0d31ec1b)
 * Остановит кластер можно набрав на терминале "ctrl+c"
 * Командой из шага 1 можно перезапустить кластер
 * Файлы формата "scala" могут быть добавлены в проект в IntelliJ IDEA. Тогда дополнительно надо добавить следующие зависимости в структуру проекта: <br>
&emsp;scalaVersion := "2.11.12" <br>
&emsp;sparkVersion = "2.4.0" <br>
&emsp;libraryDependencies ++= Seq( <br>
&emsp;&emsp;"org.apache.spark" %% "spark-core" % sparkVersion, <br>
&emsp;&emsp;"org.apache.spark" %% "spark-sql" % sparkVersion)

**Аналитика: Графики** <br>
*График 1: Зависимость размера чаевых от кол-ва пассажиров*
![graph 1](https://user-images.githubusercontent.com/62721453/209213440-4d94b18c-4d91-4e5f-9ebe-0d7d4fabd94f.png)

*График 2: Зависимость размера чаевых от кол-ва пассажиров*
![graph 3](https://user-images.githubusercontent.com/62721453/209213497-67d0028e-a5ea-461e-963f-31933fb9397e.png)

**Выводы:** <br>
*Из графика 1 зависимости размера чаевых от кол-ва пассажиров следует, что:*

 * Самые большие чаевые давала первая группа пассажиров (1 человек)
 * Чаще всего чаевые давала первая группа пассажиров, реже всего 3 группа и 4 группа (4 пассажира)
 * На основании полученных данных первая и вторая группа пассажиров лидирующие по числу чаевых

*Из графика 2 зависимости размера чаевых от пройденного расстояния следует, что:*
 * Не учитывая выброс (чаевые ~ 255 при расстоянии 0), наибольшие чаевые получали при расстоянии 16-19 миль
 * Минимальные чаевые при расстоянии 2-4 мили
 * На основании полученных графиков можно сделать вывод, что заказы на усреднённое расстояние 7-10 миль и 15-20 миль приносят лучшую прибыль
