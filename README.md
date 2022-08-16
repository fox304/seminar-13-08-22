# Инстукция по работе с GIT
## Что такое *Git*?
*Git* - это одна из реализаций распределённых систем контроля версий , позволяющая организовать версионность , как локально ,так и на удалённом сервере.Самая популярная платформа ,реализующая *Git*, - [GitHab](https://github.com)
## Подготовка репозитария
Для создания в папке репозитория необходимо открыть эту папку в терминале  и написать команду " git init ",после чего в этой папке создастся скрытая папка * .git *, и так.обр. папка станет репозиторием

## создание сохранений


### Добавление файла к сохранению
Для того чтобы добавить файл к сохранению ,необходимо использовать команду *git add*.В терминале с открытой папкой-репозитарием необходимо написать *git add <название файла>*,и этот файл добавится к сохранению.

### Просмотр состояния репозитория
Для просмотра состояния репозитория используется команда *git status*.В терминале с открытой папкой-репозиторией необходимо написать команду *git status*.В результате можно увидеть следующие выводы:
1. On branch *** nothing to commit - это означает нет активных изменений
2. Untraced file - это означает , что имеются файлы,не отслеживаемые системой 

## создание коммитов
### Создание фиксации
Для создания фиксации используется команда *git commit*.Для этого в терминале с папкой-репозиторием необходимо написать команду *git commit - m <сообщение к коммиту>*.Сообщение к коммиту писать **ОБЯЗАТЕЛЬНО**.


## перемещение между сохранениями

### журнал изменений
Для просмотра историй изменений  используется команда *git log*.Для этого в терминале с папкой-репозиторием необходимо написать *log* и вы увидите список всех коммитов в этой ветке с описанием :имени ,эл.почты,сообщением к коммиту и номер коммита.

### перемещение между коммитами
Для перемещения между коммитами используется команда *git checkout*.Для этого в терминале с папкой-репозиторием необходимо написать *git checkout <номер коммита>*.Номер коммита берется из журнала изменений ветки.

## ветки GIT
### Создание ветки 
Для того ,чтобы создать ветку нужно...


Ключевая особенность Git — ветвление, возможность работать над разными версиями проекта .То есть вместо одного списка с упорядоченными коммитами история будет расходиться в определённых точках (что делает её похожей на дерево).Каждая ветвь в Git содержит  указатель HEAD на последний коммит в этой ветке.Ветку нужно называть в соответствии с ее функциональностью.Главная ветка по умолчанию называется master.
___

Для создания ветки нужно написать :
>git branch ("имя ветки")

чтобы посмотреть список веток:
>git branch


для перемещения по веткам:
>git checkout ("имя ветки")

можно создать ветку и сразу переместиться туда одной командой:
>git checkout -b ("имя ветки")

---

После создания веток нужно обязательно сохранить изменения нажатием *Ctrl+S*,затем проиндексировать ,набрав команду *git add (*название репозитория*),затем "закоммититься" командой *git commit - m "<коментарий для коммита>"


## слияние веток  и решение конфликтов
Слияние веток - это перенос кода из одной ветки в другую.
Например, когда мы заканчиваем работу над веткой и сделали новый функционал или исправили баги, мы сливаем ее в mfster-ветку.
Сливать друг в друга можно любые ветки. Когда новая ветка сливается в мастер то мы обычно заканчиваем  работать над функционалом и хотим выложить его на боевой сайт. 
Когда мастер сливается в ветку , то мы продолжаем работать над веткой, но хотим периодически подтягивать новые коммиты с сервера - новый код, который написали наши коллеги.
Команды очень просты:
>git merge "<имя ветки, **КОТОРУЮ** хотим слить>"
После этого происходит вливание ветки на ту ,где находился в момент написания "мёрджа".

Вливание происходит несколькими способами:
1. fast forward merge-изменения одной ветки переходят в другую без создания коммитов.
2. ort stratagy - вливание будет с некоторым смещением и созданием коммита.
3. Создастся **КОНФЛИКТ** !

Собственно конфликт разрешается обычно консервативным способом-вручную корректируется то,что необходимо.

Есть возможность уйти от конфликта ,набрав команду:
>git merge --abort "<название ветки,которую вливал и передумал>"

## удаление веток
Удаление веток делается простым способом встав на ветку master и напечатав следующее:
>git branch -d "<название ветки>"

Если вдруг возникает ошибка: The branch "<название ветки>" is not fully merged , то для принудительного удаления ветки можно воспользоваться опцией -D:
>git branch -D "<название ветки>"

## Алиасы или шорткаты
В GIT есть возможность ипользовать сокращённые команды , установленные самим пользователем.Это так называемые алиасы.Особенно удобно,когда конструкция очень длинная как в данном примере:
>git config --global alias.hist "log --pretty=format:'%h %ad | %s%d [%an]' --graph --date=short"

теперь к логу можно обращаться через короткую команду:
>git hist

и нам явится уникальное графическое дерево с компактной историей коммитов!

Другие алиасы:
>git config --global alias.co checkout

>git config --global alias.ci commit

>git config --global alias.st status

>git config --global alias.br branch
