---
title: Соглашения о языке .NET для EditorConfig
ms.date: 03/31/2020
ms.topic: reference
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- language code style rules [EditorConfig]
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a3f80eb555ef11a1e0a462e93d4508e778bd987d
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2020
ms.locfileid: "80544012"
---
# <a name="language-conventions"></a>Языковые соглашения

Языковые соглашения для EditorConfig в Visual Studio делятся на две категории: те, которые применяются к Visual Basic и C#, а также те, которые относятся только к C#. Языковые соглашения влияют на использование различных аспектов языка программирования, например модификаторы и круглые скобки.

> [!TIP]
> - Чтобы просмотреть примеры кода для выбранного языка программирования, щелкните его в раскрывающемся меню в правом верхнем углу окна браузера.
>
>   ![Элемент управления выбора языка кода](media/code-language-picker.png)
>
> - Используйте ссылки **в этой статье**, чтобы перейти к различным разделам страницы.

## <a name="rule-format"></a>Формат правил

Правила для языковых соглашений имеют следующий формат:

`option_name = value:severity`

Для каждого языкового соглашения укажите значение, которое определяет условия выбора соответствующего стиля. Многие правила принимают значение `true` (предпочитать этот стиль) или `false` (не предпочитать этот стиль). Другие правила принимают значения `when_on_single_line` или `never`. Вторая часть правила определяет [серьезность](#severity-levels).

::: moniker range=">=vs-2019"

> [!NOTE]
> Так как соглашения о языке применяются анализаторами, их уровень серьезности можно также задать, используя синтаксис конфигурации по умолчанию для анализаторов. Синтаксис имеет вид `dotnet_diagnostic.<rule ID>.severity = <severity>`, например `dotnet_diagnostic.IDE0040.severity = silent`. Дополнительные сведения см. в разделе [Задание уровня серьезности правила в файле EditorConfig](../code-quality/use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file).

::: moniker-end

## <a name="severity-levels"></a>Уровни серьезности

Серьезность в языковых соглашениях указывает уровень, на котором нужно применять соответствующий стиль. Следующая таблица описывает возможные значения серьезности и их влияние:

Серьезность | Действие
:------- | ------
`error` | При несоблюдении этого правила стиля выводится ошибка компилятора.
`warning` | При несоблюдении этого правила стиля выводится предупреждение компилятора.
`suggestion` | При несоблюдении этого правила стиля пользователю выводится предложение. Предложения отображаются в виде трех серых точек под первыми двумя символами.
`silent` | При нарушении этого правила пользователю не выводится никаких данных. Однако функции создания кода будут генерировать код в этом стиле. Правила с уровнем серьезности `silent` участвуют в очистке и приводятся в меню **Быстрые действия и рефакторинг**.
`none` | При нарушении этого правила пользователю не выводится никаких данных. Однако функции создания кода будут генерировать код в этом стиле. Правила с уровнем серьезности `none` никогда не появляются в меню **Быстрые действия и операции рефакторинга**. В большинстве случаев это воспринимается как "отключено" или "игнорируется".

::: moniker range=">=vs-2019"

## <a name="automatically-configure-code-styles"></a>Автоматическая настройка стилей кода

Начиная с Visual Studio 2019 версии 16.3, в меню [Быстрые действия](quick-actions.md) можно настроить правила стиля кода после нарушения стиля.

Чтобы изменить соглашение о стиле кода, выполните указанные ниже действия.

1. Наведите указатель мыши на волнистую линию в редакторе, а затем откройте появившееся меню лампочки. Выберите пункт **Настроить или подавить ошибки** > **Настроить \<идентификатор правила> стиль кода**.

   ![Настройка стиля кода в меню лампочки в Visual Studio](media/vs-2019/configure-code-style.png)

2. Далее выберите один из вариантов стиля кода.

   ![Настройка стиля кода](media/vs-2019/configure-code-style-setting.png)

   Visual Studio добавляет или изменяет параметр конфигурации в файле EditorConfig, как показано в поле предварительного просмотра.

Чтобы изменить степень серьезности для нарушения стиля кода, выполните те же действия, но выберите пункт **Настроить \<идентификатор правила> степень серьезности** вместо **Настроить \<идентификатор правила> стиль кода**. Дополнительные сведения см. в разделе [Автоматическая настройка уровня серьезности правила](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity).

::: moniker-end

## <a name="net-code-style-settings"></a>Параметры стиля кода .NET

Правила стилей в этом разделе относятся как к C#, так и к Visual Basic.

- [Квалификаторы "This." и "Me."](#this-and-me)
  - dotnet\_style\_qualification\_for_field
  - dotnet\_style\_qualification\_for_property
  - dotnet\_style\_qualification\_for_method
  - dotnet\_style\_qualification\_for_event
- [Ключевые слова языка вместо имен типов .NET Framework для ссылок на типы](#language-keywords)
  - dotnet\_style\_predefined\_type\_for\_locals\_parameters_members
  - dotnet\_style\_predefined\_type\_for\_member_access
- [Предпочтения для модификаторов](#normalize-modifiers)
  - dotnet\_style\_require\_accessibility_modifiers
  - visual\_basic\_preferred\_modifier_order
  - dotnet\_style\_readonly\_field
- [Предпочтения относительно круглых скобок](#parentheses-preferences)
  - dotnet\_style\_parentheses\_in\_arithmetic\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_binary\_operators
  - dotnet\_style\_parentheses\_in\_other\_operators
  - dotnet\_style\_parentheses\_in\_relational\_binary\_operators
- [Настройки уровня выражений](#expression-level-preferences)
  - dotnet\_style\_object_initializer
  - dotnet\_style\_collection_initializer
  - dotnet\_style\_explicit\_tuple_names
  - dotnet\_style\_prefer\_inferred\_tuple_names
  - dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names
  - dotnet\_style\_prefer\_auto\_properties
  - dotnet\_style\_prefer\_conditional\_expression\_over\_assignment
  - dotnet\_style\_prefer\_conditional\_expression\_over\_return
  - dotnet\_style\_prefer\_compound\_assignment
- [Настройки проверки Null](#null-checking-preferences)
  - dotnet\_style\_coalesce_expression
  - dotnet\_style\_null_propagation
  - dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

### <a name="this-and-me-qualifiers"></a><a name="this-and-me"></a>Квалификаторы "This." и "Me."

Это правило стиля может применяться к полям, свойствам, методам или событиям. Значение **true** означает, что перед символом кода предпочтительно добавлять `this.` в C# или `Me.` в Visual Basic. Значение **false** означает, что перед символом кода предпочтительно _не_ добавлять `this.` или `Me.`.

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_qualification_for_field = false:suggestion
dotnet_style_qualification_for_property = false:suggestion
dotnet_style_qualification_for_method = false:suggestion
dotnet_style_qualification_for_event = false:suggestion
```

#### <a name="dotnet_style_qualification_for_field"></a>dotnet\_style\_qualification\_for_field

|||
|-|-|
| **Имя правила** | dotnet_style_qualification_for_field |
| **Идентификатор правила** | IDE0003 и IDE0009 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать поля с префиксом `this.` в C# или `Me.` в Visual Basic.<br /><br />`false` — предпочитать поля _без_ префиксов `this.` или `Me.`. |
| **Значение по умолчанию в Visual Studio** | `false:silent` |

Примеры кода:

```csharp
// dotnet_style_qualification_for_field = true
this.capacity = 0;

// dotnet_style_qualification_for_field = false
capacity = 0;
```

```vb
' dotnet_style_qualification_for_field = true
Me.capacity = 0

' dotnet_style_qualification_for_field = false
capacity = 0
```

#### <a name="dotnet_style_qualification_for_property"></a>dotnet\_style\_qualification\_for_property

|||
|-|-|
| **Имя правила** | dotnet_style_qualification_for_property |
| **Идентификатор правила** | IDE0003 и IDE0009 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать свойства с префиксом `this.` в C# или `Me.` в Visual Basic.<br /><br />`false` — предпочитать свойства _без_ префиксов `this.` или `Me.`. |
| **Значение по умолчанию в Visual Studio** | `false:silent` |

Примеры кода:

```csharp
// dotnet_style_qualification_for_property = true
this.ID = 0;

// dotnet_style_qualification_for_property = false
ID = 0;
```

```vb
' dotnet_style_qualification_for_property = true
Me.ID = 0

' dotnet_style_qualification_for_property = false
ID = 0
```

#### <a name="dotnet_style_qualification_for_method"></a>dotnet\_style\_qualification\_for_method

|||
|-|-|
| **Имя правила** | dotnet_style_qualification_for_method |
| **Идентификатор правила** | IDE0003 и IDE0009 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать методы с префиксом `this.` в C# или `Me.` в Visual Basic.<br /><br />`false` — предпочитать методы _без_ префиксов `this.` или `Me.`. |
| **Значение по умолчанию в Visual Studio** | `false:silent` |

Примеры кода:

```csharp
// dotnet_style_qualification_for_method = true
this.Display();

// dotnet_style_qualification_for_method = false
Display();
```

```vb
' dotnet_style_qualification_for_method = true
Me.Display()

' dotnet_style_qualification_for_method = false
Display()
```

#### <a name="dotnet_style_qualification_for_event"></a>dotnet\_style\_qualification\_for_event

|||
|-|-|
| **Имя правила** | dotnet_style_qualification_for_event |
| **Идентификатор правила** | IDE0003 и IDE0009 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать события с префиксом `this.` в C# или `Me.` в Visual Basic.<br /><br />`false` — предпочитать события _без_ префиксов `this.` или `Me.`. |
| **Значение по умолчанию в Visual Studio** | `false:silent` |

Примеры кода:

```csharp
// dotnet_style_qualification_for_event = true
this.Elapsed += Handler;

// dotnet_style_qualification_for_event = false
Elapsed += Handler;
```

```vb
' dotnet_style_qualification_for_event = true
AddHandler Me.Elapsed, AddressOf Handler

' dotnet_style_qualification_for_event = false
AddHandler Elapsed, AddressOf Handler
```

### <a name="language-keywords-instead-of-framework-type-names-for-type-references"></a><a name="language-keywords"></a>Ключевые слова языка вместо имен типов .NET Framework для ссылок на типы

Это правило стиля можно применить к локальным переменным, параметрам методов и членам классов, а также в виде отдельного правила для ввода выражений доступа к члену. Значение **true** означает предпочтение ключевого слова языка (например, `int` или `Integer`) вместо имени типа (например, `Int32`) для типов, которые представляет ключевое слово. Значение **false** означает предпочтение имени типа вместо ключевого слова языка.

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_predefined_type_for_locals_parameters_members = true:suggestion
dotnet_style_predefined_type_for_member_access = true:suggestion
```

#### <a name="dotnet_style_predefined_type_for_locals_parameters_members"></a>dotnet\_style\_predefined\_type\_for\_locals\_parameters_members

|||
|-|-|
| **Имя правила** | dotnet_style_predefined_type_for_locals_parameters_members |
| **Идентификатор правила** | IDE0012 и IDE0014 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать ключевые слова языка для локальных переменных, параметров методов и членов классов вместо имени типа для типов, имеющих представляющее их ключевое слово.<br /><br />`false` — предпочитать имя типа для локальных переменных, параметров методов и членов классов вместо ключевого слова языка. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// dotnet_style_predefined_type_for_locals_parameters_members = true
private int _member;

// dotnet_style_predefined_type_for_locals_parameters_members = false
private Int32 _member;
```

```vb
' dotnet_style_predefined_type_for_locals_parameters_members = true
Private _member As Integer

' dotnet_style_predefined_type_for_locals_parameters_members = false
Private _member As Int32
```

#### <a name="dotnet_style_predefined_type_for_member_access"></a>dotnet\_style\_predefined\_type\_for\_member_access

|||
|-|-|
| **Имя правила** | dotnet_style_predefined_type_for_member_access |
| **Идентификатор правила** | IDE0013 и IDE0015 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать ключевое слово языка для выражений доступа к элементам вместо имени типа для типов, имеющих представляющее их ключевое слово.<br /><br />`false` — предпочитать имя типа для выражений доступа к элементам вместо ключевого слова языка. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// dotnet_style_predefined_type_for_member_access = true
var local = int.MaxValue;

// dotnet_style_predefined_type_for_member_access = false
var local = Int32.MaxValue;
```

```vb
' dotnet_style_predefined_type_for_member_access = true
Dim local = Integer.MaxValue

' dotnet_style_predefined_type_for_member_access = false
Dim local = Int32.MaxValue
```

### <a name="modifier-preferences"></a><a name="normalize-modifiers"></a>Предпочтения для модификаторов

Этот раздел приводит предпочтительные правила стиля для модификаторов, в том числе когда требуются модификаторы доступа, указывается предпочтительный порядок сортировки или требуется модификатор только для чтения.

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_require_accessibility_modifiers = always:suggestion
dotnet_style_readonly_field = true:warning

# CSharp code style settings:
[*.cs]
csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async:suggestion

# Visual Basic code style settings:
[*.vb]
visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async:suggestion
```

#### <a name="dotnet_style_require_accessibility_modifiers"></a>dotnet\_style\_require\_accessibility_modifiers

|||
|-|-|
| **Имя правила** | dotnet_style_require_accessibility_modifiers |
| **Идентификатор правила** | IDE0040 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `always` — предпочитать указание модификаторов специальных возможностей.<br /><br />`for_non_interface_members` — предпочитать объявление модификаторов специальных возможностей, за исключением открытых элементов интерфейса. (Аналогично значению **always** и будет использоваться при наличии методов интерфейса C# по умолчанию.)<br /><br />`never` — предпочитать не указывать модификаторы специальных возможностей.<br /><br />`omit_if_default` — предпочитать указание модификаторов специальных возможностей, если они не являются модификаторами по умолчанию. |
| **Значение по умолчанию в Visual Studio** | `for_non_interface_members:silent` |
| **Представленные версии** | Visual Studio 2017 версии 15.5 |

Примеры кода:

```csharp
// dotnet_style_require_accessibility_modifiers = always
// dotnet_style_require_accessibility_modifiers = for_non_interface_members
class MyClass
{
    private const string thisFieldIsConst = "constant";
}

// dotnet_style_require_accessibility_modifiers = never
class MyClass
{
    const string thisFieldIsConst = "constant";
}
```

#### <a name="csharp_preferred_modifier_order"></a>csharp_preferred_modifier_order

|||
|-|-|
| **Имя правила** | csharp_preferred_modifier_order |
| **Идентификатор правила** | IDE0036 |
| **Применимые языки** | C# |
| **Значения** | Один или несколько модификаторов C#, таких как `public`, `private` и `protected`. |
| **Значение по умолчанию в Visual Studio** | `public, private, protected, internal, static, extern, new, virtual, abstract, sealed, override, readonly, unsafe, volatile, async:silent` |
| **Представленные версии** | Visual Studio 2017 версии 15.5 |

- Если это правило задано для списка модификаторов, предпочитать указанный порядок.
- Если это правило пропущено в файле, не предпочитать порядок модификаторов.

Примеры кода:

```csharp
// csharp_preferred_modifier_order = public,private,protected,internal,static,extern,new,virtual,abstract,sealed,override,readonly,unsafe,volatile,async
class MyClass
{
    private static readonly int _daysInYear = 365;
}
```

#### <a name="visual_basic_preferred_modifier_order"></a>visual_basic_preferred_modifier_order

|||
|-|-|
| **Имя правила** | visual_basic_preferred_modifier_order |
| **Идентификатор правила** | IDE0036 |
| **Применимые языки** | Visual Basic |
| **Значения** | Один или несколько модификаторов Visual Basic, таких как `Partial`, `Private` и `Public`. |
| **Значение по умолчанию в Visual Studio** | `Partial, Default, Private, Protected, Public, Friend, NotOverridable, Overridable, MustOverride, Overloads, Overrides, MustInherit, NotInheritable, Static, Shared, Shadows, ReadOnly, WriteOnly, Dim, Const,WithEvents, Widening, Narrowing, Custom, Async:silent` |
| **Представленные версии** | Visual Studio 2017 версии 15.5 |

- Если это правило задано для списка модификаторов, предпочитать указанный порядок.
- Если это правило пропущено в файле, не предпочитать порядок модификаторов.

Примеры кода:

```vb
' visual_basic_preferred_modifier_order = Partial,Default,Private,Protected,Public,Friend,NotOverridable,Overridable,MustOverride,Overloads,Overrides,MustInherit,NotInheritable,Static,Shared,Shadows,ReadOnly,WriteOnly,Dim,Const,WithEvents,Widening,Narrowing,Custom,Async
Public Class MyClass
    Private Shared ReadOnly daysInYear As Int = 365
End Class
```

#### <a name="visual_basic_style_unused_value_expression_statement_preference"></a>visual_basic_style_unused_value_expression_statement_preference

|||
|-|-|
| **Имя правила** | visual_basic_style_unused_value_expression_statement_preference |
| **Идентификатор правила** | IDE0058 |
| **Применимые языки** | Visual Basic |
| **Значения** | `unused_local_variable:silent` |
| **Значение по умолчанию в Visual Studio** | `unused_local_variable:silent` |

Примеры кода:

```vb
' visual_basic_style_unused_value_expression_statement_preference = unused_local_variable:silent

Dim unused = Computation()
```

#### <a name="visual_basic_style_unused_value_assignment_preference"></a>visual_basic_style_unused_value_assignment_preference

|||
|-|-|
| **Имя правила** | visual_basic_style_unused_value_assignment_preference |
| **Идентификатор правила** | IDE0059 |
| **Применимые языки** | Visual Basic |
| **Значения** | `unused_local_variable:silent` |
| **Значение по умолчанию в Visual Studio** | `unused_local_variable:silent` |

Примеры кода:

```vb
' visual_basic_style_unused_value_assignment_preference = unused_local_variable:suggestion

Dim unused = Computation()
Dim x = 1;
```

#### <a name="dotnet_style_readonly_field"></a>dotnet_style_readonly_field

|||
|-|-|
| **Имя правила** | dotnet_style_readonly_field |
| **Идентификатор правила** | IDE0044 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать, чтобы поля отмечались меткой `readonly` (C#) или `ReadOnly` (Visual Basic), если они назначаются только в коде или внутри конструктора.<br /><br />`false` — отсутствие предпочтений по наличию для полей меток `readonly` (C#) или `ReadOnly` (Visual Basic). |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |

Примеры кода:

```csharp
// dotnet_style_readonly_field = true
class MyClass
{
    private readonly int _daysInYear = 365;
}
```

```vb
' dotnet_style_readonly_field = true
Public Class MyClass
    Private ReadOnly daysInYear As Int = 365
End Class
```

### <a name="parentheses-preferences"></a>Предпочтения относительно круглых скобок

Правила стилей в этом разделе относятся к предпочтениям относительно круглых скобок, включая использование круглых скобок для арифметических, реляционных и других бинарных операторов.

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_binary_operators = always_for_clarity:silent
dotnet_style_parentheses_in_other_operators = never_if_unnecessary:silent
```

#### <a name="dotnet_style_parentheses_in_arithmetic_binary_operators"></a>dotnet\_style\_parentheses\_in\_arithmetic\_binary_operators

|||
|-|-|
| **Имя правила** | dotnet_style_parentheses_in_arithmetic_binary_operators |
| **Идентификатор правила** | IDE0047 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `always_for_clarity` — предпочитать скобки для указания приоритета арифметических операторов (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^` и `|`).<br /><br />`never_if_unnecessary` — предпочитать бесскобочную запись приоритета арифметических операторов (`*`, `/`, `%`, `+`, `-`, `<<`, `>>`, `&`, `^` и `|`). |
| **Значение по умолчанию в Visual Studio** | `always_for_clarity:silent` |
| **Представленные версии** | Visual Studio 2017 версии 15.8 |

Примеры кода:

```csharp
// dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
var v = a + (b * c);

// dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
var v = a + b * c;
```

```vb
' dotnet_style_parentheses_in_arithmetic_binary_operators = always_for_clarity
Dim v = a + (b * c)

' dotnet_style_parentheses_in_arithmetic_binary_operators = never_if_unnecessary
Dim v = a + b * c
```

#### <a name="dotnet_style_parentheses_in_relational_binary_operators"></a>dotnet\_style\_parentheses\_in\_relational\_binary_operators

|||
|-|-|
| **Имя правила** | dotnet_style_parentheses_in_relational_binary_operators |
| **Идентификатор правила** | IDE0047 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `always_for_clarity` — предпочитать скобки для указания приоритета операторов отношения (`>`, `<`, `<=`, `>=`, `is`, `as`, `==` и `!=`).<br /><br />`never_if_unnecessary` — предпочитать бесскобочную запись приоритета операторов отношения (`>`, `<`, `<=`, `>=`, `is`, `as`, `==` и `!=`). |
| **Значение по умолчанию в Visual Studio** | `always_for_clarity:silent` |
| **Представленные версии** | Visual Studio 2017 версии 15.8 |

Примеры кода:

```csharp
// dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
var v = (a < b) == (c > d);

// dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
var v = a < b == c > d;
```

```vb
' dotnet_style_parentheses_in_relational_binary_operators = always_for_clarity
Dim v = (a < b) = (c > d)

' dotnet_style_parentheses_in_relational_binary_operators = never_if_unnecessary
Dim v = a < b = c > d
```

#### <a name="dotnet_style_parentheses_in_other_binary_operators"></a>dotnet\_style\_parentheses\_in\_other\_binary_operators

|||
|-|-|
| **Имя правила** | dotnet_style_parentheses_in_other_binary_operators |
| **Идентификатор правила** | IDE0047 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `always_for_clarity` — предпочитать скобки для указания приоритета бинарных операторов (`&&`, `||` и `??`).<br /><br />`never_if_unnecessary` — предпочитать бесскобочную запись приоритета бинарных операторов (`&&`, `||` и `??`). |
| **Значение по умолчанию в Visual Studio** | `always_for_clarity:silent` |
| **Представленные версии** | Visual Studio 2017 версии 15.8 |

Примеры кода:

```csharp
// dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
var v = a || (b && c);

// dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
var v = a || b && c;
```

```vb
' dotnet_style_parentheses_in_other_binary_operators = always_for_clarity
Dim v = a OrElse (b AndAlso c)

' dotnet_style_parentheses_in_other_binary_operators = never_if_unnecessary
Dim v = a OrElse b AndAlso c
```

#### <a name="dotnet_style_parentheses_in_other_operators"></a>dotnet\_style\_parentheses\_in\_other_operators

|||
|-|-|
| **Имя правила** | dotnet_style_parentheses_in_other_operators |
| **Идентификатор правила** | IDE0047 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `always_for_clarity` — предпочитать скобки для указания приоритета операторов.<br /><br />`never_if_unnecessary` — предпочитать бесскобочную запись при очевидном приоритете операторов. |
| **Значение по умолчанию в Visual Studio** | `never_if_unnecessary:silent` |
| **Представленные версии** | Visual Studio 2017 версии 15.8 |

Примеры кода:

```csharp
// dotnet_style_parentheses_in_other_operators = always_for_clarity
var v = (a.b).Length;

// dotnet_style_parentheses_in_other_operators = never_if_unnecessary
var v = a.b.Length;
```

```vb
' dotnet_style_parentheses_in_other_operators = always_for_clarity
Dim v = (a.b).Length

' dotnet_style_parentheses_in_other_operators = never_if_unnecessary
Dim v = a.b.Length
```

### <a name="expression-level-preferences"></a>Предпочтения уровня выражений

Правила стилей в этом разделе относятся к настройкам уровня выражений, включая использование инициализаторов объектов, инициализаторов наборов, явных или выводимых имен кортежей и выводимых анонимных типов.

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_object_initializer = true:suggestion
dotnet_style_collection_initializer = true:suggestion
dotnet_style_explicit_tuple_names = true:suggestion
dotnet_style_prefer_inferred_tuple_names = true:suggestion
dotnet_style_prefer_inferred_anonymous_type_member_names = true:suggestion
dotnet_style_prefer_auto_properties = true:silent
dotnet_style_prefer_conditional_expression_over_assignment = true:suggestion
dotnet_style_prefer_conditional_expression_over_return = true:suggestion
dotnet_style_prefer_compound_assignment = true:suggestion
```

#### <a name="dotnet_style_object_initializer"></a>dotnet\_style\_object_initializer

|||
|-|-|
| **Имя правила** | dotnet_style_object_initializer |
| **Идентификатор правила** | IDE0017 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать инициализацию объектов с помощью инициализаторов объектов, когда это возможно.<br /><br />`false` — предпочитать *не* инициализировать объекты с помощью инициализаторов объектов. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// dotnet_style_object_initializer = true
var c = new Customer() { Age = 21 };

// dotnet_style_object_initializer = false
var c = new Customer();
c.Age = 21;
```

```vb
' dotnet_style_object_initializer = true
Dim c = New Customer() With {.Age = 21}

' dotnet_style_object_initializer = false
Dim c = New Customer()
c.Age = 21
```

#### <a name="dotnet_style_collection_initializer"></a>dotnet\_style\_collection_initializer

|||
|-|-|
| **Имя правила** | dotnet_style_collection_initializer |
| **Идентификатор правила** | IDE0028 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать инициализировать коллекции с помощью инициализаторов наборов, когда это возможно.<br /><br />`false` — предпочитать *не* инициализировать коллекции с помощью инициализаторов наборов. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// dotnet_style_collection_initializer = true
var list = new List<int> { 1, 2, 3 };

// dotnet_style_collection_initializer = false
var list = new List<int>();
list.Add(1);
list.Add(2);
list.Add(3);
```

```vb
' dotnet_style_collection_initializer = true
Dim list = New List(Of Integer) From {1, 2, 3}

' dotnet_style_collection_initializer = false
Dim list = New List(Of Integer)
list.Add(1)
list.Add(2)
list.Add(3)
```

#### <a name="dotnet_style_explicit_tuple_names"></a>dotnet\_style\_explicit\_tuple_names

|||
|-|-|
| **Имя правила** | dotnet_style_explicit_tuple_names |
| **Идентификатор правила** | IDE0033 |
| **Применимые языки** | C# 7.0+ и Visual Basic 15+ |
| **Значения** | `true` — предпочитать имена кортежей вместо свойств ItemX.<br /><br />`false` — предпочитать свойства ItemX вместо имен кортежей. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// dotnet_style_explicit_tuple_names = true
(string name, int age) customer = GetCustomer();
var name = customer.name;

// dotnet_style_explicit_tuple_names = false
(string name, int age) customer = GetCustomer();
var name = customer.Item1;
```

```vb
 ' dotnet_style_explicit_tuple_names = true
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.name

' dotnet_style_explicit_tuple_names = false
Dim customer As (name As String, age As Integer) = GetCustomer()
Dim name = customer.Item1
```

#### <a name="dotnet_style_prefer_inferred_tuple_names"></a>dotnet\_style\_prefer\_inferred\_tuple_names

|||
|-|-|
| **Имя правила** | dotnet_style_prefer_inferred_tuple_names |
| **Идентификатор правила** | IDE0037 |
| **Применимые языки** | C# 7.1+ и Visual Basic 15+ |
| **Значения** | `true` — предпочитать выводимые имена элементов кортежа<br /><br />`false` — предпочитать явные имена элементов кортежа |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |
| **Представленные версии** | Visual Studio 2017 версии 15.6 |

Примеры кода:

```csharp
// dotnet_style_prefer_inferred_tuple_names = true
var tuple = (age, name);

// dotnet_style_prefer_inferred_tuple_names = false
var tuple = (age: age, name: name);
```

```vb
' dotnet_style_prefer_inferred_tuple_names = true
Dim tuple = (name, age)

' dotnet_style_prefer_inferred_tuple_names = false
Dim tuple = (name:=name, age:=age)
```

#### <a name="dotnet_style_prefer_inferred_anonymous_type_member_names"></a>dotnet\_style\_prefer\_inferred\_anonymous\_type\_member_names

|||
|-|-|
| **Имя правила** | dotnet_style_prefer_inferred_anonymous_type_member_names |
| **Идентификатор правила** | IDE0037 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать выводимые имена элементов анонимного типа<br /><br />`false` — предпочитать явные имена элементов анонимного типа |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |
| **Представленные версии** | Visual Studio 2017 версии 15.6 |

Примеры кода:

```csharp
// dotnet_style_prefer_inferred_anonymous_type_member_names = true
var anon = new { age, name };

// dotnet_style_prefer_inferred_anonymous_type_member_names = false
var anon = new { age = age, name = name };
```

```vb
' dotnet_style_prefer_inferred_anonymous_type_member_names = true
Dim anon = New With {name, age}

' dotnet_style_prefer_inferred_anonymous_type_member_names = false
Dim anon = New With {.name = name, .age = age}
```

#### <a name="dotnet_style_prefer_auto_properties"></a>dotnet\_style\_prefer\_auto\_properties

|||
|-|-|
| **Имя правила** | dotnet_style_prefer_auto_properties |
| **Идентификатор правила** | IDE0032 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать автосвойства вместо других свойств с закрытыми резервными полями.<br /><br />`false` — предпочитать свойства с закрытыми резервными полями вместо автосвойств. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |

Примеры кода:

```csharp
// dotnet_style_prefer_auto_properties = true
private int Age { get; }

// dotnet_style_prefer_auto_properties = false
private int age;

public int Age
{
    get
    {
        return age;
    }
}
```

```vb
' dotnet_style_prefer_auto_properties = true
Public ReadOnly Property Age As Integer

' dotnet_style_prefer_auto_properties = false
Private _age As Integer

Public ReadOnly Property Age As Integer
    Get
        return _age
    End Get
End Property
```

#### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Имя правила** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Идентификатор правила** | IDE0041 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать проверку значения NULL с сопоставлением шаблонов вместо `object.ReferenceEquals`<br /><br />`false` — предпочитать `object.ReferenceEquals` вместо проверки значения NULL с сопоставлением шаблонов |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |
| **Представленные версии** | Visual Studio 2017 версии 15.7 |

Примеры кода:

```csharp
// dotnet_style_prefer_is_null_check_over_reference_equality_method = true
if (value is null)
    return;

// dotnet_style_prefer_is_null_check_over_reference_equality_method = false
if (object.ReferenceEquals(value, null))
    return;
```

```vb
' dotnet_style_prefer_is_null_check_over_reference_equality_method = true
If value Is Nothing
    Return
End If

' dotnet_style_prefer_is_null_check_over_reference_equality_method = false
If Object.ReferenceEquals(value, Nothing)
    Return
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_assignment"></a>dotnet\_style\_prefer\_conditional\_expression\_over_assignment

|||
|-|-|
| **Имя правила** | dotnet_style_prefer_conditional_expression_over_assignment |
| **Идентификатор правила** | IDE0045 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать назначения с тернарным условием вместо оператора if-else.<br /><br />`false` — предпочитать оператор if-else вместо тернарного условия. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |
| **Представленные версии** | Visual Studio 2017 версии 15.8 |

Примеры кода:

```csharp
// dotnet_style_prefer_conditional_expression_over_assignment = true
string s = expr ? "hello" : "world";

// dotnet_style_prefer_conditional_expression_over_assignment = false
string s;
if (expr)
{
    s = "hello";
}
else
{
    s = "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_assignment = true
Dim s As String = If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_assignment = false
Dim s As String
If expr Then
    s = "hello"
Else
    s = "world"
End If
```

#### <a name="dotnet_style_prefer_conditional_expression_over_return"></a>dotnet\_style\_prefer\_conditional\_expression\_over_return

|||
|-|-|
| **Имя правила** | dotnet_style_prefer_conditional_expression_over_return |
| **Идентификатор правила** | IDE0046 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать тернарные условия вместо оператора if-else в операторах возврата (return).<br /><br />`false` — предпочитать оператор if-else вместо тернарного условия в операторах возврата (return). |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |
| **Представленные версии** | Visual Studio 2017 версии 15.8 |

Примеры кода:

```csharp
// dotnet_style_prefer_conditional_expression_over_return = true
return expr ? "hello" : "world"

// dotnet_style_prefer_conditional_expression_over_return = false
if (expr)
{
    return "hello";
}
else
{
    return "world";
}
```

```vb
' dotnet_style_prefer_conditional_expression_over_return = true
Return If(expr, "hello", "world")

' dotnet_style_prefer_conditional_expression_over_return = false
If expr Then
    Return "hello"
Else
    Return "world"
End If
```

#### <a name="dotnet_style_prefer_compound_assignment"></a>dotnet\_style\_prefer\_compound\_assignment

|||
|-|-|
| **Имя правила** | dotnet_style_prefer_compound_assignment |
| **Идентификатор правила** | IDE0054 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — отдавать предпочтение выражениям [составного присваивания](/dotnet/csharp/language-reference/operators/assignment-operator#compound-assignment)<br /><br />`false` — не отдавать предпочтение выражениям составного присваивания |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// dotnet_style_prefer_compound_assignment = true
x += 1;

// dotnet_style_prefer_compound_assignment = false
x = x + 1;
```

```vb
' dotnet_style_prefer_compound_assignment = true
x += 1

' dotnet_style_prefer_compound_assignment = false
x = x + 1
```

### <a name="null-checking-preferences"></a>Параметры проверки NULL

Правила стилей в этом разделе относятся к параметрам проверки NULL.

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code style settings:
[*.{cs,vb}]
dotnet_style_coalesce_expression = true:suggestion
dotnet_style_null_propagation = true:suggestion
dotnet_style_prefer_is_null_check_over_reference_equality_method = true:silent
```

#### <a name="dotnet_style_coalesce_expression"></a>dotnet\_style\_coalesce_expression

|||
|-|-|
| **Имя правила** | dotnet_style_coalesce_expression |
| **Идентификатор правила** | IDE0029 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `true` — предпочитать выражения объединения со значением NULL вместо проверки тернарными операторами.<br /><br />`false` — предпочитать проверку тернарными операторами вместо выражений объединения со значением NULL. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// dotnet_style_coalesce_expression = true
var v = x ?? y;

// dotnet_style_coalesce_expression = false
var v = x != null ? x : y; // or
var v = x == null ? y : x;
```

```vb
' dotnet_style_coalesce_expression = true
Dim v = If(x, y)

' dotnet_style_coalesce_expression = false
Dim v = If(x Is Nothing, y, x) ' or
Dim v = If(x IsNot Nothing, x, y)
```

#### <a name="dotnet_style_null_propagation"></a>dotnet\_style\_null_propagation

|||
|-|-|
| **Имя правила** | dotnet_style_null_propagation |
| **Идентификатор правила** | IDE0031 |
| **Применимые языки** | C# 6.0+ и Visual Basic 14+ |
| **Значения** | `true` — предпочитать оператор с условием NULL, когда это возможно.<br /><br />`false` — предпочитать тернарную проверку NULL, когда это возможно. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// dotnet_style_null_propagation = true
var v = o?.ToString();

// dotnet_style_null_propagation = false
var v = o == null ? null : o.ToString(); // or
var v = o != null ? o.String() : null;
```

```vb
' dotnet_style_null_propagation = true
Dim v = o?.ToString()

' dotnet_style_null_propagation = false
Dim v = If(o Is Nothing, Nothing, o.ToString()) ' or
Dim v = If(o IsNot Nothing, o.ToString(), Nothing)
```

### <a name="dotnet_style_prefer_is_null_check_over_reference_equality_method"></a>dotnet\_style\_prefer\_is\_null\_check\_over\_reference\_equality\_method

|||
|-|-|
| **Имя правила** | dotnet_style_prefer_is_null_check_over_reference_equality_method |
| **Идентификатор правила** | IDE0041 |
| **Применимые языки** | C# 6.0+ и Visual Basic 14+ |
| **Значения** | `true` — предпочитать проверку значений NULL вместо метода равенства ссылок<br /><br />`false` — предпочитать метод равенства ссылок вместо проверки значений NULL |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

## <a name="net-code-quality-settings"></a>Параметры качества кода .NET

Правила качества в этом разделе относятся к коду C# и Visual Basic. Они используются для настройки анализаторов кода, встроенных в интегрированную среду разработки (IDE) Visual Studio. Сведения о настройке анализаторов FxCop с помощью файла EditorConfig см. в разделе [Настройка анализаторов FxCop](../code-quality/configure-fxcop-analyzers.md).

- [Предпочтения для параметров](#parameter-preferences)
  - dotnet\_code\_quality\_unused\_parameters

### <a name="parameter-preferences"></a>Предпочтения для параметров

Правила качества в этом разделе касаются параметров методов.

В файле *EDITORCONFIG* эти правила могут иметь следующий вид:

```ini
# CSharp and Visual Basic code quality settings:
[*.{cs,vb}]
dotnet_code_quality_unused_parameters = all:suggestion
```

#### <a name="dotnet_code_quality_unused_parameters"></a>dotnet\_code\_quality\_unused\_parameters

|||
|-|-|
| **Имя правила** | dotnet_code_quality_unused_parameters |
| **Идентификатор правила** | IDE0060 |
| **Применимые языки** | C# и Visual Basic |
| **Значения** | `all` — отметить методы с любым уровнем доступности, содержащие неиспользуемые параметры<br /><br />`non_public` — отметить только закрытые методы, которые содержат неиспользуемые параметры |
| **Значение по умолчанию в Visual Studio** | `all:suggestion` |

Примеры кода:

```csharp
// dotnet_code_quality_unused_parameters = all:suggestion
public int GetNum() { return 1; }

// dotnet_code_quality_unused_parameters = non_public:suggestion
public int GetNum(int arg1) { return 1; }
```

```vb
' dotnet_code_quality_unused_parameters = all:suggestion
Public Function GetNum()
    Return 1
End Function

' dotnet_code_quality_unused_parameters = non_public:suggestion
Public Function GetNum(arg1 As Integer)
    Return 1
End Function
```

## <a name="c-code-style-settings"></a>Параметры стиля кода C#

Правила стилей в этом разделе относятся только к C#.

- [Неявные и явные типы](#implicit-and-explicit-types)
  - csharp\_style\_var\_for\_built\_in_types
  - csharp\_style\_var\_when\_type\_is_apparent
  - csharp\_style\_var_elsewhere
- [Элементы, воплощающие выражение](#expression-bodied-members)
  - csharp\_style\_expression\_bodied_methods
  - csharp\_style\_expression\_bodied_constructors
  - csharp\_style\_expression\_bodied_operators
  - csharp\_style\_expression\_bodied_properties
  - csharp\_style\_expression\_bodied_indexers
  - csharp\_style\_expression\_bodied_accessors
  - csharp\_style\_expression\_bodied_lambdas
  - csharp\_style\_expression\_bodied\_local_functions
- [Сопоставление шаблонов](#pattern-matching)
  - csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check
  - csharp\_style\_pattern\_matching\_over\_as\_with\_null_check
- [Встроенные объявления переменных](#inlined-variable-declarations)
  - csharp\_style\_inlined\_variable_declaration
- [Настройки уровня выражений](#c-expression-level-preferences)
  - csharp\_prefer\_simple\_default_expression
- [Настройки проверки Null](#c-null-checking-preferences)
  - csharp\_style\_throw_expression
  - csharp\_style\_conditional\_delegate_call
- [Предпочтения для модификаторов](#normalize-modifiers)
  - csharp\_preferred\_modifier_order
- [Настройки блока кода](#code-block-preferences)
  - csharp\_prefer_braces
- [Предпочтения неиспользуемых значений](#unused-value-preferences)
  - csharp\_style\_unused\_value\_expression\_statement_preference
  - csharp\_style\_unused\_value\_assignment_preference
- [Параметры индекса и диапазона](#index-and-range-preferences)
  - csharp\_style\_prefer\_index_operator
  - csharp\_style\_prefer\_range_operator
- [Прочие параметры](#miscellaneous-preferences)
  - csharp\_style\_deconstructed\_variable_declaration
  - csharp\_style\_pattern\_local\_over\_anonymous_function
  - csharp\_using\_directive\_placement
  - csharp\_prefer\_static\_local_function
  - csharp\_prefer\_simple\_using_statement
  - csharp\_style\_prefer\_switch_expression

### <a name="implicit-and-explicit-types"></a>Неявные и явные типы

Правила стилей в этом разделе относятся к использованию ключевого слова [var](/dotnet/csharp/language-reference/keywords/var) или явного типа в объявлении переменной. Это правило можно отдельно применять для встроенных типов, если этот тип является очевидным, а также в других местах.

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_var_for_built_in_types = true:suggestion
csharp_style_var_when_type_is_apparent = true:suggestion
csharp_style_var_elsewhere = true:suggestion
```

#### <a name="csharp_style_var_for_built_in_types"></a>csharp\_style\_var\_for\_built\_in_types

|||
|-|-|
| **Имя правила** | csharp_style_var_for_built_in_types |
| **Идентификатор правила** | IDE0007 и IDE0008 |
| **Применимые языки** | C#  |
| **Значения** | `true` — предпочитать `var` для объявления переменных со встроенными системными типами, такими как `int`.<br /><br />`false` — предпочитать явное указание типа вместо `var` для объявления переменных со встроенными системными типами, такими как `int`. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// csharp_style_var_for_built_in_types = true
var x = 5;

// csharp_style_var_for_built_in_types = false
int x = 5;
```

#### <a name="csharp_style_var_when_type_is_apparent"></a>csharp\_style\_var\_when\_type\_is_apparent

|||
|-|-|
| **Имя правила** | csharp_style_var_when_type_is_apparent |
| **Идентификатор правила** | IDE0007 и IDE0008 |
| **Применимые языки** | C#  |
| **Значения** | `true` — предпочитать `var`, если тип уже упоминается в правой части выражения с объявлением.<br /><br />`false` — предпочитать явное указание типа вместо `var`, если тип уже упоминается в правой части выражения с объявлением. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// csharp_style_var_when_type_is_apparent = true
var obj = new Customer();

// csharp_style_var_when_type_is_apparent = false
Customer obj = new Customer();
```

#### <a name="csharp_style_var_elsewhere"></a>csharp\_style\_var_elsewhere

|||
|-|-|
| **Имя правила** | csharp_style_var_elsewhere |
| **Идентификатор правила** | IDE0007 и IDE0008 |
| **Применимые языки** | C#  |
| **Значения** | `true` — предпочитать `var` вместо явного типа во всех случаях, если это не переопределено другим правилом стиля кода.<br /><br />`false` — предпочитать явный тип вместо `var` во всех случаях, если это не переопределено другим правилом стиля кода. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// csharp_style_var_elsewhere = true
var f = this.Init();

// csharp_style_var_elsewhere = false
bool f = this.Init();
```

### <a name="expression-bodied-members"></a>Элементы, воплощающие выражение

Правила стилей в этом разделе относятся к использованию [элементов, воплощающих выражение](/dotnet/csharp/programming-guide/statements-expressions-operators/expression-bodied-members), когда логика состоит из одного выражения. Это правило может применяться к методам, конструкторам, операторам, свойствам, индексаторам и методам доступа.

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_expression_bodied_methods = false:silent
csharp_style_expression_bodied_constructors = false:silent
csharp_style_expression_bodied_operators = false:silent
csharp_style_expression_bodied_properties = true:suggestion
csharp_style_expression_bodied_indexers = true:suggestion
csharp_style_expression_bodied_accessors = true:suggestion
csharp_style_expression_bodied_lambdas = true:silent
csharp_style_expression_bodied_local_functions = false:silent
```

#### <a name="csharp_style_expression_bodied_methods"></a>csharp\_style\_expression\_bodied_methods

|||
|-|-|
| **Имя правила** | csharp_style_expression_bodied_methods |
| **Идентификатор правила** | IDE0022 |
| **Применимые языки** | C# 6.0+  |
| **Значения** | `true` — предпочитать для методов тексты выражений<br /><br />`when_on_single_line` — предпочитать для методов тексты выражений, если они будут выражены одной строкой<br /><br />`false` — предпочитать для методов блочные элементы. |
| **Значение по умолчанию в Visual Studio** | `false:silent` |

Примеры кода:

```csharp
// csharp_style_expression_bodied_methods = true
public int GetAge() => this.Age;

// csharp_style_expression_bodied_methods = false
public int GetAge() { return this.Age; }
```

#### <a name="csharp_style_expression_bodied_constructors"></a>csharp\_style\_expression\_bodied_constructors

|||
|-|-|
| **Имя правила** | csharp_style_expression_bodied_constructors |
| **Идентификатор правила** | IDE0021 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать для конструкторов тексты выражений<br /><br />`when_on_single_line` — предпочитать для конструкторов тексты выражений, если они будут выражены одной строкой<br /><br />`false` — предпочитать для конструкторов блочные элементы. |
| **Значение по умолчанию в Visual Studio** | `false:silent` |

Примеры кода:

```csharp
// csharp_style_expression_bodied_constructors = true
public Customer(int age) => Age = age;

// csharp_style_expression_bodied_constructors = false
public Customer(int age) { Age = age; }
```

#### <a name="csharp_style_expression_bodied_operators"></a>csharp\_style\_expression\_bodied_operators

|||
|-|-|
| **Имя правила** | csharp_style_expression_bodied_operators |
| **Идентификатор правила** | IDE0023 и IDE0024 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать для операторов тексты выражений<br /><br />`when_on_single_line` — предпочитать для операторов тексты выражений, если они будут выражены одной строкой<br /><br />`false` — предпочитать для операторов блочные элементы. |
| **Значение по умолчанию в Visual Studio** | `false:silent` |

Примеры кода:

```csharp
// csharp_style_expression_bodied_operators = true
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
    => new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary);

// csharp_style_expression_bodied_operators = false
public static ComplexNumber operator + (ComplexNumber c1, ComplexNumber c2)
{ return new ComplexNumber(c1.Real + c2.Real, c1.Imaginary + c2.Imaginary); }
```

#### <a name="csharp_style_expression_bodied_properties"></a>csharp\_style\_expression\_bodied_properties

|||
|-|-|
| **Имя правила** | csharp_style_expression_bodied_properties |
| **Идентификатор правила** | IDE0025 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать для свойств тексты выражений<br /><br />`when_on_single_line` — предпочитать для свойств тексты выражений, если они будут выражены одной строкой<br /><br />`false` — предпочитать для свойств блочные элементы. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// csharp_style_expression_bodied_properties = true
public int Age => _age;

// csharp_style_expression_bodied_properties = false
public int Age { get { return _age; }}
```

#### <a name="csharp_style_expression_bodied_indexers"></a>csharp\_style\_expression\_bodied_indexers

|||
|-|-|
| **Имя правила** | csharp_style_expression_bodied_indexers |
| **Идентификатор правила** | IDE0026 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать для индексаторов тексты выражений<br /><br />`when_on_single_line` — предпочитать для индексаторов тексты выражений, если они будут выражены одной строкой<br /><br />`false` — предпочитать для индексаторов блочные элементы. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// csharp_style_expression_bodied_indexers = true
public T this[int i] => _values[i];

// csharp_style_expression_bodied_indexers = false
public T this[int i] { get { return _values[i]; } }
```

#### <a name="csharp_style_expression_bodied_accessors"></a>csharp\_style\_expression\_bodied_accessors

|||
|-|-|
| **Имя правила** | csharp_style_expression_bodied_accessors |
| **Идентификатор правила** | IDE0027 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать для методов доступа тексты выражений<br /><br />`when_on_single_line` — предпочитать для методов доступа тексты выражений, если они будут выражены одной строкой<br /><br />`false` — предпочитать для методов доступа блочные элементы. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// csharp_style_expression_bodied_accessors = true
public int Age { get => _age; set => _age = value; }

// csharp_style_expression_bodied_accessors = false
public int Age { get { return _age; } set { _age = value; } }
```

#### <a name="csharp_style_expression_bodied_lambdas"></a>csharp\_style\_expression\_bodied_lambdas

|||
|-|-|
| **Имя правила** | csharp_style_expression_bodied_lambdas |
| **Идентификатор правила** | IDE0053 |
| **Значения** | `true` — предпочитать для лямбда-выражений тексты выражений<br /><br />`when_on_single_line` — предпочитать для лямбда-выражений тексты выражений, если они будут выражены одной строкой<br /><br />`false` — предпочитать для лямбда-выражений тексты элементов уровня блока |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// csharp_style_expression_bodied_lambdas = true
Func<int, int> square = x => x * x;

// csharp_style_expression_bodied_lambdas = false
Func<int, int> square = x => { return x * x; };
```

#### <a name="csharp_style_expression_bodied_local_functions"></a>csharp\_style\_expression\_bodied\_local_functions

Начиная с версии 7.0 в языке C# поддерживаются [локальные функции](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Локальные функции представляют собой частные методы типа, вложенные в другой элемент.

|||
|-|-|
| **Имя правила** | csharp_style_expression_bodied_local_functions |
| **Идентификатор правила** | IDE0061 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать для локальных функций тексты выражений<br /><br />`when_on_single_line` — предпочитать для локальных функций тексты выражений, если они будут выражены одной строкой<br /><br />`false` — предпочитать для локальных функций тексты элементов уровня блока |
| **Значение по умолчанию в Visual Studio** | `false:silent` |

Примеры кода:

```csharp
// csharp_style_expression_bodied_local_functions = true
void M()
{
    Hello();
    void Hello() => Console.WriteLine("Hello");
}

// csharp_style_expression_bodied_local_functions = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

### <a name="pattern-matching"></a>Регулярные выражения

Правила стилей в этом разделе относятся к использованию [сопоставления шаблонов](/dotnet/csharp/pattern-matching) в C#.

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_pattern_matching_over_is_with_cast_check = true:suggestion
csharp_style_pattern_matching_over_as_with_null_check = true:suggestion
```

#### <a name="csharp_style_pattern_matching_over_is_with_cast_check"></a>csharp\_style\_pattern\_matching\_over\_is\_with\_cast_check

|||
|-|-|
| **Имя правила** | csharp_style_pattern_matching_over_is_with_cast_check |
| **Идентификатор правила** | IDE0020 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать сопоставление шаблонов вместо выражений `is` с приведениями типов.<br /><br />`false` — предпочитать выражения `is` с приведениями типов вместо сопоставления шаблонов. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_pattern_matching_over_is_with_cast_check = true
if (o is int i) {...}

// csharp_style_pattern_matching_over_is_with_cast_check = false
if (o is int) {var i = (int)o; ... }
```

#### <a name="csharp_style_pattern_matching_over_as_with_null_check"></a>csharp\_style\_pattern\_matching\_over\_as\_with\_null_check

|||
|-|-|
| **Имя правила** | csharp_style_pattern_matching_over_as_with_null_check |
| **Идентификатор правила** | IDE0019 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать сопоставление шаблонов вместо выражений `as` с проверками NULL, чтобы проверить определенный тип для элемента.<br /><br />`false` — предпочитать выражения `as` с проверками NULL вместо сопоставления шаблонов, чтобы проверить определенный тип для элемента. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_pattern_matching_over_as_with_null_check = true
if (o is string s) {...}

// csharp_style_pattern_matching_over_as_with_null_check = false
var s = o as string;
if (s != null) {...}
```

### <a name="inlined-variable-declarations"></a>Встроенные объявления переменных

Это правило стиля определяет, объявляются ли переменные `out` встроенным образом или нет. Начиная с версии 7 языка C# [переменную out можно объявлять в списке аргументов вызова метода](/dotnet/csharp/language-reference/keywords/out-parameter-modifier#calling-a-method-with-an-out-argument), а не отдельно.

#### <a name="csharp_style_inlined_variable_declaration"></a>csharp\_style\_inlined\_variable_declaration

|||
|-|-|
| **Имя правила** | csharp_style_inlined_variable_declaration |
| **Идентификатор правила** | IDE0018 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать объявление переменных `out` прямо в коде, описывающем список аргументов для вызова метода, когда это возможно.<br /><br />`false` — предпочитать объявление переменных `out` до вызова метода. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_inlined_variable_declaration = true
if (int.TryParse(value, out int i) {...}

// csharp_style_inlined_variable_declaration = false
int i;
if (int.TryParse(value, out i) {...}
```

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_inlined_variable_declaration = true:suggestion
```

### <a name="c-expression-level-preferences"></a>Предпочтения уровня выражений C#

Правила стилей в этом разделе относятся к предпочтениям уровня выражений.

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_simple_default_expression = true:suggestion
```

#### <a name="csharp_prefer_simple_default_expression"></a>csharp\_prefer\_simple\_default_expression

Это правило стиля определяет использование [литерала `default` для выражений значения по умолчанию](/dotnet/csharp/language-reference/operators/default#default-literal), если компилятор может вывести тип выражения.

|||
|-|-|
| **Имя правила** | csharp_prefer_simple_default_expression |
| **Идентификатор правила** | IDE0034 |
| **Применимые языки** | C# 7.1+  |
| **Значения** | `true` — предпочитать `default` вместо `default(T)`.<br /><br />`false` — предпочитать `default(T)` вместо `default`. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_prefer_simple_default_expression = true
void DoWork(CancellationToken cancellationToken = default) { ... }

// csharp_prefer_simple_default_expression = false
void DoWork(CancellationToken cancellationToken = default(CancellationToken)) { ... }
```

### <a name="c-null-checking-preferences"></a>Параметры проверки NULL в C#

Эти правила стиля определяют синтаксис, связанный с проверкой `null`, включая использование выражений `throw` или операторов `throw`, а также выбор между проверкой Null и использованием условного оператора объединения (`?.`) при вызове [лямбда-выражения](/dotnet/csharp/lambda-expressions).

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_throw_expression = true:suggestion
csharp_style_conditional_delegate_call = false:suggestion
```

#### <a name="csharp_style_throw_expression"></a>csharp\_style\_throw_expression

|||
|-|-|
| **Имя правила** | csharp_style_throw_expression |
| **Идентификатор правила** | IDE0016 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать использование выражений `throw` вместо операторов `throw`.<br /><br />`false` — предпочитать использование операторов `throw` вместо выражений `throw`. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_throw_expression = true
this.s = s ?? throw new ArgumentNullException(nameof(s));

// csharp_style_throw_expression = false
if (s == null) { throw new ArgumentNullException(nameof(s)); }
this.s = s;
```

#### <a name="csharp_style_conditional_delegate_call"></a>csharp\_style\_conditional\_delegate_call

|||
|-|-|
| **Имя правила** | csharp_style_conditional_delegate_call |
| **Идентификатор правила** | IDE0041 |
| **Применимые языки** | C# 6.0+  |
| **Значения** | `true` — предпочитать условный оператор объединения (`?.`) при вызове лямбда-выражения вместо выполнения проверки NULL.<br /><br />`false` — предпочитать выполнение проверки NULL перед вызовом лямбда-выражения вместо использования условного оператора объединения (`?.`). |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_conditional_delegate_call = true
func?.Invoke(args);

// csharp_style_conditional_delegate_call = false
if (func != null) { func(args); }
```

### <a name="code-block-preferences"></a>Предпочтения блока кода

Это правило стиля определяет использование фигурных скобок `{ }` вокруг блоков кода.

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_prefer_braces = true:silent
```

#### <a name="csharp_prefer_braces"></a>csharp\_prefer\_braces

|||
|-|-|
| **Имя правила** | csharp_prefer_braces |
| **Идентификатор правила** | IDE0011 |
| **Применимые языки** | C# |
| **Значения** | `true` — предпочитать фигурные скобки даже для одной строки кода.<br /><br />`false` — предпочитать не использовать фигурные скобки, если это допустимо.<br /><br />`when_multiline` — предпочитать фигурные скобки на нескольких строках. |
| **Значение по умолчанию в Visual Studio** | `true:silent` |

Примеры кода:

```csharp
// csharp_prefer_braces = true
if (test) { this.Display(); }

// csharp_prefer_braces = false
if (test) this.Display();
```

### <a name="unused-value-preferences"></a>Предпочтения неиспользуемых значений

Эти правила стилей касаются неиспользуемых выражений и присваивания значений.

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_unused_value_expression_statement_preference = discard_variable:silent
csharp_style_unused_value_assignment_preference = discard_variable:suggestion
```

#### <a name="csharp_style_unused_value_expression_statement_preference"></a>csharp_style_unused_value_expression_statement_preference

|||
|-|-|
| **Имя правила** | csharp_style_unused_value_expression_statement_preference |
| **Идентификатор правила** | IDE0058 |
| **Применимые языки** | C# |
| **Значения** | `discard_variable` — предпочитать назначение неиспользуемого выражения для [отмены](/dotnet/csharp/discards) <br /><br />`unused_local_variable` — предпочитать назначение неиспользуемого выражения для локальной переменной |
| **Значение по умолчанию в Visual Studio** | `discard_variable:silent` |

Примеры кода:

```csharp
// Original code:
System.Convert.ToInt32("35");

// After code fix for IDE0058:

// csharp_style_unused_value_expression_statement_preference = discard_variable
_ = System.Convert.ToInt32("35");

// csharp_style_unused_value_expression_statement_preference = unused_local_variable
var unused = Convert.ToInt32("35");
```

#### <a name="csharp_style_unused_value_assignment_preference"></a>csharp_style_unused_value_assignment_preference

|||
|-|-|
| **Имя правила** | csharp_style_unused_value_assignment_preference |
| **Идентификатор правила** | IDE0059 |
| **Применимые языки** | C# |
| **Значения** | `discard_variable` — предпочитать использование [отмены](/dotnet/csharp/discards) при присваивании значения, которое не используется<br /><br />`unused_local_variable` — предпочитать использование локальной переменной при присваивании значения, которое не используется |
| **Значение по умолчанию в Visual Studio** | `discard_variable:suggestion` |

Примеры кода:

```csharp
// csharp_style_unused_value_assignment_preference = discard_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    _ = wordCount.TryGetValue(searchWord, out var count);
    return count;
}

// csharp_style_unused_value_assignment_preference = unused_local_variable
int GetCount(Dictionary<string, int> wordCount, string searchWord)
{
    var unused = wordCount.TryGetValue(searchWord, out var count);
    return count;
}
```

### <a name="index-and-range-preferences"></a>Параметры индекса и диапазона

Эти правила стилей связаны с использованием операторов индексов и диапазонов, которые доступны в C# 8.0 и более поздних версиях.

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_prefer_index_operator = true:suggestion
csharp_style_prefer_range_operator = true:suggestion
```

#### <a name="csharp_style_prefer_index_operator"></a>csharp\_style\_prefer\_index_operator

|||
|-|-|
| **Имя правила** | csharp_style_prefer_index_operator |
| **Идентификатор правила** | IDE0056 |
| **Применимые языки** | C# 8.0+ |
| **Значения** | `true` — предпочитать использовать оператор `^` при вычислении индекса с конца коллекции<br /><br />`false` — не предпочитать использовать оператор `^` при вычислении индекса с конца коллекции |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_prefer_index_operator = true
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[^1];

// csharp_style_prefer_index_operator = false
string[] names = { "Archimedes", "Pythagoras", "Euclid" };
var index = names[names.Length - 1];
```

#### <a name="csharp_style_prefer_range_operator"></a>csharp\_style\_prefer\_range_operator

|||
|-|-|
| **Имя правила** | csharp_style_prefer_range_operator |
| **Идентификатор правила** | IDE0057 |
| **Применимые языки** | C# 8.0+ |
| **Значения** | `true` — предпочитать использовать оператор диапазона `..` при извлечении "среза" коллекции<br /><br />`false` — не предпочитать использовать оператор диапазона `..` при извлечении "среза" коллекции |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_prefer_range_operator = true
string sentence = "the quick brown fox";
var sub = sentence[0..^4];

// csharp_style_prefer_range_operator = false
string sentence = "the quick brown fox";
var sub = sentence.Substring(0, sentence.Length - 4);
```

### <a name="miscellaneous-preferences"></a>Прочие параметры

В этом разделе содержатся прочие правила для стилей.

Пример файла *EDITORCONFIG*:

```ini
# CSharp code style settings:
[*.cs]
csharp_style_deconstructed_variable_declaration = true:suggestion
csharp_style_pattern_local_over_anonymous_function = true:suggestion
csharp_using_directive_placement = outside_namespace:silent
csharp_prefer_static_local_function = true:suggestion
csharp_prefer_simple_using_statement = true:suggestion
csharp_style_prefer_switch_expression = true:suggestion
```

#### <a name="csharp_style_deconstructed_variable_declaration"></a>csharp\_style\_deconstructed\_variable_declaration

|||
|-|-|
| **Имя правила** | csharp_style_deconstructed_variable_declaration |
| **Идентификатор правила** | IDE0042 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать деконструированное объявление переменных.<br /><br />`false` — не предпочитать деконструированное объявление переменных. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_deconstructed_variable_declaration = true
var (name, age) = GetPersonTuple();
Console.WriteLine($"{name} {age}");

(int x, int y) = GetPointTuple();
Console.WriteLine($"{x} {y}");

// csharp_style_deconstructed_variable_declaration = false
var person = GetPersonTuple();
Console.WriteLine($"{person.name} {person.age}");

(int x, int y) point = GetPointTuple();
Console.WriteLine($"{point.x} {point.y}");
```

#### <a name="csharp_style_pattern_local_over_anonymous_function"></a>csharp\_style\_pattern\_local\_over\_anonymous_function

Начиная с версии 7.0 в языке C# поддерживаются [локальные функции](/dotnet/csharp/programming-guide/classes-and-structs/local-functions). Локальные функции представляют собой частные методы типа, вложенные в другой элемент.

|||
|-|-|
| **Имя правила** | csharp_style_pattern_local_over_anonymous_function |
| **Идентификатор правила** | IDE0039 |
| **Применимые языки** | C# 7.0+ |
| **Значения** | `true` — предпочитать локальные функции анонимным.<br /><br />`false` — предпочитать анонимные функции локальным. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_style_pattern_local_over_anonymous_function = true
int fibonacci(int n)
{
    return n <= 1 ? 1 : fibonacci(n-1) + fibonacci(n-2);
}

// csharp_style_pattern_local_over_anonymous_function = false
Func<int, int> fibonacci = null;
fibonacci = (int n) =>
{
    return n <= 1 ? 1 : fibonacci(n - 1) + fibonacci(n - 2);
};
```

#### <a name="csharp_using_directive_placement"></a>csharp\_using\_directive_placement

|||
|-|-|
| **Имя правила** | csharp_using_directive_placement |
| **Идентификатор правила** | IDE0065 |
| **Применимые языки** | C# |
| **Значения** | `outside_namespace` — предпочитать директивы `using` для размещения вне пространства имен<br /><br />`inside_namespace` — предпочитать директивы `using` для размещения в пространстве имен |
| **Значение по умолчанию в Visual Studio** | `outside_namespace:silent` |

Примеры кода:

```csharp
// csharp_using_directive_placement = outside_namespace
using System;

namespace Conventions
{
    ...
}

// csharp_using_directive_placement = inside_namespace
namespace Conventions
{
    using System;
    ...
}
```

#### <a name="csharp_prefer_static_local_function"></a>csharp\_prefer\_static\_local_function

|||
|-|-|
| **Имя правила** | csharp_prefer_static_local_function |
| **Идентификатор правила** | IDE0062 |
| **Применимые языки** | C# 8.0+ |
| **Значения** | `true` — предпочитать отмечать локальные функции как `static`<br /><br />`false` — не предпочитать отмечать локальные функции как `static` |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_prefer_static_local_function = true
void M()
{
    Hello();
    static void Hello()
    {
        Console.WriteLine("Hello");
    }
}

// csharp_prefer_static_local_function = false
void M()
{
    Hello();
    void Hello()
    {
        Console.WriteLine("Hello");
    }
}
```

#### <a name="csharp_prefer_simple_using_statement"></a>csharp\_prefer\_simple\_using_statement

|||
|-|-|
| **Имя правила** | csharp_prefer_simple_using_statement |
| **Идентификатор правила** | IDE0063 |
| **Применимые языки** | C# 8.0+ |
| **Значения** | `true` — предпочитать использовать *простую* инструкцию `using`.<br /><br />`false` — не предпочитать использовать *простую* инструкцию `using`. |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |

Примеры кода:

```csharp
// csharp_prefer_simple_using_statement = true
using var a = b;

// csharp_prefer_simple_using_statement = false
using (var a = b) { }
```

#### <a name="csharp_style_prefer_switch_expression"></a>csharp\_style\_prefer\_switch_expression

|||
|-|-|
| **Имя правила** | csharp_style_prefer_switch_expression |
| **Идентификатор правила** | IDE0066 |
| **Применимые языки** | C# 8.0+ |
| **Значения** | `true` — предпочтительно использовать выражение `switch` (представлено в C# 8.0)<br /><br />`false` — предпочтительно использовать [оператор switch](/dotnet/csharp/language-reference/keywords/switch) |
| **Значение по умолчанию в Visual Studio** | `true:suggestion` |
| **Представленные версии** | Visual Studio 2019 версии 16.2 |

Примеры кода:

```csharp
// csharp_style_prefer_switch_expression = true
return x switch
{
    1 => 1 * 1,
    2 => 2 * 2,
    _ => 0,
};

// csharp_style_prefer_switch_expression = false
switch (x)
{
    case 1:
        return 1 * 1;
    case 2:
        return 2 * 2;
    default:
        return 0;
}
```

## <a name="see-also"></a>См. также

- [Соглашения по форматированию](editorconfig-formatting-conventions.md)
- [Соглашения об именовании](editorconfig-naming-conventions.md)
- [Параметры соглашений о написании кода .NET в EditorConfig](editorconfig-code-style-settings-reference.md)
