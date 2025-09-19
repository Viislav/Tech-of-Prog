Базовое клонирование репозитория с гитхаба себе на устройство: 
 git clone https://github.com/Viislav/Tech-of-Prog && cd https://github.com/Viislav/Tech-of-Prog
Клонирование в «Tech-of-Prog»...
remote: Enumerating objects: 22, done.
remote: Counting objects: 100% (22/22), done.
remote: Compressing objects: 100% (16/16), done.
remote: Total 22 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Получение объектов: 100% (22/22), 4.61 КиБ | 2.30 МиБ/с, готово.
cd: Нет такого файла или каталога: https://github.com/Viislav/Tech-of-Prog
                                                                                                                                                    
┌──(vislav㉿No-V)-[~]
└─$ cd ~/Tech-of-Prog
                                                                                                                                                    
┌──(vislav㉿No-V)-[~/Tech-of-Prog]
└─$ ls -la
итого 16
drwxrwxr-x  4 vislav vislav 4096 сен 19 21:56 .
drwx------ 42 vislav vislav 4096 сен 19 21:56 ..
drwxrwxr-x  7 vislav vislav 4096 сен 19 21:56 .git
drwxrwxr-x  6 vislav vislav 4096 сен 19 21:56 starter_repo

Здесь видно, что все файлы успешно переместились, а так же было установлено окружение(просмотрим для проверки):
 sudo apt install -y git gnupg pre-commit
Уже установлен пакет git самой новой версии (1:2.50.1-0.1).       
Уже установлен пакет gnupg самой новой версии (2.4.8-3).
Уже установлен пакет pre-commit самой новой версии (4.3.0-1).
Сводка:
  Обновление: 0, Установка: 0, Удаление: 0, Пропуск обновления: 0

Мы полностью подготовили наше окружение к дальнейшей работе.
