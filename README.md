# Домашнее задание к занятию «Репликация и масштабирование. Часть 2» - Алексей Головин SYS-23

### Инструкция по выполнению домашнего задания

1. Сделайте fork [репозитория c шаблоном решения](https://github.com/netology-code/sys-pattern-homework) к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).
2. Выполните клонирование этого репозитория к себе на ПК с помощью команды `git clone`.
3. Выполните домашнее задание и заполните у себя локально этот файл README.md:
   - впишите вверху название занятия и ваши фамилию и имя;
   - в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;
   - для корректного добавления скриншотов воспользуйтесь инструкцией [«Как вставить скриншот в шаблон с решением»](https://github.com/netology-code/sys-pattern-homework/blob/main/screen-instruction.md);
   - при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в [инструкции по MarkDown](https://github.com/netology-code/sys-pattern-homework/blob/main/md-instruction.md).
4. После завершения работы над домашним заданием сделайте коммит (`git commit -m "comment"`) и отправьте его на Github (`git push origin`).
5. Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
6. Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.

---

### Задание 1

Опишите основные преимущества использования масштабирования методами:

- активный master-сервер и пассивный репликационный slave-сервер; 
- master-сервер и несколько slave-серверов;
- активный сервер со специальным механизмом репликации — distributed replicated block device (DRBD);
- SAN-кластер.

*Дайте ответ в свободной форме.*

### Ответ на задание 1

**Активный Master-сервер и пассивный репликационный Slave-сервер** - этот метод масштабирования самый надежный, он реализуется путём добавления дополнительного сервера, который копирует все данные с Master-сервера. В случае падения Master-сервера можно будет поднять копию с Slave-сервера и создать новый Master.

**Master-сервер и несколько Slave-серверов** - создание нескольких дополнительных Slave‑серверов позволяет снять с основного сервера нагрузку и повысить общую производительность системы, таким способом можно, к примеру, производительные процессы поделить на эти Slave-сервера (отчеты аналитиков), но на работе других пользователей это никак не скажется.

**Активный сервер со специальным механизмом репликации Distributed Replicated Block Device (DRBD)** - распределённое реплицируемое блочное устройство представляет собой распределенное, гибкое и универсально реплицируемое решение хранения данных, преимущество в этом случае в увеличении отказоустойчивости.

**SAN-кластер** - высокая надёжность, более высокая производительность всей системы, быстродействие и масштабируемость, вариант больше подходит для облачного хранения данных.

---

### Задание 2


Разработайте план для выполнения горизонтального и вертикального шаринга базы данных. База данных состоит из трёх таблиц: 

- пользователи, 
- книги, 
- магазины (столбцы произвольно). 

Опишите принципы построения системы и их разграничение или разбивку между базами данных.

*Пришлите блоксхему, где и что будет располагаться. Опишите, в каких режимах будут работать сервера.* 

### Ответ на задание 2

![](https://github.com/alexei-golovin/SYS-23-12-07/blob/main/201.jpg)

Вертикальный шардинг - каждая таблица находится на отдельном сервере баз данных.		

Горизонтальный шардинг - так же каждая таблица находится на отдельном сервере баз данных, но таблица пользователей и книг разделена на две и каждая на отдельном сервере.

Книги поделены на таблицы по названиям от А до О и на от П до Я. Пользователи поделены на таблицы пользователи личные данные и на аккаунты.

---

## Дополнительные задания (со звёздочкой*)
Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

---
### Задание 3*

Выполните настройку выбранных методов шардинга из задания 2.

*Пришлите конфиг Docker и SQL скрипт с командами для базы данных*.
