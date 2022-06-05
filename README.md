# LAB4_HTB_HACK

# ТАЧКА
<img width="1220" alt="Снимок экрана 2022-06-04 в 12 52 53" src="https://user-images.githubusercontent.com/63841835/171976635-1ef71ab4-e9dd-469c-9c98-072a1dceb258.png">  
Заходим на сайт  
<img width="1039" alt="Снимок экрана 2022-06-04 в 12 58 58" src="https://user-images.githubusercontent.com/63841835/171977058-2f83f6a1-7cbe-45a9-851f-83a59fe2c0de.png">  
Сканируем nmap-ом открытые порты  
<img width="797" alt="Снимок экрана 2022-06-04 в 12 54 19" src="https://user-images.githubusercontent.com/63841835/171976673-23b9114f-5a9f-4a0b-b709-adfb85bba37d.png">
Нашли 2 открытых порта  
Сканируем udp порты  
<img width="674" alt="Снимок экрана 2022-06-04 в 13 00 29" src="https://user-images.githubusercontent.com/63841835/171977115-26d22f59-1970-472f-89f9-32f68b974155.png"> Нашли 161 port  
Отсканировали порт 161
<img width="562" alt="Снимок экрана 2022-06-04 в 13 38 18" src="https://user-images.githubusercontent.com/63841835/171980491-25f4362e-be3e-4c37-a332-952bccba7cc6.png"> 

Пробуем найти пароль от машины по ключевому слову "public", которое нашли ранее  
![image](https://user-images.githubusercontent.com/62139377/172030424-074ca3ae-a82b-44a8-93f9-459a05b0eba6.png)  
Нашли данные, похожие на логин и пароль  
![image](https://user-images.githubusercontent.com/62139377/172030426-62191bd4-6d3c-425b-9b36-245e63b1aba0.png)  
Проверяем найденные данные, пытаясь подключиться по ssh  
![image](https://user-images.githubusercontent.com/62139377/172030473-f7fabfdb-e3aa-409f-91b3-7d88cda6b040.png)  
Получилось зайти в машину и посмотрели ID
![image](https://user-images.githubusercontent.com/62139377/172030509-3dbf8ecb-98cd-4c01-88c2-5289db7f1605.png)  
Не получилось добыть флаг, отказали в доступе  
![image](https://user-images.githubusercontent.com/62139377/172030576-4dd77e28-cf66-498b-a242-64cd9be2a7b3.png)  
Так как Даниэлю отказано в доступе к флагу, решили попытаться зайти под Мэттом. Смотрим хосты 
![image](https://user-images.githubusercontent.com/62139377/172030629-879feb37-5a4a-49fb-ac0a-f02bbd8940f8.png)  
Увидели, что скорее всего, у пандоры есть локальный сервер. Пробуем пробросить порты, чтобы попытаться подключиться к веб-серверу  
![image](https://user-images.githubusercontent.com/62139377/172030731-a2d372e1-a675-4046-bba2-fea0c6f8436b.png)  
Получилось пробросить порты  
![image](https://user-images.githubusercontent.com/62139377/172030761-f5b05940-c8e1-4d8f-b813-cd2de26c16ab.png)  
Пробуем подключиться к веб-серверу  
![image](https://user-images.githubusercontent.com/62139377/172030798-1a3fcb6b-2b6e-4d9f-bbc3-08708c13c23d.png)  
Пробуем найти cve по ключевым словам "Pandora" и "v7.ONG.742_FIX_PERL2020"  
![image](https://user-images.githubusercontent.com/62139377/172030883-c2de2074-2ac0-42c5-b6fa-ed11bee487e2.png)  
Долго искали что-то похожее на правду. Сквозь боль и слезы нашли  
![image](https://user-images.githubusercontent.com/62139377/172030922-bb65630b-194c-4d44-bcbf-e813c7b1f67a.png)  
Пробуем использовать sqlmap и вводим необходимую директорию, которую нашли на сайте  
![image](https://user-images.githubusercontent.com/62139377/172030990-eae235e4-7c0b-4bc1-8dd4-ffde70c34c74.png)  
![image](https://user-images.githubusercontent.com/62139377/172031041-7cd033f7-e34b-4525-9dee-22024a57ca74.png)
![image](https://user-images.githubusercontent.com/62139377/172031052-7df45d6d-4e60-4d15-b6c5-aa73258af0d0.png)  
Вывел какой-то перечень таблиц  
![image](https://user-images.githubusercontent.com/62139377/172031087-eb365cd8-e650-45b5-ace7-bd41882c9f9c.png)
Посмотрели таблицу с паролями, но на сайт все равно не смогли зайти  
Нашли еще таблицу с сессиями, решили в ней покопаться  
Ввели в строку URL id сессии админимтратора  
![image](https://user-images.githubusercontent.com/62139377/172031587-953f3403-7f24-473f-a717-035a6897ee6c.png)  
Загрузили файл web shell, который до этого взяли с гита, и открыли его  
![image](https://user-images.githubusercontent.com/62139377/172032005-98e74150-fc88-4218-a317-bc22549d1619.png)
Взяли php скрипт с гита, поставили прослушивание на порт, который указан в скрипте  
![image](https://user-images.githubusercontent.com/62139377/172032067-5480b418-f4ea-4c0c-8346-3eca2fd2dab8.png)  
Победа  
![image](https://user-images.githubusercontent.com/62139377/172032092-599ec7d4-e1d4-43aa-b0d7-00675478cdca.png)

