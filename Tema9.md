# Тема 9. ООП на Python: концепции, принципы и примеры реализации
Отчёт по теме выполнил:
  - Плашкин Денис Владимирович 
  - ИВТ-22-2

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | - | 
| Задание 3 | + | - | 
| Задание 4 | + | - |
| Задание 5 | + | - | 
| Задание 6 | - | - | 
| Задание 7 | - | - | 
| Задание 8 | - | - | 
| Задание 9 | - | - | 
| Задание 10 | - | - | 

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторные задания:

### №1. 
Допустим, что вы решили оригинально и немного странно познакомится с человеком. Для этого у вас должен быть написан свой класс на Python, который будет проверять угадал ваше имя человек или нет. Для этого создайте класс, указав в свойствах только имя. Дальше создайте функцию __init__(), а в ней сделайте проверку на то угадал человек ваше имя или нет. Также можете проверить что будет, если в этой функцию __init__(), а в ней сделайте проверку на то угадал человек ваше имя или нет. Также можете проверить что будет, если в этой функции указав атрибут, который не указан в вашем классе, например, попробуйте вызвать фамилию.
### Ответ: 
```python
class Ivan:
    __slots__ = ['name']

    def __init__(self, name):
        if name == 'Иван':
            self.name = f"Да, я {name}"
        else:
            self.name = f"Я не {name}, a Иван"

person1 = Ivan('Алексей')
person2 = Ivan('Иван')
print(person1.name)
print(person2.name)

person1.surname = 'Петров'
```
![Меню](https://github.com/Asappich/main/blob/Tema9/pic/1.jpg)

### Вывод: 


### №2. 
Вам дали важное задание, написать продавцу мороженого программу, которая будет писать добавили ли топпинг в мороженое и цену после возможного изменения. Для этого вам нужно написать класс, в котором будет определяться изменили ли состав мороженого или нет. В этом классе реализуйте метод, выводящий на печать «Мороженое с {ТОППИНГ}» в случае наличия добавки, а иначе отобразится следующая фраза: «Обычное мороженое». При этом программа должна воспринимать как топпинг только атрибуты типа string.
### Ответ: 
```python
class Icecream:
    def __init__(self, ingreduent=None):
        if isinstance(ingreduent, str):
            self.ingredient = ingreduent
        else:
            self.ingredient = None

    def composition(self):
        if self.ingredient:
            print(f"Мороженное с {self.ingredient}")
        else:
            print("Обычное мороженное")

icecream = Icecream()
icecream.composition()
icecream = Icecream('шоколадом')
icecream.composition()
icecream = Icecream(5)
icecream.composition()
```
![Меню](https://github.com/Asappich/main/blob/Tema9/pic/2.jpg)

### Вывод: 


### №3. 
Петя – начинающий программист и на занятиях ему сказали реализовать икапсу…что-то. А вы хороший друг Пети и ко всему прочему прекрасно знаете, что икапсу…что-то – это инкапсуляция, поэтому решаете помочь вашему другу с написанием класса с инкапсуляцией. Ваш класс будет не просто инкапсуляцией, а классом с сеттером, геттером и деструктором. После написания класса вам необходимо продемонстрировать что все написанные вами функции работают. Также вас необходимо объяснить Пете почему на скриншоте ниже в консоли выводится ошибка.
### Ответ: 
```python
class MyClass:
    def __init__(self, value):
        self._value = value

    def set_value(self, value):
        self._value = value

    def get_value(self):
        return self._value
    
    def del_value(self):
        del self._value

    value = property(get_value, set_value, del_value, "Свойство value")

obj = MyClass(42)
print(obj.get_value())
obj.set_value(45)
print(obj.get_value())
obj.set_value(100)
print(obj.get_value())
obj.del_value()
print(obj.get_value())
```
![Меню](https://github.com/Asappich/main/blob/Tema9/pic/3.jpg)

### Вывод: 


### №4. 
Вам прекрасно известно, что кошки и собаки являются млекопитающими, но компьютер этого не понимает, поэтому вам нужно написать три класса: Кошки, Собаки, Млекопитающие. И при помощи “наследования” объяснить компьютеру что кошки и собаки – это млекопитающие. Также добавьте какой-нибудь свой атрибут для кошек и собак, чтобы показать, что они чем-то отличаются друг от друга.
### Ответ: 
```python
class Mammal:
    className = 'Mammal'

class Dog(Mammal):
    species = 'canine'
    sounds = 'wow'

class Cat(Mammal):
    species = 'feline'
    sounds = 'meow'

dog = Dog()
print(f"Dog is {dog.className}, but they say {dog.sounds}")
cat = Cat()
print(f"Cat is {cat.className}, but they say {cat.sounds}")
```
![Меню](https://github.com/Asappich/main/blob/Tema9/pic/4.jpg)

### Вывод: 


### №5. 
На разных языках здороваются по-разному, но суть остается одинаковой, люди друг с другом здороваются. Давайте вместе с вами реализуем программу с полиморфизмом, которая будет описывать всю суть первого предложения задачи. Для этого мы можем выбрать два языка, например, русский и английский и написать для них отдельные классы, в которых будет в виде атрибута слово, которым здороваются на этих языках. А также напишем функцию, которая будет выводить информацию о том, как на этих языках здороваются. Заметьте, что для решения поставленной задачи мы использовали декоратор @staticmethod, поскольку нам не нужны обязательные параметры-ссылки вроде self.
### Ответ: 
```python
class Russian:
    @staticmethod
    def greeting():
        print("Привет")

class English:
    @staticmethod
    def greeting():
        print("Hello")

def greet(language):
    language.greeting()

ivan = Russian()
greet(ivan)
john = English()
greet(john)
```
![Меню](https://github.com/Asappich/main/blob/Tema9/pic/5.jpg)

### Вывод: 


## Самостоятельные задания:

### №1. 
Задание Садовник и помидоры.
### Ответ: 
```python
class Tomato:
    
    states = {'Отсутствует': 0, 'Цветение': 1, 'Зеленый': 2, 'Красный': 3}
    
    def __init__(self, index):
        self._index = index
        self._state = self.states['Отсутствует']
        
    def grow(self):
        if self._state < 3:
            self._state += 1
        
    def is_ripe(self):
        return True if self._state == 3 else False
 
class TomatoBush:
    
    def __init__(self, num):
        self.tomatoes = [Tomato(index) for index in range(1, num+1)]
        
    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()
            
    def all_are_ripe(self):
        return all([tomato.is_ripe() for tomato in self.tomatoes])
    
    def give_away_all(self):
        self.tomatoes = []
 
class Gardener:
    
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant
        
    def work(self):
        self._plant.grow_all()
        
    def harvest(self):
        if self._plant.all_are_ripe():
            print('Урожай собран!')
            self._plant.give_away_all()
        else:
            print('Томаты еще не дозрели')
            
    @staticmethod
    def knowledge_base():
        print('Справка по садоводству:')
        print('1. Не забывайте регулярно поливать и подкармливать растения')
        print('2. Определите правильное расстояние между растениями, чтобы они не мешали друг другу в росте')
        print('3. Удалите поврежденные листья и плоды, чтобы предотвратить распространение болезней')
        
# ТЕСТ1.Вызов справки по садоводству
Gardener.knowledge_base()
 
# ТЕСТ2.Создание объектов классов TomatoBush и Gardener
bush = TomatoBush(5)
gardener = Gardener('John', bush)
 
# ТЕСТ3.Уход за кустом с помидорами
gardener.work()
gardener.work()
gardener.work()
 
# ТЕСТ4.Сбор урожая
gardener.harvest()
 
# Продолжение ухода за кустом, пока томаты не дозреют
gardener.work()
gardener.harvest()
gardener.work()
gardener.harvest()
gardener.work()
gardener.harvest()

# ТЕСТ5.Сбор урожая после дозревания всех томатов
gardener.work()
gardener.harvest()
```
![тест1](https://github.com/Asappich/main/blob/Tema9/pic/1s.jpg)
![тест2](https://github.com/Asappich/main/blob/Tema9/pic/2s.jpg)
![тест3](https://github.com/Asappich/main/blob/Tema9/pic/3s.jpg)
![тест4](https://github.com/Asappich/main/blob/Tema9/pic/4s.jpg)
![тест5](https://github.com/Asappich/main/blob/Tema9/pic/5s.jpg)

### Вывод: 


# Общий вывод по теме:
Объектно-ориентированное программирование (ООП) — это мощный подход к разработке программного обеспечения, основанный на работе с объектами, являющимися экземплярами классов. Основные принципы ООП включают:
  1. Классы и объекты: Классы выступают в качестве шаблонов для создания объектов, определяющих их структуру и функции.
  2. Атрибуты и методы: Атрибуты описывают состояние объекта, а методы определяют его поведение.
  3. Наследование: Позволяет создавать новые классы на базе уже существующих, что упрощает повторное использование кода и помогает строить иерархии классов.
  4. Инкапсуляция: Скрывает внутренние механизмы работы класса, обеспечивая контроль над доступом к его элементам.
  5. Полиморфизм: Разрешает объектам разных классов использовать одинаковый интерфейс, реагируя на одни и те же операции различным образом.
ООП способствует созданию структурированного, гибкого и легко поддерживаемого кода. Разработчики могут сосредотачиваться на моделировании объектов и их взаимодействий, игнорируя детали реализации. Это повышает качество архитектуры программных систем, облегчая их сопровождение и расширение.
