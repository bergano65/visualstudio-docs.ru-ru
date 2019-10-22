---
title: 'CA1407: не используйте статические члены в видимых типах COM | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6996d210417a56dd83532c481aaa0dc80b9f23ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655238"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: не используйте статические члены в видимых COM типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип, который специально помечен как видимый для модели COM, содержит метод `public``static`.

## <a name="rule-description"></a>Описание правила
 COM не поддерживает методы `static`.

 Это правило игнорирует методы доступа к свойствам, методам перегрузки операторов или методам, помеченным с помощью атрибута <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или атрибута <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

 По умолчанию следующие элементы видимы для COM: сборки, открытые типы, члены открытых экземпляров в открытых типах и все члены открытых типов значений.

 Для этого правила на уровне сборки <xref:System.Runtime.InteropServices.ComVisibleAttribute> должно быть задано значение `false`, а для класса <xref:System.Runtime.InteropServices.ComVisibleAttribute> должно быть задано значение `true`, как показано в следующем коде.

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
 Чтобы устранить нарушение этого правила, измените структуру, чтобы использовать метод экземпляра, который предоставляет те же функциональные возможности, что и метод `static`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Если клиенту COM не требуется доступ к функциональным возможностям, предоставляемым методом `static`, можно отключить вывод предупреждения из этого правила.

## <a name="example-violation"></a>Пример нарушения

### <a name="description"></a>Описание
 В следующем примере показан метод `static`, нарушающий это правило.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Комментарии
 В этом примере метод **Book. фромпажес** не может быть вызван из com.

## <a name="example-fix"></a>Пример исправления

### <a name="description"></a>Описание
 Чтобы устранить нарушение в предыдущем примере, можно было бы изменить метод на метод экземпляра, но это не имеет смысла в этом экземпляре. Лучшим решением является явное применение `ComVisible(false)` к методу, чтобы сделать его более понятным для других разработчиков, которые метод не видит из COM.

 В следующем примере к методу применяется <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>.

### <a name="code"></a>Код
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: не используйте аргументы Int64 для клиентов Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>См. также раздел
 [Взаимодействие с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
