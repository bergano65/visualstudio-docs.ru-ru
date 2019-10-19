---
title: 'CA1413: Избегайте использования полей, не являющихся открытыми, в видимых типах значений COM | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7d66c2c52b6ee7f7d1d2fbbd461ca8c1251ce13d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652703"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: избегайте использования не открытых полей в видимых типах значений COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип значения, специально помеченный как видимый для модели COM, объявляет Неоткрытое поле экземпляра.

## <a name="rule-description"></a>Описание правила
 Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое поля на предмет сведений, которые не должны быть предоставлены или которые будут иметь непреднамеренное Оформление или последствия безопасности.

 По умолчанию все открытые типы значений видимы для модели COM. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. Включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>, для которой задано значение `false`, а тип должен быть помечен <xref:System.Runtime.InteropServices.ComVisibleAttribute>ным значением `true`.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила и сделать поле скрытым, измените тип значения на ссылочный тип или удалите атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> из типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если доступность поля является общедоступной.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также раздел
 [Взаимодействие с неуправляемым кодом,](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [подходящих для взаимодействия типов .NET](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
