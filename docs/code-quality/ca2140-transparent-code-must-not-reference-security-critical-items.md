---
title: CA2140. Прозрачный код не должен ссылаться на критические для безопасности элементы
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4462bb8ef65fdf593ab0bf64813c19af5d390d97
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545033"
---
# <a name="ca2140-transparent-code-must-not-reference-security-critical-items"></a>CA2140. Прозрачный код не должен ссылаться на критические для безопасности элементы

|||
|-|-|
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|
|CheckId|CA2140|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина

Прозрачный метод:

- обрабатывает тип безопасности критические исключения

- имеет параметр, который помечен как критический тип безопасности

- универсальный параметр с критические ограничения безопасности

- имеет локальную переменную типа критических безопасности

- ссылается на тип, помеченный как безопасности важных

- вызывает метод, помеченный как безопасности важных

- ссылается на поле, помеченный как безопасности важных

- Возвращает тип, помеченный как безопасности важных

## <a name="rule-description"></a>Описание правила

Элемент кода, который помечен атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибут является критически важным для безопасности. Прозрачный метод не может использовать элемент, критический с точки зрения безопасности. Если прозрачный тип пытается использовать тип безопасности важных <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , или <xref:System.FieldAccessException> возникает.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, выполните одно из следующих действий.

- Пометить элемент кода, использующего защите важного кода с <xref:System.Security.SecurityCriticalAttribute> атрибут

     \- или -

- Удалить <xref:System.Security.SecurityCriticalAttribute> атрибут из элементы кода, которые отмечены как безопасности важных и вместо этого пометьте их с помощью <xref:System.Security.SecuritySafeCriticalAttribute> или <xref:System.Security.SecurityTransparentAttribute> атрибута.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример

В приведенных ниже примерах прозрачный метод предпринимается попытка ссылки на важные универсальная коллекция безопасности, безопасности полю и к критическому методу безопасности.

[!code-csharp[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityCriticalAttribute>
- <xref:System.Security.SecurityTransparentAttribute>
- <xref:System.Security.SecurityTreatAsSafeAttribute>
- <xref:System.Security?displayProperty=fullName>