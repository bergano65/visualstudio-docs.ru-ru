---
title: Соглашения о форматировании EditorConfig на C++
titleSuffix: ''
description: Узнайте, как использовать EditorConfig для форматирования кода C++ в Visual Studio.
ms.date: 9/14/2020
author: jureid
ms.author: jureid
manager: jmartens
dev_langs:
- CPP
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: reference
ms.workload:
- cplusplus
monikerRange: vs-2019
ms.openlocfilehash: 490a7b29d6e3d8a2dc63c27b9e9d7226b5d22662
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970885"
---
# <a name="c-editorconfig-formatting-conventions"></a>Соглашения о форматировании EditorConfig на C++

Форматировщик C++ Visual Studio имеет обширный набор настраиваемых параметров, которые можно применять глобально. Чтобы задать параметры форматирования C++ для конкретной рабочей области, используйте [clangformat](https://clang.llvm.org/docs/ClangFormat.html) или [EditorConfig](https://editorconfig.org/). Visual Studio и Visual Studio Code имеют встроенную поддержку EditorConfig для каждого из глобальных параметров форматирования C++ Visual Studio. При этом параметры EditorConfig имеют приоритет. Это означает, что вы можете добавить файлы EditorConfig в рабочую область, чтобы настроить форматирование C++ на более детальном уровне и применить согласованный стиль кода для всех пользователей, участвующих в проекте.

## <a name="c-formatting-conventions"></a>Соглашения о форматировании C++

Параметры EditorConfig форматирования C++ имеют префикс `cpp_`. Ниже приведен пример файла EditorConfig.

```ini
[*.{c++,cc,cpp,cxx,h,h++,hh,hpp,hxx,inl,ipp,tlh,tli}]

cpp_indent_case_contents_when_block = true
cpp_new_line_before_open_brace_namespace = same_line
```

В оставшейся части этого документа перечислены все параметры форматирования EditorConfig C++, поддерживаемые Visual Studio и VS Code.

### <a name="indentation-settings"></a>Параметры отступов

**Отступ для фигурных скобок**

- Имя: `cpp_indent_braces`
- Значения: `true`, `false`

**Отступ каждой строки относительно**

- Имя: `cpp_indent_multi_line_relative_to`
- Значения:
  - `outermost_parenthesis` — при вводе новой строки делается отступ относительно внешней открывающей скобки.
  - `innermost_parenthesis` — при вводе новой строки делается отступ относительно внутренней открывающей скобки.
  - `statement_begin` — при вводе новой строки делается отступ относительно начала текущего оператора.

**Внутри скобок выравнивать новые строки во время их ввода**

- Имя: `cpp_indent_within_parentheses`
- Значения:
  - `align_to_parenthesis` — выравнивать содержимое по открывающим скобкам.
  - `indent` — отступ для новых строк.

**В имеющемся коде нельзя использовать параметры выравнивания новых строк внутри скобок**

- Имя: `cpp_indent_preserve_within_parentheses`
- Значения: `true`, `false`

**Отступ в конструкции case**

- Имя: `cpp_indent_case_contents`
- Значения: `true`, `false`

**Отступ заголовков конструкции case**

- Имя: `cpp_indent_case_labels`
- Значения: `true`, `false`

**Отступ для скобок перед оператором case**

- Имя: `cpp_indent_case_contents_when_block`
- Значения: `true`, `false`

**Отступ фигурных скобок лямбда-выражений, используемых в качестве параметров**

- Имя: `cpp_indent_lambda_braces_when_parameter`
- Значения: `true`, `false`

**Положение меток Goto**

- Имя: `cpp_indent_goto_labels`
- Значения:
  - `one_left` — один отступ слева
  - `leftmost_column` — переместить в самый левый столбец
  - `none` — оставить с отступом

**Позиция директив препроцессора**

- Имя: `cpp_indent_preprocessor`
- Значения:
  - `one_left` — один отступ слева
  - `leftmost_column` — переместить в самый левый столбец
  - `none` — оставить с отступом

**Отступ спецификаторов доступа**

- Имя: `cpp_indent_access_specifiers`
- Значения: `true`, `false`

**Отступ перед блоком пространства имен**

- Имя: `cpp_indent_namespace_contents`
- Значения: `true`, `false`

**Сохранить отступы комментариев**

- Имя: `cpp_indent_preserve_comments`
- Значения: `true`, `false`

### <a name="newline-settings"></a>Параметры новой строки

**Положение открывающих фигурных скобок пространств имен**

- Имя: `cpp_new_line_before_open_brace_namespace`
- Значения:
  - `new_line` — перемещать на новую строку
  - `same_line` — оставлять на той же строке, но добавлять пробел перед скобкой
  - `ignore` — не изменять положение автоматически

**Положение открывающих фигурных скобок типов**

- Имя: `cpp_new_line_before_open_brace_type`
- Значения:
  - `new_line` — перемещать на новую строку
  - `same_line` — оставлять на той же строке, но добавлять пробел перед скобкой
  - `ignore` — не изменять положение автоматически

**Положение открывающих фигурных скобок функций**

- Имя: `cpp_new_line_before_open_brace_function`
- Значения:
  - `new_line` — перемещать на новую строку
  - `same_line` — оставлять на той же строке, но добавлять пробел перед скобкой
  - `ignore` — не изменять положение автоматически

**Положение открывающих фигурных скобок управляющих блоков**

- Имя: `cpp_new_line_before_open_brace_block`
- Значения:
  - `new_line` — перемещать на новую строку
  - `same_line` — оставлять на той же строке, но добавлять пробел перед скобкой
  - `ignore` — не изменять положение автоматически

**Положение открывающих фигурных скобок лямбда-выражений**

- Имя: `cpp_new_line_before_open_brace_lambda`
- Значения:
  - `new_line` — перемещать на новую строку
  - `same_line` — оставлять на той же строке, но добавлять пробел перед скобкой
  - `ignore` — не изменять положение автоматически
 
**Поместить скобки на отдельные строки**

- Имя: `cpp_new_line_scope_braces_on_separate_lines`
- Значения: `true`, `false`

**Для пустых типов перемещать закрывающую фигурную скобку в ту же строку, где находится открывающая скобка**

- Имя: `cpp_new_line_close_brace_same_line_empty_type`
- Значения: `true`, `false`

**Для функций с пустым телом перемещать закрывающую фигурную скобку в ту же строку, где находится открывающая скобка**

- Имя: `cpp_new_line_close_brace_same_line_empty_function`
- Значения: `true`, `false`

**Помещать ключевое слово catch и аналогичные ключевые слова на новую строку**

- Имя: `cpp_new_line_before_catch`
- Значения: `true`, `false`

**Помещать ключевое слово else на новую строку**

- Имя: `cpp_new_line_before_else`
- Значения: `true`, `false`

**Помещать "while" в цикле do-while на новую строку**

- Имя: `cpp_new_line_before_while_in_do_while`
- Значения: `true`, `false`

### <a name="spacing-settings"></a>Параметры интервалов

**Пробелы между именами функций и открывающими скобками списков аргументов**

- Имя: `cpp_space_before_function_open_parenthesis`
- Значения:
  - `insert` — вставить пробел
  - `remove` — удалить пробелы
  - `ignore` — не изменять пробелы

**Вставлять пробел между скобками со списком аргументов**

- Имя `cpp_space_within_parameter_list_parentheses` Значения: `true`, `false`

**Вставлять пробел между скобками с пустым списком аргументов**

- Имя: `cpp_space_between_empty_parameter_list_parentheses`
- Значения: `true`, `false`

**Вставлять пробел между ключевым словом и открывающей скобкой в инструкциях потока управления**

- Имя: `cpp_space_after_keywords_in_control_flow_statements`
- Значения: `true`, `false`

**Вставлять пробел между скобками операторов управления**

- Имя: `cpp_space_within_control_flow_statement_parentheses`
- Значения: `true`, `false`

**Вставлять пробел перед открывающими скобками со списками аргументов лямбда-выражений**

- Имя: `cpp_space_before_lambda_open_parenthesis`
- Значения: `true`, `false`

**Вставлять пробел между скобками в приведениях в стиле C**

- Имя: `cpp_space_within_cast_parentheses`
- Значения: `true`, `false`

**Вставлять пробел после закрывающей скобки приведения в стиле C**

- Имя: `cpp_space_after_cast_close_parenthesis`
- Значения: `true`, `false`

**Вставка пробела внутри скобок в выражении в круглых скобках**

- Имя: `cpp_space_within_expression_parentheses`
- Значения: `true`, `false`

**Вставить пробел перед открывающими скобками блоков**

- Имя: `cpp_space_before_block_open_brace`
- Значения: `true`, `false`

**Вставлять пробел между пустыми фигурными скобками**

- Имя: `cpp_space_between_empty_braces`
- Значения: `true`, `false`

**Вставка пробела перед открывающей фигурной скобкой равномерной инициализации и списков инициализаторов**

- Имя: `cpp_space_before_initializer_list_open_brace`
- Значения: `true`, `false`

**Вставлять пробел между фигурными скобками равномерной инициализации и списков инициализаторов**

- Имя: `cpp_space_within_initializer_list_braces`
- Значения: `true`, `false`

**Сохранить пробелы внутри равномерной инициализации и списков инициализаторов**

- Имя: `cpp_space_preserve_in_initializer_list`
- Значения: `true`, `false`

**Вставлять пробел перед открывающей квадратной скобкой**

- Имя: `cpp_space_before_open_square_bracket`
- Значения: `true`, `false`

**Вставлять пробел между квадратными скобками**

- Имя: `cpp_space_within_square_brackets`
- Значения: `true`, `false`

**Вставлять пробел перед пустыми квадратными скобками**

- Имя: `cpp_space_before_empty_square_brackets`
- Значения: `true`, `false`

**Вставлять пробел между пустыми квадратными скобками**

- Имя: `cpp_space_between_empty_square_brackets`
- Значения: `true`, `false`

**Группировать квадратные скобки многомерных массивов**

- Имя: `cpp_space_group_square_brackets`
- Значения: `true`, `false`

**Вставлять пробел между квадратными скобками для лямбда-выражений**

- Имя: `cpp_space_within_lambda_brackets`
- Значения: `true`, `false`

**SpaceBetweenEmptyLambdaBrackets**

- Имя: `cpp_space_between_empty_lambda_brackets`
- Значения: `true`, `false`

**Вставлять пробел перед запятой**

- Имя: `cpp_space_before_comma`
- Значения: `true`, `false`

**Вставлять пробелы после запятых**

- Имя: `cpp_space_after_comma`
- Значения: `true`, `false`

**Удалять пробелы до и после операторов членов**

- Имя: `cpp_space_remove_around_member_operators`
- Значения: `true`, `false`

**Вставлять пробел перед двоеточием для базового типа в объявлениях типов**

- Имя: `cpp_space_before_inheritance_colon`
- Значения: `true`, `false`

**Вставка пробела перед двоеточием для конструкторов**

- Имя: `cpp_space_before_constructor_colon`
- Значения: `true`, `false`

**Удалять пробелы перед точкой с запятой**

- Имя: `cpp_space_remove_before_semicolon`
- Значения: `true`, `false`

**Вставлять пробел после точки с запятой**

- Имя: `cpp_space_after_semicolon`
- Значения: `true`, `false`

**Удалять пробелы между унарными операторами и их операндами**

- Имя: `cpp_space_remove_around_unary_operator`
- Значения: `true`, `false`

**Пробелы для бинарных операторов**

- Имя: `cpp_space_around_binary_operator`
- Значения:
  - `insert` — вставлять пробелы до и после бинарных операторов.
  - `remove` — удалять пробелы вокруг бинарных операторов.
  - `ignore` — не изменять пробелы вокруг бинарных операторов.

**Пробелы для операторов присваивания**

- Имя: `cpp_space_around_assignment_operator`
- Значения:
  - `insert` — вставлять пробелы вокруг операторов назначения.
  - `remove` — удалять пробелы вокруг операторов назначения.
  - `ignore` — не изменять пробелы вокруг операторов назначения.

**Выравнивание указателей/ссылок**

- Имя: `cpp_space_pointer_reference_alignment`
- Значения:
  - `left` — выровнять по левому краю.
  - `center` — выровнять по центру.
  - `right` — выровнять по правому краю.
  - `ignore` — оставить без изменений.

**Пробелы для условных операторов**

- Имя: `cpp_space_around_ternary_operator`
- Значения:
  - `insert` — вставлять пробелы вокруг условных операторов.
  - `remove` — удалять пробелы вокруг условных операторов.
  - `ignore` — не изменять пробелы вокруг условных операторов.

### <a name="wrapping-options"></a>Параметры переноса

**Параметры переноса по блокам**

- Имя: `cpp_wrap_preserve_blocks`
- Значения:
  - `one_liners` — не переносить однострочные блоки кода.
  - `all_one_line_scopes` — не переносить по строкам блоки кода, если открывающая и закрывающая фигурные скобки находятся на одной строке.
  - `never` — всегда применять параметры перехода на новую строку к блокам.

## <a name="see-also"></a>См. также

- [EditorConfig.org](https://editorconfig.org/)
- [Поддержка EditorConfig для языковой службы](../extensibility/supporting-editorconfig.md)
- [Возможности редактора кода](writing-code-in-the-code-and-text-editor.md)
