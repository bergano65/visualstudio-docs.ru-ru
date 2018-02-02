---
title: "Подавление предупреждений анализа кода при помощи атрибута SuppressMessage в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 01/29/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 4cd3800e082673e9478eb32c6ae5627eef4d7e81
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2018
---
# <a name="suppressing-code-analysis-warnings"></a>Подавление предупреждений анализа кода

Часто полезно указать, что предупреждение неприменимо. Это значит, что члены команды код прошел проверку и предупреждения можно подавить. Подавление (ISS) используется в исходном <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибут для подавления предупреждений. Атрибут можно разместить рядом сегмент кода, который создает предупреждение. Можно добавить <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибутов в исходный файл, введя его в, или можно использовать контекстное меню на предупреждение в **список ошибок** автоматически добавляться.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Атрибут является условным атрибутом, который включается в метаданные промежуточного языка сборки управляемого кода только в том случае, если символ компиляции CODE_ANALYSIS определен во время компиляции.

В C + +/ CLI, используйте макрос ЦС\_ПОДАВЛЯТЬ\_сообщения или ЦС\_GLOBAL\_SUPPRESS_MESSAGE в файле заголовка для добавления атрибута.

> [!NOTE]
> Не следует использовать в исходном подавлений на построения выпуска для предотвращения случайного доставки метаданных подавление в исходном коде. Кроме того из-за обработки стоимость подавление в исходном коде, производительность приложения может ухудшиться.

## <a name="suppressmessage-attribute"></a>SuppressMessage - атрибут

При выборе **подавлять** меню контекст или щелкните правой кнопкой мыши предупреждение анализа кода в **список ошибок**, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибут добавляется в коде или для глобального подавления проекта файл.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Атрибут имеет следующий формат:

```vb
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>
```

```csharp
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]
```

```cpp
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")
```

Следующие свойства атрибута.

- **Правило категории** -категорию, в котором определено правило. Дополнительные сведения о категориях правил анализа кода см. в разделе [управляемого кода предупреждения](../code-quality/code-analysis-for-managed-code-warnings.md).

- **ИД правила** -идентификатор правила. Поддерживается как короткое и длинное имя идентификатора правила. Краткое имя — CAXXXX; длинное имя — CAXXXX:FriendlyTypeName.

- **При выравнивании по ширине** -текст, который используется для документирования причины для подавления сообщения.

- **Идентификатор сообщения** — уникальный идентификатор проблемы для каждого сообщения.

- **Область** -подавить предупреждение целевой объект. Если целевой объект не указан, ему присваивается целевому объекту атрибута. Ниже приведены поддерживаемые областей:

    - Module

    - Пространство имен

    - Ресурс

    - Тип

    - Член

- **Целевой** — это идентификатор, который используется для указания цели, подавляются предупреждения. Он должен содержать элемент полное доменное имя.

## <a name="suppressmessage-usage"></a>Использование SuppressMessage

Предупреждения анализа кода подавляются на уровне, к которому <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> применяется атрибут. Например атрибут может применяться на сборки, модуля, типа, члена или параметра уровня. Это предназначено для тесно связать сведения о подавлении в код месте нарушения.

Общая форма подавления включает категорию правила и идентификатор правила, которая содержит представление необязательное понятное имя правила. Пример:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

При отсутствии соображений производительности минимизация метаданных подавления в исходном коде, можно опустить имя правила. Категория правила и идентификатор правила вместе составляют достаточно уникальное обозначение правила. Пример:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

В целях удобства пропуск имени правила не рекомендуется.

## <a name="suppressing-selective-violations-within-a-method-body"></a>Подавление Выборочный нарушений в теле метода

Подавление атрибуты могут применяться к методу, но не может быть внедрен в теле метода. Это означает, что все нарушения определенное правило, подавляются при добавлении <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> к методу атрибут.

В некоторых случаях может потребоваться отключение конкретный экземпляр нарушения, например, чтобы будущий код не автоматически будут исключены из правил анализа кода. Некоторые правила анализа кода позволяют сделать это с помощью `MessageId` свойство <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибута. В общем случае правила прежних версий при нарушении в отношении конкретного символа (локальная переменная или параметр) `MessageId` свойство. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) является примером такого правила. Тем не менее, не влияют на устаревшие правила нарушений на исполняемый код (не являющегося символом) `MessageId` свойство. Кроме того, не влияют на анализаторы Roslyn `MessageId` свойство.

Можно отключить правила конкретного символа, укажите имя символа для `MessageId` свойство <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибута. В следующем примере показано кода с помощью двух нарушения [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;для `name` переменной и один для `age` переменной. Это нарушение для `age` символ подавляется.

```vb
Public Class Animal
    Dim age As Integer
    Dim name As String

    <CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId:="age")>
    Sub PrintInfo()
        Dim age As Integer = 5
        Dim name As String = "Charlie"

        Console.WriteLine("Age {0}, Name {1}", age, name)
    End Sub

End Class
```

```csharp
public class Animal
{
    int age;
    string name;

    [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Maintainability", "CA1500:VariableNamesShouldNotMatchFieldNames", MessageId = "age")]
    private void PrintInfo()
    {
        int age = 5;
        string name = "Charlie";

        Console.WriteLine($"Age {age}, Name {name}");
    }
}
```

## <a name="generated-code"></a>Созданный код

Компиляторы управляемого кода и некоторые сторонние средства создания кода для упрощения разработки кода. Как правило, созданный компилятором код, который отображается в исходных файлах помечается с `GeneratedCodeAttribute` атрибута.

Вы можете подавления предупреждений анализа кода и ошибки для созданного кода. Сведения о подавлении таких предупреждений и ошибок см. в разделе [как: отключить предупреждения для кода, созданного](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Средство анализа кода пропускает `GeneratedCodeAttribute` при применении для всей сборки или одним параметром.

## <a name="global-level-suppressions"></a>Подавления на глобальном уровне

Средство анализа управляемого кода проверяет `SuppressMessage` атрибуты, которые применяются на уровне сборки, модуля, типа, члена или параметра. Он также выявляет нарушения на ресурсы и пространства имен. Эти нарушения должны применяться на глобальном уровне и связанных и целевые. Например следующее сообщение подавляет нарушение пространство имен:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> При подавлении предупреждение в области видимости пространства имен подавление применяется к самому пространству имен. Он не подавляет предупреждение с типами в пространстве имен.

Любое подавление можно выразить путем указания явного указания области. Такие подавления должны применяться на глобальном уровне. Подавления на уровне члена нельзя указать путем оформления типа.

Подавления на глобальном уровне являются единственным способом для подавления сообщений, которые ссылаются на созданный компилятором код, который не сопоставлен с явно предоставленным исходным кодом пользователя. Например следующий код подавляет нарушение в созданном компилятором конструкторе:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target`всегда содержит имя элемента полным.

## <a name="global-suppression-file"></a>Файл глобального подавления

Файл глобального подавления содержит подавления на глобальном уровне или подавления которых не указан целевой объект. Например в этом файле хранятся подавления на уровне сборки нарушений. Кроме того подавлений ASP.NET, хранятся в этот файл, так как параметры на уровне проекта недоступны для кода программной части формы. Файл глобального подавления создается и добавляется к проекту при первом выборе **в файле проекта для блокируемых** параметр **подавлять** в **список ошибок**окна.

## <a name="see-also"></a>См. также

<xref:System.Diagnostics.CodeAnalysis>