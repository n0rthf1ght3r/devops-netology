# Домашнее задание к занятию «Инструменты Git» - Крюков Егор 

### Цель задания

В результате выполнения задания вы:

* научитесь работать с утилитами Git;
* потренируетесь решать типовые задачи, возникающие при работе в команде. 

### Инструкция к заданию

1. Склонируйте [репозиторий](https://github.com/hashicorp/terraform) с исходным кодом Terraform.
2. Создайте файл для ответов на задания в своём репозитории, после выполнения прикрепите ссылку на .md-файл с ответами в личном кабинете.
3. Любые вопросы по решению задач задавайте в чате учебной группы.

------

## Задание

В клонированном репозитории:

1. Найдите полный хеш и комментарий коммита, хеш которого начинается на `aefea`.

Полный хеш нашел слуедующими командами:
С помощью команды `git log --oneline | grep ^aefea`  нашел коммит `aefead2207 Update CHANGELOG.md`. Полный хеш получил командой `git log --pretty=%H -n 1 aefead2207`.
Полный хеш `aefead2207ef7e2aa5dc81a34aedf0cad4c32545`

2. Ответьте на вопросы.

* Какому тегу соответствует коммит `85024d3`?
***Ответ:*** Выполнил `git tag --contains 85024d3`, который вернул тег `v0.12.23`

* Сколько родителей у коммита `b8d720`? Напишите их хеши.
***Ответ:*** Выполнил команду `git show b8d720 --pretty=%P`, которая вернула 2 хеша `56cd7859e05c36c06b56d013b55a252d0bb7e158` `9ea88f22fc6269854151c571162c5bcf958bee2b`

* Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами  v0.12.23 и v0.12.24.
***Ответ:*** При помощи команды `git log --oneline v0.12.23..v0.12.24` получил список хешей и комметнтариев

```bash
  33ff1c03bb (tag: v0.12.24) v0.12.24
  b14b74c493 [Website] vmc provider links
  3f235065b9 Update CHANGELOG.md
  6ae64e247b registry: Fix panic when server is unreachable
  5c619ca1ba website: Remove links to the getting started guide's old location
  06275647e2 Update CHANGELOG.md
  d5f9411f51 command: Fix bug when using terraform login on Windows
  4b6d06cc5d Update CHANGELOG.md
  dd01a35078 Update CHANGELOG.md
  225466bc3e Cleanup after v0.12.23 release
```

* Найдите коммит, в котором была создана функция `func providerSource`, её определение в коде выглядит так: `func providerSource(...)` (вместо троеточия перечислены аргументы). ***Ответ:*** commit 8c928e83589d90a031f811fae52a81be7153e82f 

* Найдите все коммиты, в которых была изменена функция `globalPluginDirs`.
```
commit 7c4aeac5f30aed09c5ef3198141b033eea9912be - stacks: load credentials from config file on startup (#35952)
* stacks: load credentials from config file on startup
* delete unneeded file

commit 65c4ba736375607b6af6c035972f7f151232b6c6 - Remove terraform binary
commit e8a9debd2b4942069e2bbba583fc9193a78622cf - Remove accidentally-committed binary
commit 22c121df8631c4499d070329c9aa7f5b291494e1 - Bump compatibility version to 1.3.0 for terraform core release (#30988)
commit 35a058fb3ddfae9cfee0b3893822c9a95b920f4c - main: configure credentials from the CLI config file
commit 8364383c359a6b738a436d1b7745ccdce178df47 - Push plugin discovery down into command package

```
* Кто автор функции `synchronizedWriters`?
***Ответ:*** Команда `git grep -l "synchronizedWriters"` не нашла функцию в текущей ветке. Выполнил `git log -S "synchronizedWriters" --source --all --oneline`, которая нашла коммит `5ac311e2a9` с комментарием `main: synchronize writes to VT100-faker on Windows`. Выполнил команду `git show 5ac311e2a9`, которая показала автора Martin Atkins <mart@degeneration.co.uk>


