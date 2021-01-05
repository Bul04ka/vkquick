После того, как вы создали нового бота командой `$ bot new <name>`, в директории, в которой была вызвана эта команда, появится папка с именем бота

```
├── LICENSE
├── README.md
├── config.toml
└── src
    └── __init__.py
```

### `LICENSE`
Обычный текстовый файл с [MIT лицензией](https://ru.wikipedia.org/wiki/Лицензия_MIT). И вы, как полноценный правообладатель своего бота, можете вписать туда свое имя

!!! Tip
    Правообладателя можно указать сразу при создании бота (через `new`) флагом `-o`, тобишь `$ bot new mybot -o "Pavel Durov"`

### `README.md`
Классика любого проекта. Добавляйте сюда информацию о своем боте, причем как по использованию, так и для контрибьютерства (разработки). Однако, для второго можно создать отдельный файл `CONTRIBUTING.md`

### `src/`
Здесь содержится абсолютно весь код. Файлы распределяются по именам и расположению (или должны распределяться) следующим образом (т.е. по стилю)

|Тип|Способ|
|||
|Команда (reaction)| Папка с именем команды (создается через `$ bot com`)|
|Сигнал (signal)| Файл с именем сигнала (создается через `$ bot signal`)|
|Валидатор или аннотационный тип| Файл с именем валидатора/аннотипа|
|Свои файлы| Файл, начинающийся с нижнего подчеркивания|

!!! todo
    Скорее всего структура `src` поменяется на более строгую, где будет конкретное разделение содержимого. Но все зависит от того, насколько будет сложно поддерживать проект по нынешнему стилю. Возможно, это излишки

!!! todo
    Для кастомных валидаторов и аннотационных типов будут свои команды в `bot`. Достаточно удобные и с возможностью моментального применения на какой-либо команде

### `config.toml`
В нем располагаются абсолютно все настройки вашего бота, начиная токеном, заканчивая фильтром дебага

Возможные значения для каждого поля
=== "[api]"
    Поле|Тип содержимого|Значение
    :-|:-:|:-
     __token__ |str|Access token, чей владелец имеет требуемые права работы с API, либо же токен самого сообщества. Можно указать сразу через флаг `-t` в `$ bot new`
    __group_id__ |int|ID группы, от лица которого будет работать бот. Можно сразу указать это поле при создании бота через флаг `-gi`
    __version__ |float/str|Версия используемого API. Должна быть выше `5.103`
    __owner__ |`group`/`user`|Тип владельца токена — группа или пользователь (определяет задержку между запросами)
    __URL__ |str|URL для API запросов. По умолчанию `https://api.vk.com/method/`

=== "[longpoll]"
    Поле|Тип содержимого|Значение
    -|-|:
    __wait__ |int|Время максимального ожидания между ответами LongPoll сервера (в секундах)

!!! Tip
    Узнать ID группы можно [здесь](https://regvk.com/id/)

!!! Tip
    Подробнее о [TOML файлах](https://github.com/toml-lang/toml)

!!! todo
    В будущем планируется добавить возможность выбора формата конфига.