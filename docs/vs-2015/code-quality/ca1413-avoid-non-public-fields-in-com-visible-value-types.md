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
ms.openlocfilehash: 1054330b26cf145ebcbc943a56dc699fe793999f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548464"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413. Не используйте неоткрытые поля в типах значений, видимых для COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип значения, специально помеченный как видимый для модели COM, объявляет Неоткрытое поле экземпляра.

## <a name="rule-description"></a>Описание правила
 Не являющиеся общедоступными поля экземпляров типов значений, отображаемых для модели COM, отображаются для COM-клиентов. Проверьте содержимое поля на предмет сведений, которые не должны быть предоставлены или которые будут иметь непреднамеренное Оформление или последствия безопасности.

 По умолчанию все открытые типы значений видимы для модели COM. Однако для сокращения числа ложных срабатываний это правило требует явного определения видимости типа COM. Включающая сборка должна быть помечена <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> значением, `false` а тип должен быть помечен <xref:System.Runtime.InteropServices.ComVisibleAttribute> значением `true` .

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила и сделать поле скрытым, измените тип значения на ссылочный тип или удалите <xref:System.Runtime.InteropServices.ComVisibleAttribute> атрибут из типа.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если доступность поля является общедоступной.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий правило.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1407. Не используйте статические члены в типах, видимых для COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017. Пометьте сборки с помощью ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>См. также:
 [Взаимодействие с неуправляемым кодом,](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [подходящих для взаимодействия типов .NET](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)
