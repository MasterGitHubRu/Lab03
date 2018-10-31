## Laboratory work III

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [x] 1. Создать публичный репозиторий с названием **lab03** и с лиценцией **MIT**
- [x] 2. Ознакомиться со ссылками учебного материала
- [x] 3. Выполнить инструкцию учебного материала
- [x] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
$ export GITHUB_USERNAME=<имя_пользователя>   //создание переменных с именем пользователся и почтовым ящиком
$ export GITHUB_EMAIL=<адрес_почтового_ящика>
$ alias edit=<nano|vi|vim|subl>  //создание псевдонима редактора
```

```ShellSession
$ cd ${GITHUB_USERNAME}/workspace  //переход в kutyirov/workspace
$ source scripts/activate   //добавление директории в path
```

```ShellSession
$ mkdir projects/lab03 && cd projects/lab03  //создаем и переходим в директорию projects/lab03
$ git init				     //инициализация гита в текущей папке
$ git config --global user.name ${GITHUB_USERNAME} //настройка гита: имя пользователя, почта
$ git config --global user.email ${GITHUB_EMAIL}
$ git config -e --global //вывод данных пользователя
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03.git //загрузка гита с ссылки
$ git pull origin master
$ touch README.md // создание пустого файла 
$ git status      //проверка изменений гита
$ git add README1.md //добавление файла
$ git commit -m"added README1.md" //подтверждение изменения с комментарием
$ git push origin master //загрузка гита на сайт 
```

Добавить на сервисе **GitHub** в репозитории **lab03** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
.idea/
```

```ShellSession
$ git pull origin master
$ git log
```

```ShellSession
$ mkdir sources //создание директорией sources include examples
$ mkdir include
$ mkdir examples
$ cat > sources/print.cpp <<EOF //создание файла print.cpp с данным содержимым
#include <print.hpp>

void print(const std::string& text, std::ostream& out) {
  out << text;
}

void print(const std::string& text, std::ofstream& out) {  //вывод в файл
  out << text;
}
EOF
```

```ShellSession
$ cat > include/print.hpp <<EOF //создание хэдэра для предыдущего файла
#include <string>
#include <fstream>
#include <iostream>

void print(const std::string& text, std::ostream& out = std::cout);
void print(const std::string& text, std::ofstream& out);  
EOF
```

```ShellSession
$ cat > examples/example1.cpp <<EOF  //создание 2-х файлов для вывода
#include <print.hpp>

int main(int argc, char** argv) {
  print("hello");
}
EOF
```

```ShellSession
$ cat > examples/example2.cpp <<EOF
#include <fstream>
#include <print.hpp>

int main(int argc, char** argv) {
  std::ofstream file("log.txt");   //файл для вывода log.txt
  print(std::string("hello"), file);
}
EOF
```

```ShellSession
$ edit README.md
```

```ShellSession
$ git status  //проверка все ли файлы создались
$ git add .   //добавление всех файлов
$ git commit -m"added sources" //коммитим
$ git push origin master  //отправка на сайт
```

## Result

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=03
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Links

- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)
