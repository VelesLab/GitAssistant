# Помощник по работе с Git

## Содержание
- [Базовые понятия](#базовые-понятия) 
- [Командная строка](#командная-строка)
- [Настройка Git](#настройка-git)
- [Работа с Git](#работа-с-git)
- [Работа с GtHub](#работа-с-github)
- [Файл README.md](#файл-readme-md)
- [Навигация по коммитам](#навигация-по-коммитам)
- [Статусы файлов в Git](статусы-файлов-в-git)

## Базовые понятия
- VCS (**SCM**) **V**ersion **C**ontrol **S**ystem (**S**ource **C**ontrol **M**anagement)
Система контроля версий  - это програмное обеспечение, которое помогает отылеживать изменения в программах, тектовых файлах, больших документах, веб-сайтах и так далее.
- Git (Гит) - Один из многих продуктов VCS.
- Командная строка (**C**ommand-**l**ine **I**nterface, *CLI*) - Один из основных инструментов взаимодействия с компьютером.

## Командная строка
- [Инструкция по установке для пользователей Windods]()

Git — это программа, которая в том числе может работать из командной строки. Любой графический интерфейс для Git всего лишь преобразует клики пользователя в вызовы программы.
Если вы пользователь macOS или Linux, запустите программу Terminal. Её можно найти через окно поиска операционной системы. А можно использовать комбинацию горячих клавиш:

Для Linux:
```
Ctrl+Alt+T
```
Для macOS:
```
Cmd+Space
```
затем ввести 
``` 
terminal
```
Если вы пользователь Windows, запустите программу Git Bash — [как её установить]()

### Основные команды

#### Навигация

```pwd``` (**p**rint **w**orking **d**irectory, «показать рабочую папку») — покажи, в какой я папке;

```ls``` (**list** directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;

```cd <имя папки>``` (**c**hange **d**irectory, «сменить директорию») — перейди в папку <имя папки>;

#### Работа с файлами

```touch <имя файла>``` (touch, «коснуться») — создай файл <имя файла> в текущей папке;

```mkdir <имя папки>``` (**m**ake **d**irectory, «создать директорию») — создай папку с именем <имя папки> в текущей папкеж;

```cp <имя файла> ~/<имя папки>``` (**copy**, «копировать») — скопируй файл в другое место;

```mv <имя файла> ~/<имя папки>``` (**move**, «переместить») — перемести файл или папку в другое место.

[Шпаргалка. Базовые команды в консоли](https://github.com/VelesLab/GitAssistant/blob/master/instructions/console-commands.md)

## Настройка Git

[Инструкция по установке Git]()

Для настройки Git можно использовать командную строку.

#### Работа с файлом настройки ```.gitconfig```

Чтобы участникам проекта было понятно, кто и какие изменения вносил, нужно представиться и указать имя пользователя и адрес электронной почты.

Можно указать любую электронную почту и любое имя. Сделать это можно с помощью команды ```git config``` (configuration — «конфигурация», «настройка») с ключом -```-global``` («глобальный»). При этом не имеет значения, в какой директории вы находитесь прямо сейчас: вызов ```git config --global``` сработает везде.

В качестве значения ```user.name``` нужно указать своё имя или никнейм. Для настройки параметра ```user.email``` указывают электронную почту.

```bash
$ git config --global user.name "User Namovich" 
# имя или ник нужно написать латиницей и в кавычках
```

```bash
$ git config --global user.email username@yandex.ru
# здесь нужно указать свой настоящий email
``` 

Все глобальные настройки Git хранит в файле ```.gitconfig``` в домашней директории. Команда запишет в этот файл указанные имя и почту. Чтобы убедиться в этом, можно вызвать команду для чтения файлов.

```bash
$ cat ~/.gitconfig
``` 

Другой способ проверки — вывести содержимое файла конфигурации Git той же командой ```git config``` с флагом ```--list``` («список»).

```bash
$ git config --list 
```

В ответ командная строка покажет текущие значения настроек.

```bash
user.name=Username
user.email=username@yandex.ru 
```

## Работа с Git

### Инициализируем репозиторий

#### Сделать папку репозиторием — ```git init```

Чтобы Git начал отслеживать изменения в проекте, папку с файлами этого проекта нужно сделать **Git-репозиторием** (repository — «хранилище»). Для этого следует переместиться в неё и ввести команду ```git init``` (initialize — «инициализировать»).

Например, создайте папку ```first-project``` и сделайте её Git-репозиторием: перейдите в неё с помощью команды ```cd``` и выполните ```git init```.

```bash
$ cd ~/dev/first-project # перешли в нужную папку

$ git init # создали репозиторий 
```

Можно создать папку в любом месте на компьютере. Но в этом случае не забывайте менять в наших примерах путь ```~/dev/first-project``` на тот, который ведёт к вашей папке. Помните, что не рекомендуется создавать репозиторий Git внутри другого Git-репозитория. Это может вызывать проблемы с отслеживанием изменений.

В некоторых случаях при инициализации репозитория Git может показать объёмное сообщение, которое начинается со слов ```Using 'master' as the name…```. Не пугайтесь: это не ошибка. Пока это сообщение не имеет большого значения.

Также ```git init``` выведет сообщение вида ```Initialized empty Git repository in <*ваша папка с проектом*>/.git/``` («инициализирован пустой Git-репозиторий в ```<*ваша папка*>/.git/```»). В подпапке ```.git``` Git будет хранить всю служебную информацию.

![Image alt](https://github.com/VelesLab/GitAssistant/blob/master/images/S1_02_02-1_1684836781.png)

Команда ```git init``` — одна из редко применяемых, ведь репозиторий создаётся один раз, а пользоваться им можно сколько угодно долго.

**«Разгитить» папку, если что-то пошло не так, — ```rm -rf .git```**

Если вы случайно сделали Git-репозиторием не ту папку, её можно «разгитить». Для этого нужно удалить скрытую подпапку ```.git```.

```bash
$ cd <папка с репозиторием> # перешли в папку

$ rm -rf .git # удалили подпапку .git 
```

- ключ ```-r``` (**r**ecursive — «рекурсивно») позволяет удалять папки вместе с их содержимым;
- ключ ```-f``` (**f**orce — «заставить») избавит вас от вопросов вроде «Вы точно хотите удалить этот файл? А этот? И этот тоже?».

Будьте осторожны: в подпапке ```.git``` хранится история изменений. Если удалить .git, то вся история проекта будет стёрта без возможности восстановления — останется только последняя версия файлов.

**Проверить состояние репозитория — ```git status```**

После инициализации репозитория ```first-project``` запустите команду ```git status``` (status — «статус», «состояние») — она показывает текущее состояние репозитория.

Команда ```git status``` выведет:

- название текущей ветки: On branch master или On branch main;
- сообщение о том, что в репозитории ещё нет коммитов: No commits yet;
- сообщение, которое говорит: «чтобы что-нибудь закоммитить (то есть зафиксировать), нужно сначала это создать» — nothing to commit (create/copy files and use "git add" to track).

#### Добавляем файлы в репозиторий

**Подготовить файлы к сохранению — ```git add```**

- Команда ```git add``` позволяет подготовить файл к сохранению.
- Команда ```git add --all``` подготовит к сохранению сразу все файлы.
- С помощью ```git add .``` можно добавить в репозиторий текущую папку со всеми файлами.

#### Делаем первый коммит

Коммит — это одна из основных сущностей в Git (и в других системах контроля версий). Коммит гарантирует, что изменения будут сохранены в истории и при необходимости к ним можно будет «откатиться». 

Выполнить коммит — ```git commit```

Сделать коммит можно командой ```git commit``` c ключом -m (message — «сообщение»), который присваивает коммиту сообщение.

Обычно в таком сообщении поясняется, в чём именно состояли изменения. Это как заметки на полях: благодаря им проще читать и понимать текст. Сообщение коммита выполняет те же функции — улучшает понимание и упрощает навигацию. Оно пишется после ключа -m в кавычках.

- Коммит можно сделать с помощью команды git commit.
- Ключ -m позволяет присвоить коммиту сообщение. Помните, что такие сообщения должны быть информативными: чётко описывать изменения.
- В коммит попадает то, что было предварительно добавлено «в корзину», или «в кадр», перед коммитом.

#### Просмотреть историю коммитов — ```git log```

Чтобы увидеть их все, введите команду ```git log``` (log — «журнал [записей]»).

## Работа с GitHub

GitHub — платформа для хранения IT-проектов и совместной работы над ними с использованием Git. По сути, это сайт, куда можно загрузить файлы своего проекта для обмена с другими людьми.

Git и GitHub — это два разных проекта, которые развиваются независимо друг от друга. 

Git:
- консольный инструмент для работы с локальными и удалёнными репозиториями;
- проект с открытым исходным кодом.

GitHub:
- платформа для размещения удалённых репозиториев;
- принадлежит компании Microsoft.

[Инструкция по регистрации на GitHub]()

[Инструкция по созданию репозитория на GitHub]()

[Инструкция по генерации SSH-ключа]()

[Инструкция по связыванию SSH-ключа и GitHub-аккаунта]()

#### Привязать удалённый репозиторий к локальному — ```git remote add```

Откройте консоль, перейдите в каталог локального репозитория и введите команду ```git remote add``` (remote — «удалённый» и add — «добавить»).

```bash
$ cd ~/dev/first-project
$ git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
```

Команде необходимо передать два параметра: имя удалённого репозитория и его URL. В качестве имени используйте слово ```origin```. А URL вы скопировали со страницы удалённого репозитория.

**Убедиться, что репозитории связаны, — ```git remote -v```**

#### Синхронизируем локальный и удалённый репозитории

**Отправить изменения на удалённый репозиторий — ```git push```**

В первый раз эту команду нужно вызвать с флагом ```-u``` и параметрами ```origin``` (имя удалённого репозитория) и main или master (название текущей ветки). Флаг ```-u``` свяжет локальную ветку с одноимённой удалённой. Как вы связывали локальный и удалённый репозитории в предыдущем уроке, так же и здесь нужно дополнительно связать ветки.

```bash
$ git push -u origin main # Если команда приведёт к ошибке, попробуйте 
                          # заменить main на master. 
```

## Файл README.md

Чтобы другие пользователи, а также потенциальные клиенты или работодатели могли понять, что представляет собой проект, его нужно описать. Такое описание принято указывать в файле ```README.md``` (read — «прочитай» и me — «меня»).

#### Подробнее о том, зачем нужен README.md

Как правило, в ```README.md``` проекта можно найти следующую информацию:

1.  Название проекта и его краткое описание: кем создан, для чего, какие решает задачи и какие закрывает проблемы.
2. Технологии, которые применяются в проекте. В чём его отличие от аналогичных.
3. Документация проекта — подробная инструкция о том, что представляет собой проект.
4. Планы проекта, если они есть.

## Навигация по коммитам

#### Хеш - идентификатор коммита

Хеширование (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток» (англ. fingerprint).

Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий, или родительский (англ. parent), коммит.

Обычно хеш — это короткая (4040 символов в случае SHA-1) строка, которая состоит из цифр 0—90—9 и латинских букв A—FA—F (неважно, заглавных или строчных). Она обладает следующими важными свойствами:

-  если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый;
- если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).

Чтобы убедиться в этом, можно поэкспериментировать с SHA-1 на этом сайте — попробуйте ввести в поле input (англ. «ввод») разные символы, слова или предложения и понаблюдайте, как меняется хеш в поле output (англ. «вывод»).

Git хранит таблицу соответствий ```хеш → информация о коммите```. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. Можно сказать, что хеш — основной идентификатор коммита.

#### Элементы описания коммита

После вызова ```git log``` появляется список коммитов.

- строка из цифр и латинских букв после слова commit — это хеш коммита;
- Author — имя автора и его электронная почта;
- Date — дата и время создания коммита;
- в конце находится сообщение коммита.

#### Получить сокращённый лог 

Получить сокращённый лог можно с помощью команды ```git log``` с флагом ```--oneline``` (англ. «одной строкой»). В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.

Сокращённый лог полезен, если в репозитории уже много коммитов — например, сотни или тысячи. В этом случае можно быстро найти нужный по описанию.

#### HEAD

Файл ```HEAD``` (англ. «голова», «головной») — один из служебных файлов папки ```.git```. Он указывает на коммит, который сделан последним (то есть на самый новый).

В этом можно убедиться с помощью терминала. Перейдите в папку ```.git``` командой ```cd```. Посмотрите содержимое файла ```HEAD``` командой ```cat```.

Внутри ```HEAD``` — ссылка на служебный файл: ```refs/heads/master``` (или ```refs/heads/main``` в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита.


