## PART 1
# Задание №1
Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
```sh
echo "# lab02" >> README.md
git init

Инициализирован пустой репозиторий Git в /home/bogdan/lab02/.git/

```
С помощью команды git init инициализировали пустой репозиторий
# Задание №2
Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
```sh
git add README.md
git commit -m "first commit"

[master (корневой коммит) e12484e] first commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md

git branch -M main
git remote add origin https://github.com/Lam0Rka/lab02.git
git push -u origin main

Username for 'https://github.com': Lam0Rka
Password for 'https://Lam0Rka@github.com': 
Перечисление объектов: 3, готово.
Подсчет объектов: 100% (3/3), готово.
Запись объектов: 100% (3/3), 224 bytes | 224.00 KiB/s, готово.
Всего 3 (изменения 0), повторно использовано 0 (изменения 0)
To https://github.com/Lam0Rka/lab02.git
 * [new branch]      main -> main
Ветка «main» отслеживает внешнюю ветку «main» из «origin».


```
add - Добавить (все дальнейшие комментарии будут скопированы из man тк я понимаю, что они делают и в принципе перевод)
commit - Record changes to the repository.
branch - List, create, or delete branches.
push - Update remote refs along with associated objects
# Задание №3
Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.
```sh
cat > hello_world.cpp

include <iostream>
using namespace std;
int main()
{
cout<<"Hello World";
}

```
С помощью команды cat мы создали файл расширения .cpp
# Задание №4
Добавьте этот файл в локальную копию репозитория.
```sh
git add hello_world.cpp
```
# Задание №5
Закоммитьте изменения с осмысленным сообщением.
```sh
git commit -m 'Добавили файл .cpp с небольшой ошибкой'

[main 3f8aa4d] Добавили файл .cpp с небольшой ошибкой
 1 file changed, 6 insertions(+)
 create mode 100644 hello_world.cpp

```

# Задание №6
Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
```sh
#include <iostream>
#include <string>

using namespace std;

int main()
{
string n;
cout << "Введите имя пользователя: ";
cin >> n;
cout<<"Hello World from " <<n;
}
```

# Задание №7
Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?
```sh
git commit -m 'Изменена первая версия программы был добавлен "#", а также появилась возможность вписать своё имя'
```
Вместо git add мы просто используем git push и все наши файл удачно загружаются на репозиторий(могу быть не прав)
# Задание №8
Запуште изменения в удалёный репозиторий.
```sh
git push
```
Запушили, что тут ещё говорить
# Задание №9
Проверьте, что история коммитов доступна в удалёный репозитории.
```sh
https://github.com/Lam0Rka/lab02 (Доступна)
```
##PART 2
# Задание №1
В локальной копии репозитория создайте локальную ветку patch1.
```sh
git checkout -b patch1
Переключено на новую ветку «patch1»
```
checkout - Переключится на новую ветку
 -b <new_branch>
 Create a new branch named <new_branch> and start it at <start_point>
# Задание №2
Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;.
```sh
#include <iostream>
#include <string>

int main()
{
std::string n;
std::cout << "Введите имя пользователя: ";
std::cin >> n;
std::cout<<"Hello World from " <<n;
}

git add hello_world.cpp

```
Изменения внесены
# Задание №3
commit, push локальную ветку в удалённый репозиторий.
```sh
git status

На ветке patch1

git commit -m 'Программа до конца доработана, создан патч1'

[patch1 dc77a28] Программа до конца доработана, создан патч1
 1 file changed, 7 insertions(+), 3 deletions(-)

git push origin patch1
```

# Задание №4
Проверьте, что ветка patch1 доступна в удалёный репозитории.
```sh
https://github.com/Lam0Rka/lab02/tree/patch1
```

# Задание №5
Создайте pull-request patch1 -> master.
```sh
Сделано на сайте
```

# Задание №6
В локальной копии в ветке patch1 добавьте в исходный код комментарии.
```sh
Сделано на сайте
git add hello_world.cpp
```
Done
# Задание №7
commit, push.
```sh
git commit -m 'Я устал писать нормальный текст'
git push origin patch1
```

# Задание №8
Проверьте, что новые изменения есть в созданном на шаге 5 pull-request
```sh
https://github.com/Lam0Rka/lab02/pull/1 (Да, всё есть)
```

# Задание №9
В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.
```sh
git checkout main
Переключено на ветку «main»
Ваша ветка обновлена в соответствии с «origin/main».

git merge patch1
Обновление 3f8aa4d..d8acfd5
Fast-forward
 hello_world.cpp | 10 +++++++---
 1 file changed, 7 insertions(+), 3 deletions(-)

git push origin main
Username for 'https://github.com': Lam0Rka
Password for 'https://Lam0Rka@github.com': 
Всего 0 (изменения 0), повторно использовано 0 (изменения 0)
To https://github.com/Lam0Rka/lab02.git
   3f8aa4d..d8acfd5  main -> main

git push origin patch1
Username for 'https://github.com': Lam0Rka
Password for 'https://Lam0Rka@github.com': 
Everything up-to-date
```

# Задание №10
Локально выполните pull.
```sh
git push origin patch1
Username for 'https://github.com': Lam0Rka
Password for 'https://Lam0Rka@github.com': 
Everything up-to-date
```

# Задание №11
С помощью команды git log просмотрите историю в локальной версии ветки master.
```sh
git log
commit d8acfd5516d8b39c07ebc47ed112eca7712edf2c (HEAD -> main, origin/patch1, origin/main, patch1)
Author: Lam0Rka <mr.ender.super@gmail.com>
Date:   Wed Mar 10 22:13:57 2021 +0300

    Я устал писать нормальный текст

commit dc77a2827202f87b2b19498f38812252556f9049
Author: Lam0Rka <mr.ender.super@gmail.com>
Date:   Wed Mar 10 21:52:23 2021 +0300

    Программа до конца доработана, создан патч1

commit 3f8aa4d056dab525cd3b2bb87a92ce1a6e8bfdb2
Author: Lam0Rka <mr.ender.super@gmail.com>
Date:   Wed Mar 10 21:22:28 2021 +0300

    Добавили файл .cpp с небольшой ошибкой

commit e12484e7c93f08e115f6505ea8436a475331b55c
Author: Lam0Rka <mr.ender.super@gmail.com>
:
```
# Задание №12
Удалите локальную ветку patch1.
```sh
git branch -d patch1
Ветка patch1 удалена (была d8acfd5).
```
-d - Удалили ветку
##PART 3
# Задание №1
Создайте новую локальную ветку patch2.
```sh
git checkout -b patch2
```

# Задание №2
Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla.
```sh
sudo apt-get install clang-format
clang-format -i -style=Mozilla hello_world.cpp
```

# Задание №3
commit, push, создайте pull-request patch2 -> master.
```sh
git add hello_world.cpp
git commit -m 'Changed code-style to Morilla style'
git push origin patch2
```

# Задание №4
В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
```sh
#include <iostream>
#include <string>

int main()
{
std::string n;
std::cout << "Введите имя пользователя: "; //Privet Narod
std::cin >> n;
std::cout<<"Hello World from " <<n;
}
git add hello_world.cpp
git commit -m 'НОВЫЙ СОВЕРШЕННЫЙ КОД'
git push origin main
```

# Задание №5
Убедитесь, что в pull-request появились конфликтны.
```sh
Конфликт действительно появился
```

# Задание №6
Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.
```sh
git checkout patch2
git pull origin master
git rebase master
git add hello_world.cpp
git commit -m 'Solved conflict'
git rebase master
git rebase --continue
git push origin patch2 --force
```
Тут долго рассказывать кто что каго съел и что произошло, но конфликт решён
# Задание №7
Сделайте force push в ветку patch2
```sh
git push origin patch2 --force
```

# Задание №8
Убедитель, что в pull-request пропали конфликтны.
```sh
Конфликты все пропали УРА УРА УРА
```

# Задание №9
Вмержите pull-request patch2 -> master.
```sh
Всё сделано и подтверждено
```

Так, вы просили сказать с какими трудностями мы столкнулись, да вроде нет ничего такого, все живы и счастливы
