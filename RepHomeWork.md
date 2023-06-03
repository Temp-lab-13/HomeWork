# Работа с репозиторием

## Начало работы с Git
* **Первичная настройка Git**

Перед тем как вообще что-то можно будет сделать с помощью Git, после установки самой программы на ваше устройство необходимо, как минимум, "представиться" программе, задав ей своё Имя/Ник и электронную почту. А так же, проверить, установилась ли она вообще.

Сделать это можно в предоставленной установленной программе GitBash среде (по умолчанию, это Vim), или в Командной строке(Windows)/Теминале(MakOS, Lunix). Для этого понадобиться ввести нижеследующие команды.
```Bash
git --version
``` 
Отображает текущую версию Git, если она установилась успешно.
```Bash
git config --global <Имя/ник пользователя>
``` 
Это позволит программе запомнить ваше имя, от которого будут производиться все последующие коммиты.
```Bash
git config --global <user@email.com>
``` 
Ну а это позволит программе запомнить вашу электронную почту. 

Кстати, команда ниже позволяет посмотреть текущие настройки Git:
```Bash
git config --List
``` 
* **Инициализация**

Команда для инициализации текщей папки/директории в качестве репозитория.

Именно с этого начинается работа с репозиторием - вы его создаёте в определённом месте, что бы внутри отслеживать все последующие изменения.

Будьте винмательны при использовании этой команды и проверяйте текущее Ваше положение. Иначе, рискуете сделать репозиторием... всё. И это очень плохо.
```bash
git init
```
* **Навигация**

А как же перместиться к нужной директории, что бы там воспользоваться предыдущей командой и не испортить себе жизнь?

Для этого, если вы работаете не в среде с проводником, потребуется прописать путь к нужной папке, при этом, придёться учитывать особенности среды, в которой вы вводите команды. Поскольку команды относятся не к самому Git и являются стандартными для выбранной среды(Командной строки или Терминале, к примеру).
```bash
cd <путь>
```
Что бы подняться в дереве директорий на уровень выше, без прописывания всего пути:
```bash
cd ../
```
Что бы подняться в дереве директорий на *два* уровеня выше, без прописывания всего пути:
```bash
cd ../..
```
*(пожалуй, я не буду на этом моменте больше оснанавливаться, там команд ещё туча)*
* **Статус**

Говорят - *самая важная* команда Git. Позволяет проверить текущее состояние репозитория. Был ли он инициализрован в текущей папке вообще и находитесь ли в нём? 

Есть ли ещё не отслеживаемые директории и файлы(возможно вы что-то новое создали и перемстили в папку с репозиторием)? 

Есть ли уже модифицированный(изменённые) файлы требующие фиксации?

И ещё некоторые интересные моменты.
```bash
git status
```
## Работа с коммитами
* **Индексирование**

Прежде чем начинать работу с проектом и создавать свои первые коммиты, необходимо создать файлы проекта и, указать Git, что их необходимо отслеживать. Иначе, никакие изменения проводимые с ними, не будут фиксироваться. 

Что бы это сделать и проиндексировать новые *Созданые*, или добавленные в процессе файлы, необходимо, сделать, собственно, первый коммит (:

Для этого, первонаперво, необходимо "подготовить" файлы и папки, которые мы хотим отслеживать, к будущему коммиту.

По одному элементу, если вам нужнго добавить не все файлы и директории репозитория или конкретной подпапки.
```bash
git add <имя файла>
```
Или все разом. Но учтите, что добавлены буду только те файлы, что находяться в той папке, где вы находитесь, и во всех вложенных в неё директориях. По этому, наиболее целесообразно применять команду из корневой папки репозитория.
```bash
git add .
```
* **Commit**

И только после предшествующих действий применяется комманда *commit*. Не забывайте про комментарии к коммитам, что бы потом всегда можно было понять, что было сделанно на момент создания новго коммита. Будущий вы, за это будет вас благодарить с со лезами на глазах, после того как запорит вашу программу и ему придёться "откатиться" назад, когда всё ещё работало.
```bash
git commit -m "коментарий к коммиту"
```
Или просто:
```bash
git commit
```
**Но!** после этой команды, вас выбросит на спецэкран, где необходимо будет нажать на клавиатуре "i", что бы получить доступ к комментированию.

Потом, вписать коментарий и нажать "Esc", что бы выйти из режима редактирования. 

Что бы закончить и сохранить коммит, нужно нажать нажать ":" и, ввести "wq". После чего нажать "Enter/Ввод". 

Сложно, но для практики в работе с консольными средами - самое то.
* **Логи**

Команда раскрывает список изменений, т.е. всех коммитов сделанных в репозитории. С указанием изголовья и названием текущей ветки, из которой идёт запрос на логи.

Если вам нужен какой-то коммит из прошлого, что бы посмотреть как было раньше и как плохо вы сделали сейчас. То хэш-код нужных коммитов вы найдёте именно здесь. Конечно, если вы следовали совету и комментировали коммиты как пологается для упрощённой навигации по ним.

Кроме того, вы получите информацию о времени создания комита, кто его автор и куда слать гневные электронные писамь о его коде и... всё.

И да. Q - важная клавиша. (:
```bash
git log
```
* **Переход на коммит**

Если нужно перейти к старому коммиту ~~или сменить ветку репозитория~~, то просто наберите команду, а после хэш(многомного непонятных символов, который) заранее найденного коммита(можно просто 4-ре первых символа), ~~илибо имя ветки~~.
```bash
git checkout <хэш коммита>
```

* **Сравнение**

Если нужно посмотреть, чем текущий код отличается от того, что был при последнем коммите, то вам нужна команда:
```bash
git diff
```
## Работа с ветками
* **Создание новой ветки**
Для создания новой ветки, необходимо выбрать откуда будет происходить "отпочкование". Обычно это главная ветка masetr/main. Перейти на неё, если вы уже на ней не наодитесь.

После использовать команду с введением названия ветки(название ветки по хорошему должно отражать цель для которой она была создана)

```bash
git branch <НазваниеВетки>
```
Кстати, что бы просто просмотреть список существующих веток, нажно просто набрать (git branch), и всё. Вы увидите какие ветки существуют в работе, и на какой находитесь сейчас. Вот так:
```bash
git branch
```

* **Переход по веткам**

Если нужно сменить ветку репозитория, то просто наберите команду и имя ветки. ( не забудьте закоммитеть текущую ветку перед переходом)
```bash
git checkout <имя ветки>
```

* **Слияние веток**

Когда вы готовы позориться перед коллегами, то можно начать слияние веток. Как правило, дополнительные ветки перекидываются к основной (мастер или маин), в которой существует основной, чистовой проект. Но могут быть и доп. ветки у дополнительных веток. В любом случаи, вам надо переместиться на векту с *которой* вы собираетсеь слить *второстепенную ветку*. И указать, что вы хотите *стать едиными*
```bash
git merge <имя ветки>
```
Не забудьте закоммитить изменения.
* **Удаление веток**

Что бы замести следы и удалть не нужную ветку, наберите:

```bash
git branch -d <НазваниеВетки>
```
Если хочется посмотреть на визуальное отображение взаимодействия веток относительно вашей текущей, то...:
```bash
git log --graph
```
## Test-conflict
* **Рукотворный конфликт**

В случаи конфликта веток, когда существует в разных ветках сразу, разные изменения(контент), придёться в ручную разгребать, что оставить, что выкинуть, или всё оставить. Графические интерфейсы(VS Code, к примеру), в этом плане, намного удобней и наглядней.

И так. Чёто-то я не понял, с чего в конфликте у меня участвовал значительный кусок текста, который вообще не должен был в нём участвовать. Пробуем ещё раз.

Ещё раз. Предыдущий Конфликт был не очень удачно и наглядно сделан. Но зато, в нём уже не было проблемы с задействованный лишним текстом.


Какой-то текст для наглядного конфликта для 3-го теста.

Всё Ок. 
#
**Прмечание.** _Ветки удалять не буду, не потому что не знаю или забыл, а что бы можно было на них переключиться и посмотреть всё что с ними творилось отдельно._