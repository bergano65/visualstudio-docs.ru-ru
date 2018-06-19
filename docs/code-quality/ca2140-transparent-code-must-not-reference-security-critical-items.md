---
title: 'CA2140: прозрачный код не должен ссылаться на элементы, критичные в плане безопасности'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2129
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2140
helpviewer_keywords:
- CA2140
- SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode
- CA2129
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c02de86564f6d7754b3c9db86d93577c374a72e0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918440"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140: прозрачный код не должен ссылаться на элементы, критичные в плане безопасности
|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Прозрачный метод:

-   обрабатывает тип критические исключения безопасности

-   имеет параметр, который помечен как критический для безопасности тип

-   универсальный параметр с критические ограничения безопасности

-   имеет локальную переменную критического для безопасности типа

-   ссылается на тип, помеченный как безопасности критические

-   вызывает метод, помеченный как безопасности критические

-   ссылка на поле, помеченный как безопасности критические

-   Возвращает тип, помеченный как безопасности критические

## <a name="rule-description"></a>Описание правила
 Элемент кода, который отмечен атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибут является критически важным для безопасности. Прозрачный метод не может использовать элемент, критический с точки зрения безопасности. Если прозрачный тип пытается использовать тип, критический безопасности <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , или <xref:System.FieldAccessException> возникает.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, выполните одно из следующих действий.

-   Пометить элемент кода, использующего критический код безопасности с <xref:System.Security.SecurityCriticalAttribute> атрибута

     \- или -

-   Удалить <xref:System.Security.SecurityCriticalAttribute> атрибут из элементов кода, которые отмечены как безопасности критических и отметьте их атрибутом вместо <xref:System.Security.SecuritySafeCriticalAttribute> или <xref:System.Security.SecurityTransparentAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующих примерах прозрачный метод пытается выполнить ссылку критических универсальной коллекции безопасности, критические для безопасности поле и критический метод безопасности.

 [!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>См. также
 <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecurityTransparentAttribute> <xref:System.Security.SecurityTreatAsSafeAttribute> <xref:System.Security?displayProperty=fullName>