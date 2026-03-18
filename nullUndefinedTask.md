## Задание (TypeScript): «Нормализация ника пользователя»

### Цель

На практике закрепить `if/else`, оператор `??` (nullish coalescing) и оператор `||` (logical OR).

Посмотреть что значит nullable параметр

---

## Условие

Напиши функцию `resolveNickname`, которая возвращает отображаемый ник по правилам ниже.

Важно: в решении **обязательно** должны использоваться:

- `**if/else`**
- `**??`**
- `**||`**

---

## Дана сигнатура

```ts
type UserInput = {
  nickname?: string | null
  firstName?: string | null
}

export function resolveNickname(
  input: UserInput,
  fallback: string
): string
```

---

## Правила

1. **Если** `input.nickname` не `null/undefined` -> сделай `trim()` и если результат не пустой → вернуть результат -> **иначе** (пустая строка после trim) → считать ник “невалидным” и просто продолжить обработку
2. Дальше обработай `input.firstName`: если `input.firstName` равно `null` или `undefined` возвращаем пустую строку, для полученного результата сделать `trim()`.
3. Итоговое значение функции формируем след образом:
  - если значение пункта 1  валидно - возвращаем его
  - если значение  2-ого пункта - не пустая строка  - возвращаем его
  - если значения в пункте 1 и 2 не валидно и пустая строка соответственно - возвращаем значение  `fallback`
4. Требования по операторам:
  - `**??`** использовать для обработки `null/undefined`
  - `**||`** использовать для обработки “пустых” значений (например, `""` после `trim()`)

---

## Примеры (ожидаемое поведение)

- `resolveNickname({ nickname: "  Neo  ", firstName: "  Alice " }, "Guest")` → `"Neo Alice"`
- `resolveNickname({ nickname: "  Neo  " }, "Guest")` → `"Neo"`
- `resolveNickname({ nickname: "   ", firstName: "  Alice " }, "Guest")` → `"Alice"`
- `resolveNickname({ nickname: null, firstName: "   " }, "Guest")` → `"Guest"`
- `resolveNickname({}, "Guest")` → `"Guest"`
- `resolveNickname({ nickname: "", firstName: null }, "Guest")` → `"Guest"`

---

Для проверки в файле с заданием вывести в консоль лог все примеры ожидаемого поведения. 