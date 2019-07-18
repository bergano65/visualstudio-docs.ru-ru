---
title: Соглашения о форматировании в среде .NET для EditorConfig
ms.date: 06/17/2019
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- formatting conventions [EditorConfig]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3218e819d8f94cf760cdc75d6bfa6d29d0a29568
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67823342"
---
# <a name="formatting-conventions"></a>Соглашения по форматированию

Соглашения о форматировании для EditorConfig в Visual Studio разделяются на две категории:

- [параметры форматирования .NET](#net-formatting-settings);

- [Параметры форматирования C#](#c-formatting-settings)

## <a name="rule-format"></a>Формат правил

Правила для соглашений о форматировании имеют следующий формат:

`rule_name = value`

Для большинства правил вы указываете значение `true` (предпочитать этот стиль) или `value` (не предпочитать этот стиль) для `false`. Для нескольких правил указываются другие значения, например `flush_left` или `before_and_after`, которые описывают порядок применения этих правил. Уровень серьезности указывать не нужно.

## <a name="net-formatting-settings"></a>Параметры форматирования .NET

Правила форматирования в этом разделе относятся к коду C# и Visual Basic.

- [Управление директивами using](#organize-using-directives)
  - dotnet_sort_system_directives_first
  - dotnet_separate_import_directive_groups

### <a name="organize-using-directives"></a>Оптимизация директив Using

Эти правила форматирования относятся к сортировке и отображению директив `using` и инструкций `Imports`.

Пример файла *EDITORCONFIG*:

```ini
# .NET formatting settings
[*.{cs,vb}]
dotnet_sort_system_directives_first = true
dotnet_separate_import_directive_groups = true
```

#### <a name="dotnetsortsystemdirectivesfirst"></a>dotnet\_sort\_system\_directives_first

|||
|-|-|
| **Имя правила** | dotnet_sort_system_directives_first |
| **Применимые языки** | C# и Visual Basic |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — сортировать директивы System.* `using` в алфавитном порядке, располагая их перед всеми остальными директивами using.<br /><br />`false` — не размещать директивы System.* `using` перед другими директивами `using`. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// dotnet_sort_system_directives_first = true
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;

// dotnet_sort_system_directives_first = false
using System.Collections.Generic;
using Octokit;
using System.Threading.Tasks;
```

#### <a name="dotnetseparateimportdirectivegroups"></a>dotnet\_separate\_import\_directive\_groups

|||
|-|-|
| **Имя правила** | dotnet_separate_import_directive_groups |
| **Применимые языки** | C# и Visual Basic |
| **Представленные версии** | Visual Studio 2017 версии 15.5 |
| **Значения** | `true` — поместить пустую строку между группами директив `using`.<br /><br />`false` — не помещать пустую строку между группами директив `using`. |
| **Значение по умолчанию в Visual Studio** | `false` |

Примеры кода:

```csharp
// dotnet_separate_import_directive_groups = true
using System.Collections.Generic;
using System.Threading.Tasks;

using Octokit;

// dotnet_separate_import_directive_groups = false
using System.Collections.Generic;
using System.Threading.Tasks;
using Octokit;
```

## <a name="c-formatting-settings"></a>Параметры форматирования C#

Правила форматирования в этом разделе относятся только к коду C#.

- [Параметры перевода строки](#new-line-options)
  - csharp_new_line_before_open_brace
  - csharp_new_line_before_else
  - csharp_new_line_before_catch
  - csharp_new_line_before_finally
  - csharp_new_line_before_members_in_object_initializers
  - csharp_new_line_before_members_in_anonymous_types
  - csharp_new_line_between_query_expression_clauses
- [Параметры отступа](#indentation-options)
  - csharp_indent_case_contents
  - csharp_indent_switch_labels
  - csharp_indent_labels
- [Параметры интервалов](#spacing-options)
  - csharp_space_after_cast
  - csharp_space_after_keywords_in_control_flow_statements
  - csharp_space_between_method_declaration_parameter_list_parentheses
  - csharp_space_between_method_call_parameter_list_parentheses
  - csharp_space_between_parentheses
  - csharp_space_before_colon_in_inheritance_clause
  - csharp_space_after_colon_in_inheritance_clause
  - csharp_space_around_binary_operators
  - csharp_space_between_method_declaration_empty_parameter_list_parentheses
  - csharp_space_between_method_call_name_and_opening_parenthesis
  - csharp_space_between_method_call_empty_parameter_list_parentheses
  - csharp_space_after_comma
  - csharp_space_after_dot
- [Параметры переноса](#wrap-options)
  - csharp_preserve_single_line_statements
  - csharp_preserve_single_line_blocks

### <a name="new-line-options"></a>Параметры новой строки

Эти правила форматирования относятся использованию новых строк для форматирования кода.

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_new_line_before_open_brace = methods, properties, control_blocks, types
csharp_new_line_before_else = true
csharp_new_line_before_catch = true
csharp_new_line_before_finally = true
csharp_new_line_before_members_in_object_initializers = true
csharp_new_line_before_members_in_anonymous_types = true
csharp_new_line_between_query_expression_clauses = true
```

#### <a name="csharpnewlinebeforeopenbrace"></a>csharp\_new\_line\_before\_open_brace

Это правило определяет, следует ли располагать открывающую фигурную скобку `{` одной строке с предшествующим кодом или на новой строке. Для этого правила укажите **all**, **none** либо один или несколько элементов кода, таких как **methods** или **properties**, для которых следует применять это правило. Если вы указываете несколько элементов кода, разделяйте их запятыми (,).

|||
|-|-|
| **Имя правила** | csharp_new_line_before_open_brace |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `all` — требовать, чтобы фигурные скобки для всех выражений размещались в новой строке (стиль Олмана).<br /><br />`none` — требовать, чтобы фигурные скобки для всех выражений размещались в строке выражения (стиль Кернигана и Ритчи).<br /><br />`accessors`, `anonymous_methods`, `anonymous_types`, `control_blocks`, `events`, `indexers`, `lambdas`, `local_functions`, `methods`, `object_collection_array_initializers`, `properties`, `types` — требовать, чтобы фигурные скобки для указанного элемента кода размещались в новой строке (стиль Олмана). |
| **Значение по умолчанию в Visual Studio** | `all` |

Примеры кода:

```csharp
// csharp_new_line_before_open_brace = all
void MyMethod()
{
    if (...)
    {
        ...
    }
}

// csharp_new_line_before_open_brace = none
void MyMethod() {
    if (...) {
        ...
    }
}
```

#### <a name="csharpnewlinebeforeelse"></a>csharp\_new\_line\_before_else

|||
|-|-|
| **Имя правила** | csharp_new_line_before_else |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — размещать инструкции `else` в новой строке.<br /><br />`false` — размещать инструкции `else` в той же строке. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_new_line_before_else = true
if (...) {
    ...
}
else {
    ...
}

// csharp_new_line_before_else = false
if (...) {
    ...
} else {
    ...
}
```

#### <a name="csharpnewlinebeforecatch"></a>csharp\_new\_line\_before_catch

|||
|-|-|
| **Имя правила** | csharp_new_line_before_catch |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — размещать инструкции `catch` в новой строке.<br /><br />`false` — размещать инструкции `catch` в той же строке. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_new_line_before_catch = true
try {
    ...
}
catch (Exception e) {
    ...
}

// csharp_new_line_before_catch = false
try {
    ...
} catch (Exception e) {
    ...
}
```

#### <a name="csharpnewlinebeforefinally"></a>csharp\_new\_line\_before_finally

|||
|-|-|
| **Имя правила** | csharp_new_line_before_finally |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — требовать, чтобы инструкции `finally` размещались в новой строке после закрывающей фигурной скобки.<br /><br />`false` — требовать, чтобы инструкции `finally` размещались в той же строке после закрывающей фигурной скобки. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_new_line_before_finally = true
try {
    ...
}
catch (Exception e) {
    ...
}
finally {
    ...
}

// csharp_new_line_before_finally = false
try {
    ...
} catch (Exception e) {
    ...
} finally {
    ...
}
```

#### <a name="csharpnewlinebeforemembersinobjectinitializers"></a>csharp\_new\_line\_before\_members\_in\_object_initializers

|||
|-|-|
| **Имя правила** | csharp_new_line_before_members_in_object_initializers |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — требовать, чтобы элементы инициализаторов объектов размещались в разных строках.<br /><br />`false` — требовать, чтобы элементы инициализаторов объектов размещались в той же строке. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_new_line_before_members_in_object_initializers = true
var z = new B()
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_object_initializers = false
var z = new B()
{
    A = 3, B = 4
}
```

#### <a name="csharpnewlinebeforemembersinanonymoustypes"></a>csharp\_new\_line\_before\_members\_in\_anonymous_types

|||
|-|-|
| **Имя правила** | csharp_new_line_before_members_in_anonymous_types |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — требовать, чтобы элементы анонимных типов размещались в разных строках.<br /><br />`false` — требовать, чтобы элементы анонимных типов размещались в той же строке. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_new_line_before_members_in_anonymous_types = true
var z = new
{
    A = 3,
    B = 4
}

// csharp_new_line_before_members_in_anonymous_types = false
var z = new
{
    A = 3, B = 4
}
```

#### <a name="csharpnewlinebetweenqueryexpressionclauses"></a>csharp_new_line_between_query_expression_clauses

|||
|-|-|
| **Имя правила** | csharp_new_line_between_query_expression_clauses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — требовать, чтобы элементы в предложениях выражений запросов размещались в отдельных строках.<br /><br />`false` — требовать, чтобы элементы в предложениях выражений запросов размещались в той же строке. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_new_line_between_query_expression_clauses = true
var q = from a in e
        from b in e
        select a * b;

// csharp_new_line_between_query_expression_clauses = false
var q = from a in e from b in e
        select a * b;
```

### <a name="indentation-options"></a>Параметры отступа

Эти правила форматирования относятся к использованию отступа для форматирования кода.

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_indent_case_contents = true
csharp_indent_switch_labels = true
csharp_indent_labels = flush_left
```

#### <a name="csharpindentcasecontents"></a>csharp\_indent\_case_contents

|||
|-|-|
| **Имя правила** | csharp_indent_case_contents |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — отступ в конструкции `switch` case<br /><br />`false` — не использовать отступ в конструкции `switch` case |
| **Значение по умолчанию в Visual Studio** | `true` |

- Когда для этого правила задано значение **true**, i.
- Когда для этого правила задано значение **false**, d.

Примеры кода:

```csharp
// csharp_indent_case_contents = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_case_contents = false
switch(c) {
    case Color.Red:
    Console.WriteLine("The color is red");
    break;
    case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
    default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharpindentswitchlabels"></a>csharp\_indent\_switch_labels

|||
|-|-|
| **Имя правила** | csharp_indent_switch_labels |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — отступ для меток `switch`.<br /><br />`false` — не использовать отступ для меток `switch`. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_indent_switch_labels = true
switch(c) {
    case Color.Red:
        Console.WriteLine("The color is red");
        break;
    case Color.Blue:
        Console.WriteLine("The color is blue");
        break;
    default:
        Console.WriteLine("The color is unknown.");
        break;
}

// csharp_indent_switch_labels = false
switch(c) {
case Color.Red:
    Console.WriteLine("The color is red");
    break;
case Color.Blue:
    Console.WriteLine("The color is blue");
    break;
default:
    Console.WriteLine("The color is unknown.");
    break;
}
```

#### <a name="csharpindentlabels"></a>csharp\_indent_labels

|||
|-|-|
| **Имя правила** | csharp_indent_labels |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `flush_left` — метки размещаются в крайнем левом столбце.<br /><br />`one_less_than_current` — метки размещаются на предыдущей позиции отступа относительно текущего контекста.<br /><br />`no_change` — метки размещаются на той же позиции отступа, что и текущий контекст. |
| **Значение по умолчанию в Visual Studio** | `no_change` |

Примеры кода:

```csharp
// csharp_indent_labels= flush_left
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
error:
        throw new Exception(...);
    }
}

// csharp_indent_labels = one_less_than_current
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
    error:
        throw new Exception(...);
    }
}

// csharp_indent_labels= no_change
class C
{
    private string MyMethod(...)
    {
        if (...) {
            goto error;
        }
        error:
        throw new Exception(...);
    }
}
```

### <a name="spacing-options"></a>Параметры интервалов

Эти правила форматирования относятся к использованию пробелов для форматирования кода.

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_space_after_cast = true
csharp_space_after_keywords_in_control_flow_statements = true
csharp_space_between_method_declaration_parameter_list_parentheses = true
csharp_space_between_method_call_parameter_list_parentheses = true
csharp_space_between_parentheses = control_flow_statements, type_casts
csharp_space_before_colon_in_inheritance_clause = true
csharp_space_after_colon_in_inheritance_clause = true
csharp_space_around_binary_operators = before_and_after
csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
csharp_space_between_method_call_name_and_opening_parenthesis = false
csharp_space_between_method_call_empty_parameter_list_parentheses = false
csharp_space_after_comma = true
csharp_space_after_dot = false
```

#### <a name="csharpspaceaftercast"></a>csharp\_space\_after_cast

|||
|-|-|
| **Имя правила** | csharp_space_after_cast |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — требовать наличие пробела между типом и значением в приведении.<br /><br />`false` — требовать _отсутствие_ пробела между типом и значением в приведении. |
| **Значение по умолчанию в Visual Studio** | `false` |

Примеры кода:

```csharp
// csharp_space_after_cast = true
int y = (int) x;

// csharp_space_after_cast = false
int y = (int)x;
```

#### <a name="csharpspaceafterkeywordsincontrolflowstatements"></a>csharp_space_after_keywords_in_control_flow_statements

|||
|-|-|
| **Имя правила** | csharp_space_after_keywords_in_control_flow_statements |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — требовать наличие пробела после ключевого слова в операторе потока управления, например цикле `for`.<br /><br />`false` — требовать _отсутствие_ пробела после ключевого слова в операторе потока управления, например цикле `for`. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_space_after_keywords_in_control_flow_statements = true
for (int i;i<x;i++) { ... }

// csharp_space_after_keywords_in_control_flow_statements = false
for(int i;i<x;i++) { ... }
```

#### <a name="csharpspacebetweenmethoddeclarationparameterlistparentheses"></a>csharp_space_between_method_declaration_parameter_list_parentheses

|||
|-|-|
| **Имя правила** | csharp_space_between_method_declaration_parameter_list_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — размещать пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода.<br /><br />`false` — не размещать пробел после открывающей скобки и перед закрывающей скобкой в списке параметров объявления метода. |
| **Значение по умолчанию в Visual Studio** | `false` |

Примеры кода:

```csharp
// csharp_space_between_method_declaration_parameter_list_parentheses = true
void Bark( int x ) { ... }

// csharp_space_between_method_declaration_parameter_list_parentheses = false
void Bark(int x) { ... }
```

#### <a name="csharpspacebetweenmethodcallparameterlistparentheses"></a>csharp_space_between_method_call_parameter_list_parentheses

|||
|-|-|
| **Имя правила** | csharp_space_between_method_call_parameter_list_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — размещать пробел после открывающей скобки и перед закрывающей скобкой в вызове метода.<br /><br />`false` — не размещать пробел после открывающей скобки и перед закрывающей скобкой в вызове метода. |
| **Значение по умолчанию в Visual Studio** | `false` |

Примеры кода:

```csharp
// csharp_space_between_method_call_parameter_list_parentheses = true
MyMethod( argument );

// csharp_space_between_method_call_parameter_list_parentheses = false
MyMethod(argument);
```

#### <a name="csharpspacebetweenparentheses"></a>csharp_space_between_parentheses

|||
|-|-|
| **Имя правила** | csharp_space_between_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `control_flow_statements` — добавлять пробел между скобками для операторов потока управления.<br /><br />`expressions` — добавлять пробел между скобками для выражений.<br /><br />`type_casts` — размещать пробел между скобками в приведениях типов. |
| **Значение по умолчанию в Visual Studio** | `false` |

Если пропустить это правило или использовать значение, отличное от `control_flow_statements`, `expressions` или `type_casts`, этот параметр не применяется.

Примеры кода:

```csharp
// csharp_space_between_parentheses = control_flow_statements
for ( int i = 0; i < 10; i++ ) { }

// csharp_space_between_parentheses = expressions
var z = ( x * y ) - ( ( y - x ) * 3 );

// csharp_space_between_parentheses = type_casts
int y = ( int )x;
```

#### <a name="csharpspacebeforecolonininheritanceclause"></a>csharp\_space\_before\_colon\_in\_inheritance_clause

|||
|-|-|
| **Имя правила** | csharp_space_before_colon_in_inheritance_clause |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения** | `true` — требовать наличие пробела перед двоеточием для баз или интерфейсов в объявлении типа.<br /><br />`false` — требовать _отсутствие_ пробела перед двоеточием для баз или интерфейсов в объявлении типа. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_space_before_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_before_colon_in_inheritance_clause = false
interface I
{

}

class C: I
{

}
```

#### <a name="csharpspaceaftercolonininheritanceclause"></a>csharp\_space\_after\_colon\_in\_inheritance_clause

|||
|-|-|
| **Имя правила** | csharp_space_after_colon_in_inheritance_clause |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения** | `true` — требовать наличие пробела после двоеточия для баз или интерфейсов в объявлении типа.<br /><br />`false` — требовать _отсутствие_ пробела после двоеточия для баз или интерфейсов в объявлении типа. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_space_after_colon_in_inheritance_clause = true
interface I
{

}

class C : I
{

}

// csharp_space_after_colon_in_inheritance_clause = false
interface I
{

}

class C :I
{

}
```

#### <a name="csharpspacearoundbinaryoperators"></a>csharp\_space\_around\_binary_operators

|||
|-|-|
| **Имя правила** | csharp_space_around_binary_operators |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения** | `before_and_after` — вставлять пробел до и после бинарных операторов.<br /><br />`none` — удалять пробелы до и после бинарных операторов.<br /><br />`ignore` — игнорировать пробелы вокруг бинарных операторов. |
| **Значение по умолчанию в Visual Studio** | `before_and_after` |

Если пропустить это правило или использовать значение, отличное от `before_and_after`, `none` или `ignore`, этот параметр не применяется.

Примеры кода:

```csharp
// csharp_space_around_binary_operators = before_and_after
return x * (x - y);

// csharp_space_around_binary_operators = none
return x*(x-y);

// csharp_space_around_binary_operators = ignore
return x  *  (x-y);
```

#### <a name="csharpspacebetweenmethoddeclarationemptyparameterlistparentheses"></a>csharp_space_between_method_declaration_empty_parameter_list_parentheses

|||
|-|-|
| **Имя правила** | csharp_space_between_method_declaration_empty_parameter_list_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения** | `true` — вставлять пробел между скобками пустого списка параметров при объявлении метода.<br /><br />`false` — удалять пробел между скобками пустого списка параметров при объявлении метода. |
| **Значение по умолчанию в Visual Studio** | `false` |

Примеры кода:

```csharp
// csharp_space_between_method_declaration_empty_parameter_list_parentheses = true
void Goo( )
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}

// csharp_space_between_method_declaration_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspacebetweenmethodcallnameandopeningparenthesis"></a>csharp_space_between_method_call_name_and_opening_parenthesis

|||
|-|-|
| **Имя правила** | csharp_space_between_method_call_name_and_opening_parenthesis |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения** | `true` — вставлять пробел между именем вызываемого метода и открывающей скобкой.<br /><br />`false` — удалять пробел между именем вызываемого метода и открывающей скобкой. |
| **Значение по умолчанию в Visual Studio** | `false` |

Примеры кода:

```csharp
// csharp_space_between_method_call_name_and_opening_parenthesis = true
void Goo()
{
    Goo (1);
}

void Goo(int x)
{
    Goo ();
}

// csharp_space_between_method_call_name_and_opening_parenthesis = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspacebetweenmethodcallemptyparameterlistparentheses"></a>csharp_space_between_method_call_empty_parameter_list_parentheses

|||
|-|-|
| **Имя правила** | csharp_space_between_method_call_empty_parameter_list_parentheses |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |
| **Значения** | `true` — вставлять пробел между скобками в пустом списке аргументов.<br /><br />`false` — удалять пробел между скобками в пустом списке аргументов. |
| **Значение по умолчанию в Visual Studio** | `false` |

Примеры кода:

```csharp
// csharp_space_between_method_call_empty_parameter_list_parentheses = true
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo( );
}

// csharp_space_between_method_call_empty_parameter_list_parentheses = false
void Goo()
{
    Goo(1);
}

void Goo(int x)
{
    Goo();
}
```

#### <a name="csharpspaceaftercomma"></a>csharp_space_after_comma

|||
|-|-|
| **Имя правила** | csharp_space_after_comma |
| **Применимые языки** | C# |
| **Значения** | `true` — вставлять пробел после запятой.<br /><br />`false` — удалять пробел после запятой. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
// csharp_space_after_comma = true
int[] x = new int[] { 1, 2, 3, 4, 5 };

// csharp_space_after_comma = false
int[] x = new int[] { 1,2,3,4,5 }
```

#### <a name="csharpspaceafterdot"></a>csharp_space_after_dot

|||
|-|-|
| **Имя правила** | csharp_space_after_dot |
| **Применимые языки** | C# |
| **Значения** | `true` — вставлять пробел после точки.<br /><br />`false` — удалять пробел после точки. |
| **Значение по умолчанию в Visual Studio** | `false` |

Примеры кода:

```csharp
// csharp_space_after_dot = true
this. Goo();

// csharp_space_after_dot = false
this.Goo();
```

### <a name="wrap-options"></a>Параметры переноса

Эти правила форматирования определяют размещение операторов и блоков кода в одной или разных строках.

Пример файла *EDITORCONFIG*:

```ini
# CSharp formatting settings:
[*.cs]
csharp_preserve_single_line_statements = true
csharp_preserve_single_line_blocks = true
```

#### <a name="csharppreservesinglelinestatements"></a>csharp_preserve_single_line_statements

|||
|-|-|
| **Имя правила** | csharp_preserve_single_line_statements |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — оставлять выражения и объявления элемента в одной строке.<br /><br />`false` — оставлять выражения и объявления элемента в разных строках. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
//csharp_preserve_single_line_statements = true
int i = 0; string name = "John";

//csharp_preserve_single_line_statements = false
int i = 0;
string name = "John";
```

#### <a name="csharppreservesinglelineblocks"></a>csharp_preserve_single_line_blocks

|||
|-|-|
| **Имя правила** | csharp_preserve_single_line_blocks |
| **Применимые языки** | C# |
| **Представленные версии** | Visual Studio 2017 версия 15.3 |
| **Значения** | `true` — оставлять блок кода в одной строке.<br /><br />`false` — оставлять блок кода в разных строках. |
| **Значение по умолчанию в Visual Studio** | `true` |

Примеры кода:

```csharp
//csharp_preserve_single_line_blocks = true
public int Foo { get; set; }

//csharp_preserve_single_line_blocks = false
public int MyProperty
{
    get; set;
}
```

## <a name="see-also"></a>См. также

- [Языковые соглашения](editorconfig-language-conventions.md)
- [Соглашения об именовании](editorconfig-naming-conventions.md)
- [Параметры соглашений о написании кода .NET в EditorConfig](editorconfig-code-style-settings-reference.md)
