---
title: Отключение предупреждений анализа кода
ms.date: 12/01/2018
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 6cd61304e150da63d2d461ef364e7039789c71fc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825829"
---
# <a name="suppress-code-analysis-warnings"></a>Отключение предупреждений анализа кода

Часто полезно указать, что предупреждение неприменимо. Это указывает на члены команды, что код прошел проверку, и что можно подавить предупреждения. Подавление (ISS) используется в исходном <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибут, чтобы подавить предупреждение. Атрибут можно поместить рядом в фрагменте кода, который создает предупреждение. Вы можете добавить <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибут в исходный файл, введя его, или можно использовать контекстное меню на предупреждение в **список ошибок** добавляется автоматически.

<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> Атрибута является условным атрибутом, который включается в метаданные промежуточного языка сборки управляемого кода, только в том случае, если символ компиляции CODE_ANALYSIS определен во время компиляции.

В C++выполняет, используйте макрос ЦС\_ПОДАВЛЯТЬ\_сообщения или ЦС\_GLOBAL\_SUPPRESS_MESSAGE в файле заголовка для добавления атрибута.

> [!NOTE]
> Не следует использовать подавлений в исходном для сборок выпуска, для предотвращения случайно доставки метаданные подавление в исходном коде. Кроме того из-за стоимости обработки подавление в исходном коде, производительность приложения может снижаться.

> [!NOTE]
> Если миграция проекта в Visual Studio 2017 или Visual Studio 2019 г., вы можете неожиданно столкнуться с большим числом предупреждений анализа кода. Эти предупреждения поступают от [анализаторов Roslyn](roslyn-analyzers-overview.md). Если вы не готовы устранить предупреждения, их все можно отключить, выбрав **анализ** > **выполнить анализ кода и подавить активные проблемы**.
>
> ![Запустить анализ кода и подавить проблемы в Visual Studio](media/suppress-active-issues.png)

## <a name="suppressmessage-attribute"></a>SuppressMessage - атрибут

При выборе **подавлять** в контекстном меню предупреждение анализа кода в **список ошибок**, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> добавляется атрибут, либо в коде, либо для глобального подавления проекта файл.

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

Свойства атрибута включают:

- **Категория** -категорию, в котором определено правило. Дополнительные сведения о категориях правил анализа кода, см. в разделе [управляемый код предупреждения](../code-quality/code-analysis-for-managed-code-warnings.md).

- **CheckId** -идентификатор правила. Поддержка включает в себя как короткое и длинное имя идентификатора правила. Короткое имя является CAXXXX; длинное имя — CAXXXX:FriendlyTypeName.

- **Обоснование** -текст, который используется для документирования причина подавления сообщения.

- **MessageId** — уникальный идентификатор проблемы для каждого сообщения.

- **Область** -целевой объект, на котором подавляется предупреждение. Если целевой объект не указан, ему присваивается целевой объект атрибута. Поддерживается [областей](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) включают следующее:

   - `module`

   - `resource`

   - `type`

   - `member`

   - `namespace` — Это область подавляет предупреждения от само пространство имен. Он не подавляет предупреждения для типов в пространстве имен.

   - `namespaceanddescendants` -(Новое в Visual Studio 2019 г.) эта область подавляет предупреждения в пространстве имен и всех ее потомков символов. `namespaceanddescendants` Значение допустимо только для анализаторов Roslyn и учитывается на статическом анализе двоичных, основанное на FxCop.

- **Целевой объект** — это идентификатор, который используется для указания целевого объекта, на котором подавляется предупреждение. Он должен содержать имя полного имени элемента.

## <a name="suppressmessage-usage"></a>Использование SuppressMessage

Предупреждения анализа кода подавляются на уровне, к которому <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> применяется атрибут. Например атрибут может применяться на сборки, модуля, типа, члена или параметра уровня. Это предназначено для тесно связать сведения о подавлении в код месте нарушения.

Общая форма подавления включает категорию правила и идентификатор правила, который содержит представление необязательное понятное имя правила. Пример:

`[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

При возникновении соображений производительности, сводя к минимуму метаданных подавления в исходном коде, можно опустить имя правила. Категория правил и идентификатор правила вместе составляют достаточно уникальное обозначение правила. Пример:

`[SuppressMessage("Microsoft.Design", "CA1039")]`

В целях удобства обслуживания при пропуске названия правило не рекомендуется.

## <a name="suppress-selective-violations-within-a-method-body"></a>Подавлять выборочной нарушений в теле метода

Подавление атрибуты могут применяться к методу, но не может быть внедрен в теле метода. Это означает, что все нарушения определенного правила, подавляются при добавлении <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> к методу атрибут.

В некоторых случаях может потребоваться подавлять конкретного экземпляра нарушения, например, чтобы будущий код не автоматически исключаются из правил анализа кода. Некоторые правила анализа кода позволяют это сделать с помощью `MessageId` свойство <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибута. В общем случае правила прежних версий для нарушения в отношении конкретного символа (локальная переменная или параметр) `MessageId` свойство. [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md) является примером такого правила. Тем не менее, не влияют на устаревших правил для нарушений для исполняемого кода (не являющегося символом) `MessageId` свойство. Кроме того, не влияют на анализаторов .NET Compiler Platform («Roslyn») `MessageId` свойство.

Можно отключить правила конкретного символа, укажите имя символа для `MessageId` свойство <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибута. В следующем примере кода с помощью двух нарушений [CA1500:VariableNamesShouldNotMatchFieldNames](../code-quality/ca1500-variable-names-should-not-match-field-names.md)&mdash;для `name` переменной и один для `age` переменной. Только нарушение для `age` символ подавляется.

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

Компиляторы управляемого кода и некоторые сторонние средства создания кода для упрощения разработки кода. Как правило, созданный компилятором код, который отображается в исходных файлах помечается с помощью `GeneratedCodeAttribute` атрибута.

Можно выбрать, следует ли подавлять предупреждения анализа кода и ошибки для сформированного кода. Сведения о подавлении таких предупреждений и ошибок, см. в разделе [как: Отключение предупреждений для созданного кода](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

> [!NOTE]
> Анализ кода не учитывает `GeneratedCodeAttribute` при применении для всей сборки или одним параметром.

## <a name="global-level-suppressions"></a>Подавления на уровне Global

Средство анализа управляемого кода проверяет `SuppressMessage` атрибуты, которые применяются на уровне сборки, модуля, типа, члена или параметра. Оно также выявляет нарушения на уровне ресурсов и пространств имен. Эти нарушения должны применяться на глобальном уровне и являются областью действия и целевые. Например следующее сообщение подавляет нарушение пространство имен:

`[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> При отключении предупреждения с `namespace` области, он подавление применяется к самому пространству имен. Он не подавляет предупреждение для типов в пространстве имен.

Любое подавление может быть выражен путем указания явного указания области. Такие подавления должны применяться на глобальном уровне. Нельзя указать подавления на уровне элементов, дополняя тип.

Подавления на уровне Global являются единственным способом для подавления сообщений, которые ссылаются на код, созданный компилятором, который не сопоставляется с явно предоставленным исходным кодом пользователя. Например следующий код отключает нарушение в созданном компилятором конструкторе:

`[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> `Target` всегда содержит полное имя.

## <a name="global-suppression-file"></a>Файл глобального подавления

Файл глобального подавления поддерживает подавления на глобальном уровне или подавления, для которых не указан целевой объект. Например в этом файле хранятся подавления на уровне сборки нарушений. Кроме того подавлений ASP.NET, хранятся в этот файл, так как на уровне проекта параметры недоступны для кода программной части формы. Файл глобального подавления создается и добавляется в проект при первом выборе **в файле проекта для блокируемых предупреждений** параметр **подавлять** в команду **список ошибок**окно.

## <a name="see-also"></a>См. также

- <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope>
- <xref:System.Diagnostics.CodeAnalysis>
- [Использование анализаторов Roslyn](../code-quality/use-roslyn-analyzers.md)