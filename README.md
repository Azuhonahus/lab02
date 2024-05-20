## Laboratory work II


### Part I

1. **Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).**
2. **Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.**


```bash
	
$ mkdir lab02 && cd lab02
$ git init
Initialized empty Git repository in /Users/aleksandrnikonorov/Azuhonahus/workspace/tasks/lab02/.git/
$ git remote add origin https://github.com/Azuhonahus/lab02
$ git pull origin main
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), 1.49 KiB | 254.00 KiB/s, done.
From https://github.com/Azuhonahus/lab02
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> origin/main

	
```
	
	
3. **Создайте файл `hello_world.cpp` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу "Hello world" на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку `using namespace std;`.**


```bash
$ nano hello_world.cpp
```

```cpp
#include <iostream>

using namespace std;


int main() 
{

cout << "Hello,World! " << endl;

return 0;
}
```



4. **Добавьте этот файл в локальную копию репозитория.**


``` bash

$ git add -A

```


5. **Закоммитьте изменения с *осмысленным* сообщением.**


```bash 

$ git commit -m "add hello_world.cpp"
[main 0b325c0] add hello_world.cpp
 1 file changed, 12 insertions(+)
 create mode 100644 hello_world.cpp


```


6. **Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.**


```bash
$ nano hello_world.cpp
```
```cpp 
#include <iostream>
#include <string>

using namespace std;

int main()
{
    string name;
    
    getline(cin, name);
    
    
    cout<<"Hello World from " << name;

    return 0;
}
```


7. **Закоммитьте новую версию программы.** Почему не надо добавлять файл повторно `git add`?


```bash

 $ git add -A
 $ git commit -m "add hello_world v2.0"
 [main c9edd30] add hello_world v2.0
 1 file changed, 10 insertions(+), 5 deletions(-)

```


8. **Запуште изменения в удалёный репозиторий.**


```bash

$ git push origin main
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 757 bytes | 757.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/Azuhonahus/lab02
   0cc5ddc..c9edd30  main -> main


```


10. **Проверьте, что история коммитов доступна в удалёный репозитории.**


<img width="1440" alt="Снимок экрана 2024-05-20 в 11 00 15" src="https://github.com/Azuhonahus/lab02/assets/161419066/1ba8584a-99a2-481c-85eb-5b97f22170f1">






### Part II
**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*


1. **В локальной копии репозитория создайте локальную ветку `patch1`.**


```bash

$ git checkout -b patch1
Switched to a new branch 'patch1'

```


2. **Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.**


```bash
$ nano hello_world.cpp
```

```cpp
#include <iostream>
#include <string>


int main()
{
    std::string name;

    getline(std::cin, name);


    std::cout<<"Hello World from " << name;

    return 0;
}
```


3. **commit, push локальную ветку в удалённый репозиторий.**


```bash 

$ git add -A
$ git commit -m "hello_world.cpp without using namespace std;"
[patch1 cd56563] hello_world.cpp without using namespace std;
 1 file changed, 6 insertions(+), 8 deletions(-)
$ git push origin patch1
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 398 bytes | 398.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'patch1' on GitHub by visiting:
remote:      https://github.com/Azuhonahus/lab02/pull/new/patch1
remote: 
To https://github.com/Azuhonahus/lab02
 * [new branch]      patch1 -> patch1



```


4. **Проверьте, что ветка `patch1` доступна в удалёный репозитории.**


<img width="1440" alt="Снимок экрана 2024-05-20 в 11 03 02" src="https://github.com/Azuhonahus/lab02/assets/161419066/29d6fd1f-6759-4171-831f-88051d105e35">



5. **Создайте pull-request `patch1 -> master`.**


6. **В локальной копии в ветке `patch1` добавьте в исходный код комментарии.**


```bash
$ nano hello_world.cpp
```

```cpp
#include <iostream>
#include <string>


int main()
{
    std::string name;

    //name input
    getline(std::cin, name);

    //name output
    std::cout<<"Hello World from " << name;

    return 0;
}

```


7. **commit**, **push**.
```bash
$ git add -A
$ git commit -m "Comments"
[patch1 550fa2c] Comments
 1 file changed, 2 insertions(+), 1 deletion(-)
$ git push origin patch1
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 307 bytes | 307.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/Azuhonahus/lab02
   cd56563..550fa2c  patch1 -> patch1

```
8. **Проверьте, что новые изменения есть в созданном на **шаге 5_pull-request**


<img width="1440" alt="Снимок экрана 2024-05-20 в 11 06 07" src="https://github.com/Azuhonahus/lab02/assets/161419066/0a8a22ff-d16c-448a-91b1-9fac33f553a9">




9. **удалённый репозитории выполните  слияние PR `patch1 -> master` и удалите ветку `patch1` в удаленном репозитории.**

10. Локально выполните **pull**.


```bash

$ git checkout main
Switched to branch 'main'
$ git pull origin main
remote: Enumerating objects: 2, done.
remote: Counting objects: 100% (2/2), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 2 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (2/2), 1.76 KiB | 600.00 KiB/s, done.
From https://github.com/Azuhonahus/lab02
 * branch            main       -> FETCH_HEAD
   c9edd30..1180c08  main       -> origin/main
Updating c9edd30..1180c08
Fast-forward
 hello_world.cpp | 15 +++++++--------
 1 file changed, 7 insertions(+), 8 deletions(-)


```


11. С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.


```bash

$ git log

```
<img width="974" alt="Снимок экрана 2024-05-20 в 11 08 54" src="https://github.com/Azuhonahus/lab02/assets/161419066/4119cd7e-ff2f-4b93-8ada-820037e5c380">




12. Удалите локальную ветку `patch1`.


```bash

$ git branch -D patch1
Deleted branch patch1 (was 550fa2c).


```




### Part III
**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*


1. **Создайте новую локальную ветку `patch2`.**


```bash

$ git checkout -b patch2
Switched to a new branch 'patch2'

```


2. **Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.**


```bash

$ clang-format  -style=Mozilla hello_world.cpp
#include <iostream>
#include <string>

int
main()
{
  std::string name;

  // name input
  getline(std::cin, name);

  // name output
  std::cout << "Hello World from " << name;

  return 0;
}


```


3. **commit, push, создайте pull-request `patch2 -> master`**.


```bash

$ git add -A
$ git commit -m "Mozilla codestyle"
[patch2 1c8dbbc] Mozilla codestyle
 1 file changed, 1 insertion(+)
$ git push origin patch2
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 291 bytes | 291.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/Azuhonahus/lab02
   1180c08..1c8dbbc  patch2 -> patch2
aleksandrnikonorov@MacBook-Air-Aleksandr lab02 % git pull origin main
From https://github.com/Azuhonahus/lab02
 * branch            main       -> FETCH_HEAD
Already up to date.


```


4. **В ветке "master" в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.**


5. **Убедитесь, что в pull-request появились 'конфликтны'.**


6. **Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.**


```bash

$ git pull origin main
 * branch            main       -> FETCH_HEAD
Already up to date.
$ git rebase main
Current branch patch2 is up to date.

```


7. **Сделайте *force push* в ветку `patch2`**

```bash

$ git push --force origin patch2
Everything up-to-date


```


8. **Убедитель, что в pull-request пропали конфликтны.**


9. **Вмержите pull-request `patch2 -> master`.**

