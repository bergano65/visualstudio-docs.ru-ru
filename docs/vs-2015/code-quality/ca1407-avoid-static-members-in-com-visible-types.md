---
title: 'CA1407: Не используйте статические члены в видимых COM типах | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 19e9c1fae6a4f3446b5de63e3dc9b76d3bb92367
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591921"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: не используйте статические члены в видимых COM типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1407: не используйте статические члены в видимых COM типах](https://docs.microsoft.com/visualstudio/code-quality/ca1407-avoid-static-members-in-com-visible-types).

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
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Комментарии
 В этом примере **Book.FromPages** метод не может быть вызван из COM.

## <a name="example-fix"></a>Пример исправления

### <a name="description"></a>Описание
 Чтобы устранить нарушение в предыдущем примере, можно изменить метод на метод экземпляра, но, не имеет смысла в данном экземпляре. Лучшим решением является явное применение `ComVisible(false)` в метод, чтобы сделать его снимите флажок, чтобы другие разработчики, что метод не видны из COM.

 В следующем примере применяется <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> методу.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: не используйте аргументы Int64 для клиентов Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



