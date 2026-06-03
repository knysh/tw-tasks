Задание 1. «Модель тест-кейса и репозиторий» 

Условие
Нужно описать сущность тест-кейс и сервис, который с ними работает.

Класс TestCase:

поля: id (строка), title, steps (массив строк), priority ('low' | 'medium' | 'high'), isAutomated (boolean);
в конструкторе — валидация: title не пустой, иначе throw new Error('...');
методы:
markAutomated() — isAutomated = true;
getSummary() — строка вида: "[high] Название (3 шага, automated)".

Класс TestCaseRepository:
поля: testCase - массив TestCases

массив кейсов;
create(testCase) — сохранить, если id уникален, иначе ошибка;
getTestCases() - возврат значения testCase 


Скрипт main (или тесты в node без фреймворка):

создать 3 кейса разного приоритета;
вывести в консоль getTestCases() у которых приоритет high 
вывести в консоль getTestCases() у которых приоритет medium 
вывести в консоль getTestCases() у которых приоритет low 
