Cначала настроим ssh на виртуалке

Devices->Network->Network Settings...->Advanced->Port Forwarding-> 127.0.0.1(или другой), 4242, 10.0.2.15, 4242,

    ssh level02@127.0.0.1 -p 4242

Вводим пароль

    ls -la

Видим какой то файл level02.pcap   https://www.reviversoft.com/ru/file-extensions/pcap

Судя по всему это пакетные данные. Файл хранит дамп сетевых данных, захваченных в режиме реального времени

https://habr.com/ru/company/ruvds/blog/416537/

Выходим отсюда

Скопируем к себе на компутер

    scp -P 4242 level02@127.0.0.1:~/level02.pcap .

Посмотрим что в файле через Wireshark

    chmod 777 level02.pcap

Открываем в Wireshark 

Многа букафф непанятна................................

Судя по запросам, длина у которых больше 100, кто то пытался залогиниться через tcp в ssh, причем в пользователя levelX

Посмотрим что там в Analyze->Follow->TCP Stream    https://networkguru.ru/analiz-dampov-tcp-s-pomoshchyu-wireshark/

    ..%..%..&..... ..#..'..$..&..... ..#..'..$.. .....#.....'........... .38400,38400....#.SodaCan:0....'..DISPLAY.SodaCan:0......xterm.........."........!........"..".....b........b....	B.
    ..............................1.......!.."......"......!..........."........"..".............	..
    .....................
    Linux 2.6.38-8-generic-pae (::ffff:10.1.1.2) (pts/10)

    ..wwwbugs login: l.le.ev.ve.el.lX.X
    ..
    Password: ft_wandr...NDRel.L0L
    .
    ..
    Login incorrect
    wwwbugs login:

. = 0x7f = DEL (смотрим какие пакеты отвечают за . на конце у них у всех 7f = 16 ричное представление DEL), так что пароль у нас будет ft_waNDReL0L

    su flag02

 Вводим ft_waNDReL0L
 
    getflag
    
Получаем заветный флаг

    kooda2puivaav1idi4f57q8iq