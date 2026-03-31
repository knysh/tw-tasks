# Задание: оператор `??` в TypeScript

**Тема:** Nullish coalescing operator (`??`)  

## Условие

Напиши функцию обработки настроек пользователя. 
1. Создать файл `task-nullish.ts`
2. Реализовать функцию обработки настроек processUserSettings

## Дано 

Сигнатура входящих параметров: 

```ts

// тип входящих настроек
type UserSettings = {
  theme?: string | null;
  pageSize?: number | null;
  showHints?: boolean | null;
  nickname?: string | null;
};

// тип результата, который должна возвращать функция
type Result = {
  theme: string;
  pageSize: number;
  showHints: boolean;
  nickname: string;
};

// объект с настройками по умолчанию
const defaultUserSettings: Result = {
  theme: 'dark';
  pageSize: 5;
  showHints: false;
  nickname: 'Guest';
};

export function processUserSettings(settings: UserSettings): Result {
  // обработать каждое значение внутри settings, вернуть значение по умолчанию для каждого отсутствующего значения
```

## Тестовые данные (ожидаемый результат)

Проверь через `console.log` такие кейсы:

1. Пустой объект:
   - вход: `{}`
   - результат: `{ theme: 'dark', pageSize: 5, showHints: false, nickname: 'Guest' }`

2. Все поля заданы явно:
   - вход: `{ theme: 'light', pageSize: 20, showHints: true, nickname: 'Alex' }`
   - результат: `{ theme: 'light', pageSize: 20, showHints: true, nickname: 'Alex' }`

3. Значения `null` заменяются на дефолтные:
   - вход: `{ theme: null, pageSize: null, showHints: null, nickname: null }`
   - результат: `{ theme: 'dark', pageSize: 5, showHints: false, nickname: 'Guest' }`

4. Значения `undefined` заменяются на дефолтные:
   - вход: `{ theme: undefined, pageSize: undefined, showHints: undefined, nickname: undefined }`
   - результат: `{ theme: 'dark', pageSize: 5, showHints: false, nickname: 'Guest' }`

5. "Ложные" значения не должны заменяться (проверка отличия `??` от `||`):
   - вход: `{ theme: '', pageSize: 0, showHints: false, nickname: '' }`
   - результат: `{ theme: '', pageSize: 0, showHints: false, nickname: '' }`

6. Смешанный кейс:
   - вход: `{ theme: null, pageSize: 0, showHints: undefined, nickname: 'Neo' }`
   - результат: `{ theme: 'dark', pageSize: 0, showHints: false, nickname: 'Neo' }`

