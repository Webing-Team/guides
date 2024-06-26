# Использование GitHub через командную строку
### Содержание:
1. [Загрузка файлов](#загрузка-файлов).

### Загрузка файлов
**Шаг 1.**  Первым делом необходимо создать репозиторий в GitHub.

![Хайповая картинка](/git-and-github/images/image-1.png)

**Шаг 2.** Чтобы загрузить файлы в репозиторий, необходимо сделать его локальную копию на ваш компьютер. Для этого переходим в `< > Code`, затем `SSH` и копируем ключ.

![Хайповая картинка](/git-and-github/images/image-2.png)
![Хайповая картинка](/git-and-github/images/image-3.png)

**Шаг 3.** Выбираем локальную папку для копии репозитория, в нашем случае это папка с именем `los-capibaras`. Открываем её, нажимаем правую кнопку мыши и выбираем `Open GitBash here`.
> *Примечание:* Репозиторий будет скопирован в виде папки, поэтому нет смысла создавать папку под репозиторий самостоятельно.

![Хайповая картинка](/git-and-github/images/image-4.png)

**Шаг 4.** В открывшемся окне мы видим следующую строку (у каждого она будет своя): `luneu@LAPTOP-7GUDUPTE MINGW64 /c/GitHub/los-capibaras`.

- Часть до `@` указывает имя пользователя, вызвавшего командную строку — `luneu`.
- Часть от `@` до пробела указывает имя устройства, с которого была вызвана командная строка — `LAPTOP-7GUDUPTE`.
- Далее идет указание программного обеспечения, используемого для работы с командной строкой — `MINGW64`.
- Последним указан путь к текущему рабочему каталогу — `/c/GitHub/los-capibaras`.

![Хайповая картинка](/git-and-github/images/image-5.png)

Мы прописываем `git clone` и вставляем скопированную ссылку на SSH ключ репозитория.
> *Примечание:* Копирование из GitBash или вставка в GitBash происходит исключительно через правую кнопку мыши и `Copy` или `Paste` соответственно.

![Хайповая картинка](/git-and-github/images/image-6.png)
![Хайповая картинка](/git-and-github/images/image-7.png)

Можете посмотреть в папку и убедиться, что копирование произошло успешно, так как теперь там появилась копия репозитория на вашем устройстве.

![Хайповая картинка](/git-and-github/images/image-8.png)

**Шаг 5.** В добавленную папку можете внести все изменения. В нашем случае мы добавим две разные картинки. Одна из них находится в файле `Capybara.png`, а вторая в папке `hype-pictures`, в файле `Oppenheimer.png`.

![Хайповая картинка](/git-and-github/images/image-9.png)

**Шаг 6.** Перейдём в нашу новую папку в GitBash через ввод команды ``cd`` и указания нового пути, в нашем случае: `cd /c/GitHub/los-capibaras/Test`.
> *Примечание:* Переход также можно осуществить через повторное открытие GitBash в новой папке (Test в нашем случае).

![Хайповая картинка](/git-and-github/images/image-10.png) 

Можно заметить, что появилось слово после линии `(main)`, оно означает ветку, в которой мы находимся. Для работы с ветками есть 3 основные команды:
- `git checkout -b <название>` - выполняет переход в новосозданную ветку.
- `git checkout <название>` - выполняет переход в указанную ветку.
- `git branch` - показывает список существующих веток.
- `git branch -d <название>` - удаляет выбранную ветку.

![Хайповая картинка](/git-and-github/images/image-11.png)

Теперь мы можем проверить все произведённые изменения через команду `git status`. Напомним, что статус показывает состояние файла в локальной копии репозитория на вашем устройстве относительно репозитория.

![Хайповая картинка](/git-and-github/images/image-12.png)

Всего существует 3 статуса у файлов:
- `Untracked` - это файлы, которые вы добавили в локальный репозиторий, но их ещё не существует в оригинальном репозитории.
- `Modified` - это файлы, которые существуют в оригинальном репозитории, однако были изменены на локальной копии.
- `Deleted` - это файлы, которые были удалены на локальной копии, но существуют в оригинальном репозитории.

В нашем случае показано, что добавлены файл и папка, то есть `Untracked files`.
> *Примечание:* Пустые папки не будут добавлены, покуда в них не появятся файлы.

**Шаг 7.** При работе в команде важно грамотно производить изменения, чтобы все члены команды понимали, что было изменено. При работе с большими файлами одному человеку это также может быть полезно, дабы помнить, чтобы было изменено в прошлый раз в тех или иных местах. Поэтому любые изменения сопровождаются коммитами (комментариями). В соответствии с принятыми стандартами их пишут на латинице в настоящем времени в краткой форме, например: 'Add', 'Update the part with pink button', 'Fix the bag with the button'.

Для того, чтобы добавить файл для коммита, необходимо его добавить через команду `git add <file>` или `git add .`, если вы хотите добавить все изменения сразу (будьте осторожны, ведь добавление всех файлов сразу приведёт к появлению везде одинаковых комментариев).

Заметим, что если файл находится в папке, то путь будет необходимо указать включая её (либо можно открыть GitBash в этой папке и без указания пути добавить файл там). Также папку можно добавить целиком, не указывая конкретный файл.

Для примера добавим картинку `Capybara.png` как отдельный файл через команду `git add Capybara.png` и картинку `Oppenheimer.png` как часть папки `hype-pictures` через команду `git add hype-pictures/Oppenheimer.png`. 
> *Примечание:* Можно было добавить папку целиком через команду `git add hype-pictures/`

![Хайповая картинка](/git-and-github/images/image-13.png)

Можете вновь прописать `git status`, чтобы убедиться, все ли желаемые файлы для изменения были внесены.

Если вы вдруг добавили случайно не тот файл, то можете прописать `git reset`, тем самым скинуть все добавления и заново добавить нужные файлы.

![Хайповая картинка](/git-and-github/images/image-14.png)

**Шаг 8.** Теперь необходимо добавить сам комментарий через команду `git commit -m 'TEXT'`, -m кратко обозначает messege (сообщение).

![Хайповая картинка](/git-and-github/images/image-15.png)

Стоит отметить, что после отправки коммита нам возвращается сообщение с описанием количества добавленных и убранных строк. Так как у нас была картинка, то оба значения равны нулю.

**Шаг 9.** После того, как все изменения будут закоммичены, необходимо будет закинуть все коммиты с локальной копии репозитория в сам репозиторий через команду `git push`. В случае, если вы делали изменения не в основной ветке, то необходимо будет указать путь: `git push <удалённый репозиторий> <локальная ветка>:<удалённая ветка>`.
- <удалённый репозиторий> - это обычно название удалённого репозитория, например, origin.
- <локальная ветка> - это название вашей локальной ветки, которую вы хотите отправить на удалённый репозиторий.
- <удалённая ветка> - это название ветки на удалённом репозитории, в которую вы хотите отправить изменения.

Так как мы производили изменения в основной ветке и туда же отправляем, а по умолчанию у команды `git push` стоит `git push origin main:main`, то можно ввести просто `git push`.

![Хайповая картинка](/git-and-github/images/image-16.png)

Всё было успешно добавлено, можем проверять удалённый репозиторий на гитхабе.
![Хайповая картинка](/git-and-github/images/image-17.png)
