---
# Front matter
title: "Лаб.1 Установка и конфигурация
операционной системы на виртуальную машину"
author: "Поляков Иван Андреевич"

# Generic otions
lang: ru-RU
toc-title: "Содержание"

# Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

# Pdf output format
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
  - \usepackage[T2A]{fontenc}
---

# Цель работы

Целью данной работы является приобретение практических навыков
установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Последовательность выполнения работы
Загрузите в дисплейном классе операционную систему Linux. Осуществите
вход в систему. Запустите терминал. Перейдите в каталог /var/tmp:

cd /var/tmp

Создайте каталог с именем пользователя (совпадающий с логином студента в дисплейном классе). Для этого можно использовать команду:

mkdir /var/tmp/Cid -unC

или непосредственно:

mkdir /var/tmp/имя_пользователя

Здесь вместо имя_пользователя должен быть указан ваш логин (учётная
запись) в дисплейном классе.

Запустите виртуальную машину, введя в командной строке:

VirtualBox &

Проверьте в свойствах VirtualBox месторасположение каталога
для виртуальных машин. Для этого в VirtualBox выберите Файл
Настройки , вкладка Общие . В поле Папка для машин (рис. 1.1) должно стоять
/var/tmp/имя_пользователя. Здесь имя_пользователя — логин (учётная запись) студента в дисплейном классе. Если указан другой каталог, то
требуется изменить его, как указано выше.

![Рис. 1.1. Окно «Свойства» VirtualBox](img1/1.png){ #fig:001 width=100% }

Создайте новую виртуальную машину. Для этого в VirtualBox выберите
Машина Создать .

Укажите имя виртуальной машины (ваш логин в дисплейном классе), тип
операционной системы — Linux, RedHat (рис. 1.2).

![Рис. 1.2. Окно «Имя машины и тип ОС»](img1/2.png){ #fig:002 width=100% }

Укажите размер основной памяти виртуальной машины (рис. 1.3) — 2048
МБ (или большее число, кратное 1024 МБ, если позволяют технические характеристики вашего компьютера).
Задайте конфигурацию жёсткого диска — загрузочный,VDI (BirtualBox Disk
Image), динамический виртуальный диск (рис. 1.4–1.6).

![Рис. 1.3. Окно «Размер основной памяти»](img1/3.png){ #fig:003 width=100% }

![Рис. 1.4. Окно подключения или создания жёсткого диска на виртуальной
машине](img1/4.png){ #fig:004 width=100% }

![Рис. 1.5. Окно определения типа подключения виртуального жёсткого диска
](img1/5.png){ #fig:005 width=100% }

![Рис. 1.6. Окно определения формата виртуального жёсткого диска](img1/6.png){ #fig:006 width=100% }

Задайте размер диска — 40 ГБ (или больше), его расположение — в данном
случае /var/tmp/имя_пользователя/имя_пользователя.vdi (рис. 1.7).

![Рис. 1.7. Окно определения размера виртуального динамического жёсткого
диска и его расположения](img1/7.png){ #fig:007 width=100% }

Выберите в VirtualBox для Вашей виртуальной машины Настройки
Носители . Добавьте новый привод оптических дисков и выберите образ
операционной системы, например для работающих в дисплейных классах
/afs/dk.sci.pfu.edu.ru/common/files/iso/Rocky-8.6-x86_64-dvd1.iso
(рис. 1.8).

![Рис. 1.8. Окно «Носители» виртуальной машины: подключение
образа оптического диска](img1/8.png){ #fig:008 width=100% }

Запустите виртуальную машину (рис. 1.9), выберите English в качестве языка интерфейса (рис. 1.10) и перейдите к настройкам установки операционной
системы (рис. 1.11).

![Рис. 1.9. Запуск виртуальной машины](img1/9.png){ #fig:009 width=100% }

![Рис. 1.10. Установка английского языка интерфейса ОС](img1/10.png){ #fig:010 width=100% }

![Рис. 1.11. Окно настройки установки образа ОС](img1/11.png){ #fig:011 width=100% }

При необходимости скорректируйте часовой пояс, раскладку клавиатуры
(рекомендуется добавить русский язык, но в качестве языка по умолчанию
указать английский язык; задать комбинацию клавиш для переключения
между раскладками клавиатуры — например Alt + Shift ).

В разделе выбора программ укажите в качестве базового окружения
Server with GUI , а в качестве дополнения — Development Tools (рис. 1.12)

![Рис. 1.12. Окно настройки установки: выбор програм](img1/12.png){ #fig:012 width=100% }

Отключите KDUMP (рис. 1.13).

![Рис. 1.13. Окно настройки установки: отключение KDUMP](img1/13.png){ #fig:013 width=100% }

Место установки ОС оставьте без изменения (рис. 1.14).

![Рис. 1.14. Окно настройки установки: место установки](img1/14.png){ #fig:014 width=100% }

Включите сетевое соединение и в качестве имени узла укажите
user.localdomain (рис. 1.15), где вместо user укажите имя своего пользователя в соответствии с соглашением об именовании.

![Рис. 1.15. Окно настройки установки: сеть и имя узла](img1/15.png){ #fig:015 width=100% }

Установите пароль для root и пользователя с правами администратора
(рис. 1.16–1.17).

![Рис. 1.16. Установка пароля для root](img1/16.png){ #fig:016 width=100% }

![Рис. 1.17. Установка пароля для пользователя с правами администратора](img1/17.png){ #fig:017 width=100% }

После завершения установки операционной системы корректно перезапустите виртуальную машину (рис. 1.18) и примите условия лицензии
(рис. 1.19–1.20).

![Рис. 1.18. Завершение установки ОС](img1/18.png){ #fig:018 width=100% }

![Рис. 1.19. Первоначальная настройка ОС: переход к лицензии](img1/19.png){ #fig:019 width=100% }

![Рис. 1.20. Первоначальная настройка ОС: лицензия](img1/20.png){ #fig:020 width=100% }

В VirtualBox оптический диск должен отключиться автоматически, но если
это не произошло, то необходимо отключить носитель информации с образом, выбрав Свойства Носители Rocky-версия-dvd1.iso Удалить устройство .

Войдите в ОС под заданной вами при установке учётной записью. В меню
Устройства виртуальной машины подключите образ диска дополнений гостевой ОС (рис. 1.21, 1.22), при необходимости введите пароль пользователя
root вашей виртуальной ОС.

![Рис. 1.18. Завершение установки ОС](img1/18.png){ #fig:018 width=100% }

![Рис. 1.19. Первоначальная настройка ОС: переход к лицензии](img1/19.png){ #fig:019 width=100% }

После загрузки дополнений нажмите Return или Enter и корректно перезагрузите виртуальную машину.


# Выводы

Приобрел практические навыки
установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.
