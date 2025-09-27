===ПРЕДУСТАНОВКА НЕОБХОДИМЫХ УТИЛИТ===
Установим необходимые утилиты для дальнейшей работы:

	┌──(vislav㉿No-V)-[~/Univer/ToP/Tech-Prog/01_dev_environment]
	└─$ sudo apt install -y git gnupg pre-commit
	
	[sudo] пароль для vislav: 
	Уже установлен пакет git самой новой версии (1:2.51.0-1).         
	Уже установлен пакет gnupg самой новой версии (2.4.8-3).
	Установка:
	  pre-commit
	
	Установка зависимостей:
	  nodeenv  python3-cfgv  python3-distlib  python3-identify  python3-virtualenv
	
	Сводка:
	  Обновление: 0, Установка: 6, Удаление: 0, Пропуск обновления: 0
	  Объём загрузки: 642 kB
	  Требуемое пространство: 2 585 kB / 384 GB доступно
	...........................................................................................
В конце все пакеты настраиваются и обрабатываются. Можем переходить к следующему этапу.

===НАЧАЛО РАБОТЫ И ПОДНЯТИЕ СЕРВИСОВ===

Базовое клонирование необходимого репозитория с гитхаба себе на устройство: 

	git clone https://github.com/Viislav/Tech-of-Prog && cd https://github.com/Viislav/Tech-of-Prog
		Клонирование в «Tech-of-Prog»...
		remote: Enumerating objects: 22, done.
		remote: Counting objects: 100% (22/22), done.
		remote: Compressing objects: 100% (16/16), done.
		remote: Total 22 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
		Получение объектов: 100% (22/22), 4.61 КиБ | 2.30 МиБ/с, готово.
                                                                                                                                          
	┌──(vislav㉿No-V)-[~]

	└─$ cd ~/Tech-of-Prog
                                                                                                                                              
	┌──(vislav㉿No-V)-[~/Tech-of-Prog]
	
	└─$ ls -la
		итого 16
		drwxrwxr-x  4 vislav vislav 4096 сен 19 21:56 .
		drwx------ 42 vislav vislav 4096 сен 19 21:56 ..
		drwxrwxr-x  7 vislav vislav 4096 сен 19 21:56 .git
		drwxrwxr-x  6 vislav vislav 4096 сен 19 21:56 starter_repo

Здесь видно, что все файлы успешно переместились.
Теперь необходимо утстановить среду Docker Engine. У меня она установлена заранее, но проверить стоит.

	sudo apt install -y git gnupg pre-commit

		Уже установлен пакет git самой новой версии (1:2.50.1-0.1).       
		
		Уже установлен пакет gnupg самой новой версии (2.4.8-3).
		
		Уже установлен пакет pre-commit самой новой версии (4.3.0-1).

		Сводка:
		  
		  Обновление: 0, Установка: 0, Удаление: 0, Пропуск обновления: 0
Мы полностью подготовили наше окружение к дальнейшей работе.
Далее нам необходимо поднять сервисы, чтобы они именно работали: 
	
 	┌──(vislav㉿No-V)-[~/Tech-of-Prog]
	└─$ cd ~/Tech-of-Prog/starter_repo 
	                                                                                                                                                    
	┌──(vislav㉿No-V)-[~/Tech-of-Prog/starter_repo]
	└─$ docker-compose up -d --build     
		[+] Running 5/5
		 ✔ app Pulled                                                                                                                                 15.2s 
		   ✔ ce1261c6d567 Already exists                                                                                                               0.0s 
		   ✔ 11b89692b208 Pull complete                                                                                                                3.5s 
		   ✔ 764e05fe66b6 Pull complete                                                                                                               11.8s 
		   ✔ a4aefcec16c5 Pull complete                                                                                                               11.8s 
		[+] Running 2/2
		 ✔ Network starter_repo_default  Created                                                                                                       0.0s 
		 ✔ Container starter_repo-app-1  Started  
Всё, мы полностью готовы к работе!

===GIT:КОММИТЫ, ВЕТВЛЕНИЯ И РЕГРЕССИЯ===
