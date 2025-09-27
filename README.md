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
Теперь мы полностью подготовили наше окружение/сервисы к дальнейшей работе.
Далее нам необходимо поднять сервисы: 
	
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
Проверяем работу: 
	
	┌──(vislav㉿No-V)-[~/…/ToP/Tech-Prog/01_dev_environment/starter_repo]
	└─$ docker compose exec app python -m pytest -q
	
	...                                                                                                              [100%]
	3 passed in 0.01s
Всё работает! Темперь начинаются основные действия.

===GIT: КОММИТЫ, ВЕТВЛЕНИЯ И РЕГРЕССИЯ===

Итак, для начала, создадим сам ключ командой:

	┌──(vislav㉿No-V)-[~/Tech-of-Prog/starter_repo]
	└─$ gpg --full-generate-key 
И да, я не раскажу дальнейшее создание ключа и вам не советую хвастаться этим,так как это крайне конфидециальная информация. Единственное скажу: я создал ключ RSA(only sign) с 2048 битами на неограниченный срок.
Далее мы регистрируем его и подписываем:

	┌──(vislav㉿No-V)-[~/Tech-of-Prog/starter_repo]
	└─$ git config --global user.signingkey *****************                                                                                                                                                                                                            
	┌──(vislav㉿No-V)-[~/Tech-of-Prog/starter_repo]
	└─$ git config --global commit.gpgsign true

Всё, с ключом разобрались.

Теперь создадим ветвления. Создаём ветвление:

	┌──(vislav㉿No-V)-[~/Tech-of-Prog/starter_repo]
	└─$ git checkout -b feature/setup                          
	fatal: a branch named 'feature/setup' already exists
Обновляем наш GIT:

	┌──(vislav㉿No-V)-[~/Tech-of-Prog/starter_repo]
	└─$ git fetch origin && git rebase origin/main
	remote: Enumerating objects: 34, done.
	remote: Counting objects: 100% (34/34), done.
	remote: Compressing objects: 100% (33/33), done.
	remote: Total 33 (delta 10), reused 0 (delta 0), pack-reused 0 (from 0)
	Распаковка объектов: 100% (33/33), 12.63 КиБ | 91.00 КиБ/с, готово.
	Из https://github.com/Viislav/Tech-of-Prog
	   dcc247e..220f9a5  main       -> origin/main
	Успешно перемещён и обновлён refs/heads/feature/setup.
И наконецЮ проверяем, что всё сработало корректно:
	
	┌──(vislav㉿No-V)-[~/Tech-of-Prog/starter_repo]
	└─$ git show                                  
	commit 220f9a5d50f6a33898338510372182348f9167ad (HEAD -> feature/setup, origin/main, origin/HEAD)
	Author: Vlad <165074922+Viislav@users.noreply.github.com>
	Date:   Sat Sep 27 11:14:25 2025 +0600
Всё, ветвление создано и оно работает. Идём дальше.







