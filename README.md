# Лабораторная работа 5

## Задание 1 - Автоматизация проверки формата файлов при коммите
Создайте bash-скрипт, который будет выполнять проверку того, что коммитится файл формата .txt и в файле присутствует какой-то текст (например, в конце файла есть подпись автора, неважно как она выглядит, главное чтобы была какая-нибудь проверка содержимого файла). Далее поместите этот скрипт в нужную папку и проверьте, что перед каждым коммитом проходит проверка, например, добавьте вывод о результате проверки в консоль. За этот функционал отвечает Git Hooks, там сказазно как автоматизировать такую проверку.

## Решение

Создадим файл через консоль под названием script.bash командой touch script.bash. Учитываем, что наши файлы выглядят слеюущим образом:

![11](https://github.com/user-attachments/assets/0fa222ae-696b-41c5-9c12-628a39b0ae02)

![22](https://github.com/user-attachments/assets/52e4b1a1-7c64-4bb9-8e49-9136de75774e)

Этот файл будет использоваться для валидации файлов, которые добавляются в коммит в процессе его создания. Также будет предусмотрен случай, когда пользователь не добавляет никаких новых изменённых файлов. Внутри файла будет размещён следующий код, который проверяет правильность формата и наличие информации об авторе:

![396584752-048f06cc-ae86-40f8-b99f-a3feeedbb868](https://github.com/user-attachments/assets/fef1621f-bae4-44a5-86fe-ccfd837cd499)

Закроем script.bash, сохранив его. Сделаем этот код запускаемым командой chmod +x script.bash. Перейдём в папку .git/hooks. Там изменим файл pre-commit.sample:
image

![396585689-3e22c011-7100-4b4f-aa01-250e92d18ba0](https://github.com/user-attachments/assets/1aeeefa2-0a24-4784-bfea-4ad7ffa59a39)

Уберём из названия файла .sample, чтобы он мог быть запущен консолью.

Сделаем файл запускаемым командой chmod +x pre-commit.

Проверим, что всё работает:

![396588020-672d4fbd-7295-47f2-b314-db7fc8296900](https://github.com/user-attachments/assets/dd86abf8-ebe3-4d76-8e54-3512fcc8d991)

## Задание 2 - Использование Git Flow в проекте
 
Предположим, у вас есть задача на создание новой функциональности для вашего проекта с использованием Git Flow. Давайте рассмотрим конкретный пример. В примере важен не сам проект и его код (его тут вообще как такового нет), а принцип работы Git Flow.

Убедимся, что Git Flow установлен в системе.

![396591072-cde0c91b-e061-4436-8dcf-7f80393afd32](https://github.com/user-attachments/assets/dc795569-b095-4477-8fd4-81206f30116f)

Инициализируем командой git flow init и создадим ветку для новой функциональности:

![image](https://github.com/user-attachments/assets/a03e4bb6-130a-4c5d-9893-f5b8a95391f3)

Начнём работу над feature. Создадим файл task_manager.py, введём код из примера в него и заккомитим изменения. Далее пропишем команду git flow feature finish task-management.

![image](https://github.com/user-attachments/assets/8da9cacd-14f8-4c1e-9f0f-b7d51ad4f6cf)

Переключимся на ветку develop. Создадим релиз и закоммитим его.

![image](https://github.com/user-attachments/assets/1fa7f252-e049-4e36-b2e8-c8f8702a007a)
![image](https://github.com/user-attachments/assets/89c9c43f-ee10-477b-9b72-c2a9b61347ba)

Пропишем git flow release finish v1.0.0, чтобы закончить работу над релизом, а затем создадим hotfix.

![image](https://github.com/user-attachments/assets/7e7f77ca-1612-47c6-8952-75d39be84a7d)

После успешной работы над hotfix пропишем git flow hofix finish hotfix-1.0.1.

![image](https://github.com/user-attachments/assets/196d3179-216f-4b62-9052-af5e73cc8aae)

Завершим работу и загрузим изменения при помощи git push origin develop. Не забудем про git push origin main.

![image](https://github.com/user-attachments/assets/048b19aa-c6c8-4d59-9b7b-5266ee8e7664)
![photo_2024-12-24_18-08-10](https://github.com/user-attachments/assets/a5715282-6207-44a1-8873-393f097a1770)
