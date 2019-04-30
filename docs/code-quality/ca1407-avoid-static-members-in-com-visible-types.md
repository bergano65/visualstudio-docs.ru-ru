---
title: CA1407. Не используйте статические члены в типах, видимых для COM
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b09122aebdc02b9eacb32df596914a0a08a9ea9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546262"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407. Не используйте статические члены в типах, видимых для COM

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, который специально помечен как видимый для модели объектов компонента (COM) содержит `public``static` метод.

## <a name="rule-description"></a>Описание правила
 COM не поддерживает `static` методы.

 Это правило не учитывает свойство и доступа к событиям, перегрузки методов или методы, помеченные с помощью операторов <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> атрибут или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибута.

 По умолчанию следующие являются видимыми для COM: сборки, открытые типы, члены открытых экземпляров в открытых типов и все члены открытых типов значения.

 Для этого правила возникает, уровня сборки <xref:System.Runtime.InteropServices.ComVisibleAttribute> должно быть присвоено `false` и класс - <xref:System.Runtime.InteropServices.ComVisibleAttribute> должно быть присвоено `true`, как показано в следующем коде.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените структуру использовать метод экземпляра, который предоставляет те же функции, что `static` метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если COM-клиента не требуется доступ к функциональности, предоставляемой `static` метод.

## <a name="example-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показан `static` метод, который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Комментарии
 В этом примере **Book.FromPages** метод не может быть вызван из COM.

## <a name="example-fix"></a>Пример исправления

### <a name="description"></a>Описание
 Чтобы устранить нарушение в предыдущем примере, можно изменить метод на метод экземпляра, но, не имеет смысла в данном экземпляре. Лучшим решением является явное применение `ComVisible(false)` в метод, чтобы сделать его снимите флажок, чтобы другие разработчики, что метод не видны из COM.

 В следующем примере применяется <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> методу.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1017: Пометьте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Не используйте аргументы Int64 для клиентов Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: Избегайте не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)