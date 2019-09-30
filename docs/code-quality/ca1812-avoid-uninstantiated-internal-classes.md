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
ms.openlocfilehash: f924e9530a7ee43ec2222366141c3af6be2efc29
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233612"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812. Избегайте неиспользуемых внутренних классов

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Экземпляр внутреннего типа (уровня сборки) никогда не создается.

## <a name="rule-description"></a>Описание правила

Это правило пытается найти вызов одного из конструкторов типа и сообщает о нарушении, если вызов не найден.

Это правило не проверяет следующие типы:

- Типы значений

- Абстрактные типы

- Перечисления

- Делегаты

- Типы массивов, созданные компилятором

- Типы, которые не могут быть созданы и которые определяют [`static`](/dotnet/csharp/language-reference/keywords/static) только методы ([ `Shared` в Visual Basic](/dotnet/visual-basic/language-reference/modifiers/shared)).

Если применить <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> к анализируемой сборке, это правило не будет помечать типы, помеченные как [`internal`](/dotnet/csharp/language-reference/keywords/internal) ([ `Friend` в Visual Basic](/dotnet/visual-basic/language-reference/modifiers/friend)), так как поле может использоваться дружественной сборкой.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, удалите тип или добавьте код, который его использует. Если тип содержит только `static` методы, добавьте в тип один из следующих элементов, чтобы компилятор не выдать конструктор открытого экземпляра по умолчанию:

- Модификатор для типов, C# предназначенных для .NET Framework 2,0 или более поздней версии. `static`

- Закрытый конструктор для типов, предназначенных для .NET Framework версий 1,0 и 1,1.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

В этом правиле можно отключить вывод предупреждений. Рекомендуется подавлять это предупреждение в следующих ситуациях:

- Класс создается с помощью методов отражения с поздним связыванием, <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>таких как.

- Класс создается автоматически средой выполнения или ASP.NET. Примерами автоматически создаваемых классов являются классы, <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> реализующие <xref:System.Web.IHttpHandler?displayProperty=fullName>или.

- Класс передается как параметр типа с [ `new` ограничением](/dotnet/csharp/language-reference/keywords/new-constraint). Следующий пример будет помечен правилом CA1812:

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

- [CA1811 Избегайте невызванного закрытого кода](../code-quality/ca1811-avoid-uncalled-private-code.md)
- [CA1801: Проверка неиспользуемых параметров](../code-quality/ca1801-review-unused-parameters.md)
- [CA1804 Удалить неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)