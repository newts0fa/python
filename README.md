# Calculator Package

Базовый калькулятор на языке Python, позволяющий делать базовые и расширенные математические операции.

## Установка

```bash
pip install calculator-pkg-newts0fa
```

## Использование

```python
from calculator.basic import add, subtract
from calculator.advanced import power, square_root

print(add(2, 3))             # Вывод: 5
print(subtract(5, 2))        # Вывод: 3
print(power(2, 3))           # Вывод: 8
print(square_root(16))       # Вывод: 4.0
```
## Лицензия

Без лицензии

Задания:
1. Исследование структуры пакета
а. Дополните схему дерева файлов и модулей пакета calculator, указав, какие модули и функции в них содержатся.

calculator/
├── __init__.py
├── basic/
│   ├── __init__.py
│   ├── addition.py
      function: add()
│   └── subtraction.py
      function: subtract()
└── advanced/
    ├── __init__.py
    ├── exponentiation.py
          function: exponentiate()
    └── root.py
          function: root()

б. Объясните, какую роль играют файлы __init__.py в каждом каталоге пакета. Почему без них пакет не будет работать правильно?

В каждом каталоге пакета играют важную роль в определении структуры пакета и обеспечении его правильной работы.

2. Работа с __init__.py
а. Обратите внимание на использование переменной __all__ в файле calculator/__init__.py. Объясните, как она влияет на импорт пакета.

Переменная all в файле init.py используется для явного указания того, какие модули, функции или классы должны быть доступны при использовании конструкции from package import *. Это позволяет контролировать, что именно будет импортировано из пакета, если кто то решит использовать такой импорт, а так же улучшает читаемость и поддержку кода, предоставляя разработчикам четкое представление о публчиных интерфейсах пакета

б. Удалите или закомментируйте строку __all__ = ["basic", "advanced"] в файле calculator/__init__.py. Попробуйте импортировать пакет снова:


from calculator import basic
     
Что произошло? Объясните причину возникшей проблемы.

Будут импортированы все модули , находящиеся в пакете calculator, включая все подкаталоги и файлы, которые являются модулями. Это включает и те файлы, которые могут быть предназначены только для внутреннего использования. В частности, если в пакете есть скрытые модули, они тоже могут быть импортированы если не определна переменная all

в. Верните строку __all__ обратно. Попробуйте выполнить команду:


from calculator import *
     
Какие модули будут импортированы? Как можно управлять импортируемыми модулями с помощью __all__?

Если вернуть all, структура пакета снова будет ограничена только модулями, указанными в all . Это даст возможность контролировать, какие части пакета будут доступны при импорте с использованием from calculator import *

3. Абсолютный и относительный импорт
а. В файле calculator/basic/__init__.py замените относительные импорты на абсолютные:


from calculator.basic.addition import add
from calculator.basic.subtraction import subtract
     
Проверьте работоспособность пакета. Объясните разницу между относительным и абсолютным импортом. Какие преимущества и недостатки каждого из них?

1. Относительные импорты в Python начинаются с точки (. или ..), чтобы указать на текущий каталог или его родительские каталоги. Это обычно используется внутри пакета, чтобы упростить импорт в пределах того же пакета. 2. Абсолютные импорты указывают на полный путь к модулю, начиная от корня проекта. В случае с абсолютными импортами мы точно указываем путь от главного пакета, как в примере выше — from calculator.basic.addition import add.

б. Предположим, что структура пакета изменилась, и папка basic была переименована в simple. Объясните, как это повлияет на абсолютные и относительные импорты. Какой импорт легче поддерживать при реорганизации структуры пакета?

:Если структура проекта меняется часто, относительные импорты могут быть предпочтительнее, поскольку они менее чувствительны к таким изменениям. Однако для внешнего взаимодействия или работы с большими проектами абсолютные импорты предпочтительнее из-за их прозрачности и ясности.

4. Добавление новых модулей
а. Добавьте в пакет calculator/basic новый модуль multiplication.py с функцией multiply(a, b), которая возвращает произведение a и b.

Ваш ответ (кликните два раза на эту ячейку, удалите содержимое и впишите ответ)

б. Обновите файл calculator/basic/__init__.py, чтобы функция multiply была доступна при импорте пакета.

Ваш ответ (кликните два раза на эту ячейку, удалите содержимое и впишите ответ)

в. В файле main.py импортируйте новую функцию и протестируйте ее.


from calculator.basic import multiply

print(multiply(4, 5))        # Вывод: 20
     
Ваш ответ (кликните два раза на эту ячейку, удалите содержимое и впишите ответ)

5. Исследование переменной __name__
а. В файле calculator/advanced/exponentiation.py добавьте следующий код:


if __name__ == "__main__":
    print(power(2, 5))
     
б. Запустите файл exponentiation.py напрямую. Что произошло? Какой вывод вы получили?

Если запустить файл exponentiation.py напрямую, переменнаяvanced/expбудет установлена в "main", так как это главный исполняемый файл. • Условие ifexponentia== "main": будет истинным, и код внутри блока выполнится. В частности, вызовется функция power(2, 5), и результат (32) будет выведен в консоль. Ожидаемый результат : 32

в. Импортируйте функцию power в main.py и запустите main.py. Выполняется ли код внутри блока if __name__ == "__main__": в файле exponentiation.py при импорте? Объясните, почему.

Если импортировать модуль (в данном случае, exponentiation.py) в другой файл, Python присваивает переменной name значение, которое соответствует имени модуля (то есть calculator.advanced.exponentiation). • Следовательно, проверка if name == "main": не будет выполнена, потому чтоление кодав данном случае не равно "main". Это означает, что код внутри блока ifadvanced/e== "main": не выполнится при импорте. if name == "main": — этот блок кода выполняется только в том случае, если файл выполняется напрямую как главный скрипт. Когда файл импортируется как модуль, переменная name будет содержать имя модуля, а не "main", и код внутри блока не выполнится.

6. Изучение путей поиска модулей
а. Выведите переменную sys.path в main.py:


import sys
print(sys.path)
     
Объясните, какие пути в ней содержатся и как Python использует их для поиска модулей.

Переменная sys.path — это список строк, каждая из которых представляет собой путь, который Python использует для поиска модулей и пакетов при импорте. Когда вы пытаетесь импортировать модуль, Python проверяет каждый путь из списка sys.path в порядке их следования, начиная с первого

б. Попробуйте переместить папку calculator в другую директорию, которая не входит в sys.path. Можете ли вы теперь импортировать пакет? Что нужно сделать, чтобы Python мог найти ваш пакет?

Это происходит потому, что папка calculator теперь находится в другом месте, и Python не может найти её в стандартных путях поиска. Вы можете добавить новый путь к папке calculator в список sys.path Использовать переменную окружения PYTHONPATH

7. Создание подпакетов
а. Внутри calculator/advanced создайте подпакет trigonometry с функциями sin, cos и tan. Структура должна выглядеть так:


calculator/
└── advanced/
    ├── trigonometry/
            tangent.py
            cosine.py
            sine.py
    │   ├── __init__.py
    │   ├── sine.py
    │   ├── cosine.py
    │   └── tangent.py
     
б. Реализуйте функции в соответствующих модулях, используя модуль math из стандартной библиотеки Python.

в. Обновите __init__.py файлы, чтобы обеспечить корректный импорт функций.

г. Импортируйте функции в main.py и протестируйте их.

8. Практика с относительным импортом
а. В файле calculator/advanced/trigonometry/sine.py попробуйте импортировать функцию square_root из модуля root.py двумя способами:

Используя относительный импорт.
Используя абсолютный импорт.
б. Объясните, какой способ импорта сработал, а какой нет, и почему.

Относительный импорт работает только в контексте пакета, когда модуль sine.py не запускается напрямую. Он будет искать родительский модуль или пакет. • Абсолютный импорт всегда работает, так как Python ищет модуль по полному пути от корня проекта.

Чтобы относительный импорт работал корректно, нужно запускать скрипт как часть пакета, а не как самостоятельный файл. Например, вместо того чтобы запускать sine.py напрямую, лучше запускать проект с корня через команду:
