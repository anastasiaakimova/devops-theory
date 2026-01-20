# How to use simple bash scripting (variables, conditions & tests, grep, awk, sed)

Bash (short for "Bourne Again SHell") is an interactive command interpreter and scripting language developed for Unix-like operating systems

## Creating simple script

1. Create a file:
`nano hello.sh` <br>
Content: <br>
`#!/bin/bash` <br>
`echo "Hello, world!"`
2. Make it executable
`chmod +x hello.sh`
3. Start file
`./hello.sh`


`#!/bin/bash` - a shebang - it tells Linux which interpreter to use.

## Variables

A variable is a named location in memory where a string value is stored.<br>
В bash всё — строки, даже числа.

```
NAME="Anastasia"
AGE=25
```

- Нельзя ставить пробелы вокруг `=`

- Имя переменной:

- - только буквы, цифры и `_`

- - не может начинаться с цифры

Использование переменной <br>
`echo $NAME`

или (рекомендуется):

`echo "${NAME}"`

Почему `${}` лучше?

- безопасно

- удобно при конкатенации

`FILE="log"`
`echo "${FILE}_2026.txt"`

Типы переменных
1. Локальные (shell variables)
`CITY="Riga"`


Доступны только в текущем shell или скрипте

2. Переменные окружения (environment variables) <br>
`export ENV="prod"` <br>
или <br>
`ENV="prod"` <br>
`export ENV` <br>

Теперь доступны:

- дочерним процессам

- другим программам

Проверка:

`env | grep ENV`

3. Readonly переменные
`readonly VERSION="1.0"`

Изменить нельзя:

`VERSION="2.0"`  # ошибка

4. Удаление переменной
`unset NAME`

## Arguments

Arguments are the values ​​passed to the script when it is run. <br>
`./script.sh arg1 arg2 arg3`

Специальные positional variables
|Переменная|	Что означает |
|-----|----|
|`$0`|	имя скрипта |
|`$1`|	первый аргумент |
|`$2`|	второй аргумент |
|`$9`|	девятый аргумент |
|`${10}`|	десятый аргумент |
|`$#`|	количество аргументов |
|`$@`|	все аргументы (по отдельности) |
|`$*`|	все аргументы (как одна строка) |

**Пример простого скрипта**

```
#!/bin/bash

echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "Total arguments: $#"
```


## grep, sed, awk
| Команда | Что делает | Примеры применения |
|--------|------------|--------------------|
| `grep` | • Ищет строки по шаблону (текст / regex)<br>• Используется для фильтрации вывода<br>• Не изменяет данные, только показывает | • `grep "error" app.log`<br>• `ps aux \| grep nginx`<br>• `grep -i "warn" file.txt`<br>• `grep -r "TODO"`  |
| `awk` | • Обрабатывает текст построчно<br>• Работает с колонками (полями)<br>• Подходит для анализа и отчётов | • `awk '{print $1}' file.txt`<br>• `awk '{print $1, $3}' file.txt`<br>• `df -h \| awk '{print $1, $5}'`<br>• `awk '$3 > 100 {print $0}' data.txt` |
| `sed` | • Редактирует поток текста<br>• Используется для замены, удаления, вставки строк<br>• Может менять файл или вывод | • `sed 's/error/warn/' file.txt`<br>• `sed 's/error/warn/g' file.txt`<br>• `sed '1d' file.txt`<br>• `sed -i 's/8080/9090/g' config.conf` |


| Command / What it does | How thinks | Bssic syntax  | Examples |
|-------------------|------------|------------------|---------|
|`grep` <br> Ищет строки, содержащие заданный шаблон (текст или regex), <br> и выводит их целиком <br><br> Searches for lines matching a pattern (text or regex). <br> Used to filter output. Does not modify data. | → Читает текст построчно <br> → проверяет каждую строку на совпадение <br>→ если совпало, печатает строку | `grep [опции] "шаблон" файл` | `grep "error" app.log`  – найти строки с `error` <br> `grep -i "error" app.log`  – поиск без учёта регистра  <br> `grep -v "DEBUG" app.log`  – показать все строки, кроме содержащих `DEBUG`  <br> `grep -n "timeout" app.log`  – показать номер строки  <br> `grep -R "listen" /etc/nginx`  – рекурсивный поиск по директории <br> `grep -E "error\|fail\|timeout" app.log` – поиск по нескольким шаблонам |
| `awk` <br> Анализирует и обрабатывает структурированный текст (колонки), <br> может фильтровать, считать, форматировать <br><br> Analyse text line by line and works with columns (fields). Often used for analysis and reports.| → Считает каждую строку записью <br> → разбивает её на поля <br> → работает с ними как с переменными ($1, $2, $3…) | `awk 'шаблон { действие }' файл` | `awk '{print $1}' file.txt`  – вывести первую колонку <br> `awk '{print $1, $3}' file.txt` – вывести первую и третью колонки  <br> `awk '$3 > 100 {print $1, $3}' data.txt` – фильтрация по значению колонки  <br> `awk -F ':' '{print $1}' /etc/passwd ` – указать разделитель `:`  <br> `awk '{sum += $2} END {print sum}' numbers.txt` – посчитать сумму значений  <br> `awk '{ if ($2 == "ERROR") print $0 }' app.log` – вывести строки с условием |
| `sed` <br> Редактирует текстовый поток: <br> замена, удаление, вставка строк <br><br> Edits text streams: replace, delete, insert lines. <br>Can modify output or files | → Читает строку <br> → применяет правило <br> → выводит результат (по умолчанию без изменения файла) | `sed 'команда' файл` | `sed 's/old/new/' file.txt`  – заменить первое совпадение в строке  <br> `sed 's/old/new/g' file.txt`  – заменить все совпадения  <br> `sed '/DEBUG/d' app.log` – удалить строки с `DEBUG`  <br> `sed '5d' file.txt` – удалить 5-ю строку  <br> `sed -i 's/8080/9090/' nginx.conf` – изменить файл напрямую  <br> `sed 's/[0-9]\\+/NUMBER/g' file.txt ` – заменить все числа словом `NUMBER` |


## How to use set
In Bash, set is a **built-in command used** to **control shell behavior** and **shell options**

`set [options] [--] [arguments]`

- Enables/disables shell options
- Changes how scripts behave
- Helps with debugging and safety

|||
|--|---|
|`set -e`| exit on error <br> Stops the script if any command fails |
|`set -u`| Undefined variables are errors <br>Catches bugs caused by typos or missing env vars. <br> Errors if you use an unset variable <br> ✅ Prevents silent bugs |
|`set -x` | Debug mode (trace) <br> Prints commands before executing them. <br> Shows expanded variables <br> ✅ Great for debugging pipelines and scripts |       
|`set -o pipefail` | Fail on pipeline errors <br> By default, pipelines return the **last command’s exit code.** <br> This option makes the pipeline fail if **any command fails**. <br> Without pipefail → might succeed <br> With pipefail → ❌ fails correctly |

### The recommended safe mode
You’ll see this at the top of many professional scripts: <br>
`set -euo pipefail` <br>
Meaning: 
- `-e` → exit on error
- `-u` → error on unset variables
- `-o pipefail` → detect pipeline failures

#### Turn it off
`set +x`

## If conditions

```
#!/bin/bash

ENV=$1

if [ "$ENV" = "prod" ]; then
  echo "Production deployment"
elif [ "$ENV" = "dev" ]; then
  echo "Development deployment"
else
  echo "Unknown environment"
fi
```
Spaces around [ and ] are mandatory.

Every command returns an exit code:
- 0 → success
- !=0 → failure

## Loops

### For loop
```
for ENV in dev test prod; do
  echo "Deploying to $ENV"
done
```
### While loop
```
COUNT=1
while [ $COUNT -le 3 ]; do
  echo "Run $COUNT"
  COUNT=$((COUNT + 1))
done
```

### Functions

```
deploy() {
  ENV=$1
  echo "Deploying to $ENV"
}

deploy dev
deploy prod
```

## Regular expressions


||**Специальные символы в регулярных выражениях**|
|---|---|
|`^`|  начало строки|
|`$`|  конец строки|
|`.`|  любой символ|
|`*`|  ноль или более повторений|
|`+`|  одно или более повторений|
|`?`|  ноль или одно повторение|
|`[]`|  набор символов (например, [0-9] для цифр)|
|`()`|  группировка|
|`\|`|  логическое "или" (альтернатива)|
|`\`|  экранирование символов|

