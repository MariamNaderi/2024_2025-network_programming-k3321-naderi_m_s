University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://itmo-ict-faculty/network-programming)

Year: 2024/2025

Group: K3321

Author: Naderi Mariam Shakhovna

Lab: Lab2

Date of create: 15.05.2025

Date of finished: 06.06.2025

# Лабораторная работ №2 "Развертывание дополнительного CHR, первый сценарий AnsibleN"

`Цель работы:`
С помощью Ansible настроить несколько сетевых устройств и собрать информацию о них. Правильно собрать файл Inventory.

## Ход работы

### Схема

<img src="./pic/topology.jpg" style="width:400px;">

### Настройка второго VPN-тунеля

Как в первой лабе был настроен второй клиент с помощью wireguard. На картинках видно, что пинг до сервера идет. 

<img src="./pic/pic5.PNG" style="width:700px;">

<img src="./pic/pic6.PNG" style="width:700px;">


### Настройка с помощью Ansible

Был прописан инвентарь hosts.ini:

<img src="./pic/pic3.PNG" style="width:700px;">

После все команды были прописаны в ямле (conf.yml, там нет экспорта это в другом файле):

<img src="./pic/pic4.PNG" style="width:700px;">

Проверяем, что есть связь с хостами:

<img src="./pic/pic1.PNG" style="width:700px;">

Запускаем:

<img src="./pic/pic2.PNG" style="width:700px;">

Проверяем работу ospf, ниже видно, что хосты видят соседа и проходит пинг:

<img src="./pic/pic7.PNG" style="width:700px;">

<img src="./pic/pic8.PNG" style="width:700px;">

С помощью еще одного ямла был сделан экспорт (данные экспорта есть в папке лабы):

<img src="./pic/pic9.PNG" style="width:550px;">

Ошибок нет:

<img src="./pic/pic10.PNG" style="width:700px;">

