---
title: CA1812. Избегайте неиспользуемых внутренних классов
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0d55af3c5522c6bb9aa3ad8a023f070c187ca6f
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714264"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812. Избегайте неиспользуемых внутренних классов

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Никогда не инициализируется во внутренний тип (на уровне сборки).

## <a name="rule-description"></a>Описание правила

Это правило пытается найти вызова одного из конструкторов типа и приводит к нарушению, если запрос не найден.

Это правило не проверяет следующие типы:

- Типы значений

- Абстрактные типы

- Перечисления

- Делегаты

- Типы массивов, определяемые компилятором

- Типы, не может быть создан, и только определяют [ `static` ](/dotnet/csharp/language-reference/keywords/static) ([ `Shared` в Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)) методы.

Если применить <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> к сборке, который анализируется, это правило не пометит типы, помеченные как [ `internal` ](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` в Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)) потому, что поле может относиться к используемые дружественной сборки.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите тип или добавьте код, который его использует. Если тип содержит только `static` методы, добавьте один из следующих к типу, чтобы запретить компилятору выполнять выпуска конструктор открытого экземпляра по умолчанию:

- `static` Модификатор для C# типы, предназначенные [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] или более поздней версии.

- Закрытый конструктор для типов, предназначенных для .NET Framework версий 1.0 и 1.1.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила. Мы рекомендуем отключить предупреждение в следующих ситуациях:

- Класс создается через методы отражения с поздним связыванием, такие как <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>.

- Класс создается автоматически средой выполнения или ASP.NET. Некоторые примеры автоматически созданных классов: те, которые реализуют <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> или <xref:System.Web.IHttpHandler?displayProperty=fullName>.

- Класс передается в качестве параметра типа, имеющего [ `new` ограничение](/dotnet/csharp/language-reference/keywords/new-constraint). Следующий пример будут помечены правилом CA1812:

    ```csharp
    internal class MyClass
    {
        public DoSomething()
        {
        }
    }
    public class MyGeneric<T> where T : new()
    {
        public T Create()
        {
            return new T();
        }
    }

    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
    mc.Create();
    ```

## <a name="related-rules"></a>Связанные правила

- [CA1811: Не используйте Невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804: Удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)