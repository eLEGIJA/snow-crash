Смотрим пользователей, которые у нас есть в образе. ID<1000 системные пользователи

    vim /etc/passwd
    
Находим пользователей flag01 и level01

    level01:x:2001:2001::/home/user/level01:/bin/bash               //ничего интересного

    flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash     //есть хэш пароля

Попробуем сломать хэш пароля через John the Ripper (https://download.openwall.net/pub/projects/john/contrib/macosx/)

    https://habr.com/ru/post/325298/

На маке заходим в папку с John the Ripper, в папку run, создаем файл с паролем и ломаем

    echo '42hDRfypTqqnw' > pass

    ./john pass

    ./john pass --show

    ?:abcdefg       //пароль будет без символов ?:

Проверим:

    su flag01
 
 Вводим abcdefg
 
    getflag
    
Получаем заветный флаг

    f2av5il02puano7naaf6adaaf