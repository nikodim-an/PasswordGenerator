# PasswordGenerator

#### генератор паролей для Linux

------

#### Что это?

Программа генерации паролей для пользователей системы линукс. Создает пароли со сложностью, которая подходит для всех интернет сервисов, и при этом пароли легко запоминаются. Рассчитана на генерацию паролей на текущий год, по окончании которого пароли (по идее) нужно сменить. В течение календарного года всегда выводит стандартный список паролей.
Если год прошел, а пароли пользователем не сменены, или он, вот молодец (!), вспомнил про сервис которым не пользовался пару лет, то в скрипт можно запустить с параметром (год):
`    ./PGenerator.py 2002`
После чего будут сформированы пароли, действовавшие в 2002 году.

#### Как это?

Работает в терминале, при необходимости (в случае когда введен любой параметр запуска) выводит пароли в папке со скриптом в отдельный файл (или в корневую папку пользователя, если запускается через ссылку)

#### Настройка

Для настройки генератора нужно изменить ключи генерации паролей (хотя можно оставить и такие, я их у себя поменял ))) ). По крайней мере фразу `'Маня зовут Вова я знаю три слова'` - этого уже достаточно, чтобы сгенерировались абсолютно уникальные пароли. Ситуация когда два пользователя введут одинаковый ключ не рассматривается - ее просто не может быть, без предварительной договоренности между ними.

Для большей надежности в словаре 

```python
suffix = {  'Почтовые ящики': 'тут будет пароль дял почтовых ящиков', 
            'Банки':'деньги-деньги', 
          	'Форумы':'форумы, мы-немы', 
            'Торент трекеры':'пароли для скачивания видяшек, музяшек и прочей ерунды',
            'Программирование':'о а тут будет пароль к гитхабу',
            'Библиотеки':'почитать мы любим',
            'Игры':'танки чтоль???',
            'Сыночка':'Пароли дял сервисов любимого сына',
            'Дочечка':'Пароли дял сервисов любимой деченьки',
            'Прочие пароли':'прочие пароли - всякая хрень', 
            'Для оперативной замены «засвеченных»':'Чтобы было на что заменить скомпроментированный пароль'
             }
```

измените значения ключей (они на втором месте)  на совершенно **любые** строки

```python
'тут будет пароль дял почтовых ящиков', 
'деньги-деньги', 
'форумы, мы-немы', 
'пароли для скачивания видяшек, музяшек и прочей ерунды'
...
```

#### Как сделать запуск удобным?

Создать символическую ссылку в бинах (/bin) - в этом случае будет запускаться просто из терминала (например создайте ссылку с именем «пароли», тогда в терминале нужно будет набрать «пароли» и нажать ввод. Примерно так:
`$ пароли`
или
`$ пароли 2019`
Для большей безопасности, например когда к ПК имеет доступ не только владелец - создать ссылку в /sbin. В этом случае скрипт запустится только с командой sudo и указанием пароля.

#### Немного о безопасности

**Никогда и никому не передавайте настроенный скрипт! Никогда! Никому!** Запустив его у себя на машине этот человек получит полную генерацию ваших паролей! Последствия вы, конечно же, понимаете…