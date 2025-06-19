University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Introduction in routing](https://itmo-ict-faculty/network-programming)

Year: 2024/2025

Group: K3321

Author: Naderi Mariam Shakhovna

Lab: Lab4

Date of create: 15.06.2025

Date of finished: 18.06.2025

# Лабораторная работ №4 "Базовая 'коммутация' и туннелирование используя язык программирования P4"

`Цель работы:`
Изучить синтаксис языка программирования P4 и выполнить 2 задания обучающих задания от Open network foundation для ознакомления на практике с P4.

## Ход работы

### 1. Развернуть Vagrant

В начале были установлены VB и vagrant. После был склонирован репозиторий p4lang/tutorials. 

Как итог, развернутый vagrant.

<img src="./pic/pic1.PNG" style="width:700px;">

### 2. Implementing Basic Forwarding 

Схема:

<img src="./pic/topology1.PNG" style="width:600px;">

По заданию был исправлен файл [basic.p4](https://github.com/MariamNaderi/2024_2025-network_programming-k3321-naderi_m_s/blob/main/lab4/basic.p4).

В файле было реализовано извлечение заголовков Ethernet и IPv4:

<img src="./pic/pic3.PNG" style="width:500px;">

Также было реализовано действие ipv4_forward (установка egress_spec, обновление MAC-адресов (src/dst), уменьшение TTL):

<img src="./pic/pic4.PNG" style="width:500px;">

Еще были добавлены IPv4- и Ethernet-заголовоки в пакет.

<img src="./pic/pic5.PNG" style="width:500px;">

Проверяем работу:

<img src="./pic/pic2.PNG" style="width:500px;">

### 3. Implementing Basic Tunneling  

Схема:

<img src="./pic/topology2.png" style="width:600px;">

По заданию был исправлен файл [basic_tunnel.p4](https://github.com/MariamNaderi/2024_2025-network_programming-k3321-naderi_m_s/blob/main/lab4/basic_tunnel.p4).

Было добавлено новое состояние parse_myTunnel для обработrb пакетов из тунеля, теперь парсится и MyTunnel.

<img src="./pic/pic10.jpg" style="width:400px;">

Далее было добавлено новое действие myTunnel_forward и новая таблица myTunnel_exact. Плюс обновление логики в apply.

<img src="./pic/pic11.jpg" style="width:400px;">

И в конце депарсинг, теперь добавляется заголовок тунеля.

<img src="./pic/pic12.jpg" style="width:400px;">

Можно увидеть, что после запускаются h1 и h2.

<img src="./pic/pic6.jpg" style="width:700px;">

Далее был запущен сервер на хосте 2, а с первого было отправлено сообщение без тунеля, все прошло успешно:

<img src="./pic/pic7.jpg" style="width:700px;">

Тут видно, что 3 хост тоже работает.

<img src="./pic/pic8.jpg" style="width:700px;">

Теперь тест с тунелем, видно, что появилась шапка тунеля.

<img src="./pic/pic9.jpg" style="width:700px;">









