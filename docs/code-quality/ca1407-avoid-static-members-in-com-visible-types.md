---
title: 'CA1407: не используйте статические члены в видимых COM типах'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f14e3b2577d182db432402a267e8bd6979736186
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: не используйте статические члены в видимых COM типах
|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, который специально помечен как видимый для модели объектов компонентов (COM) содержит `public``static` метод.

## <a name="rule-description"></a>Описание правила
 COM не поддерживает `static` методы.

 Это правило не учитывает свойства и методы доступа к событию, перегрузки методов или методы, помеченные с помощью операторов <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> атрибута или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> атрибута.

 По умолчанию, являются видимыми для COM следующие: сборки, открытые типы, члены общих экземпляров в открытых типах и все элементы общих типов значений.

 Для этого правила возникает уровня сборки <xref:System.Runtime.InteropServices.ComVisibleAttribute> должно быть присвоено `false` и класс - <xref:System.Runtime.InteropServices.ComVisibleAttribute> должно быть присвоено `true`, как показано в следующем коде.

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
 Чтобы устранить нарушение данного правила, измените используйте метод экземпляра, который предоставляет те же функциональные возможности, как при разработке `static` метод.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно безопасно подавить предупреждение из этого правила, если COM-клиента не требуется доступ к функциям, которые предоставляются `static` метод.

## <a name="example-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показан `static` метод, который нарушает это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Комментарии
 В этом примере **Book.FromPages** метод не может быть вызван из COM.

## <a name="example-fix"></a>Пример исправления

### <a name="description"></a>Описание
 Чтобы устранить нарушение в предыдущем примере, можно изменить метод на метод экземпляра, однако, не имеет смысла в данном экземпляре. Лучшим решением является явное применение `ComVisible(false)` в метод, чтобы сделать его снимите флажок, чтобы другие разработчики, что метод не виден из COM.

 В следующем примере применяется <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> методу.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Связанные правила
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: не используйте аргументы Int64 для клиентов Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)