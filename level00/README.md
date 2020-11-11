Смотрим пользователей, которые у нас есть в образе. ID<1000 системные пользователи

    vim /etc/passwd
    
Находим пользователя flag00 и level00

Посмотрим файлы, которые принадлежат этим юзерам в образе

    find / -user flag00     //какой то файл john????
    
    find / -user level00    //ничего интересного
    
Перенаправим вывод в /dev/null, чтобы не показывать ошибки https://www.cyberciti.biz/faq/how-to-redirect-output-and-errors-to-devnull/

    find / -user flag00 2>/dev/null
    
Получаем:

    /usr/sbin/john
    
    /rofs//usr/sbin/john
    
В обоих лежит строка cdiiddwpgswtgt

Попробуем через шифр Цезаря https://planetcalc.ru/1434/

При ROT11 строка обретает хоть какой-то смысл

    nottoohardhere
